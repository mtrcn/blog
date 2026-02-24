---
title: "Export Bunq account statements for UK visa application via Bunq's APIs"
date: 2019-12-01
tags: 
  - "bunq"
  - "python"
  - "uk"
  - "visaapplication"
---

Six months ago, I applied to UK visa together with a solicitor. My solicitor asked me to provide daily bank statements for the last three months to prove that my account balance never down below asked level by Home Office. At that time, I was using Bunq and had a chat with Bunq support, and I was told that it is not possible via application unless I export statements day by day. That means I had to do some actions for 90 times. Thank god, I'm a developer and Bunq provides API that can automate it.

<!--more-->

First, I created an API key via Bunq's mobile application. Then, I started to read API documentation to find out which endpoints are available to export statements.

I found that there is an endpoint with `/user/{userID}/monetary-account/{monetary-accountID}/customer-statement`, it generates statements and returns statement's `Id`, so that I can download the statement with this ID. It also requires `userID` and `monetary-accountID` as route parameters.

Bunq provides [Python SDK](https://github.com/bunq/sdk_python); this makes my job easier for authentication and API calls.

I started to code, first of all, I need to create an API context with following;

```
from bunq.sdk import context, client

apiContext =  context.ApiContext(context.ApiEnvironmentType.PRODUCTION, '[API KEY]',  "ExportStatementClient")
apiContext.save('D:/BunqApiContext')
```

Then, I need to obtain my `userID`, and I can get it with the following code;

```
rom bunq.sdk import context, client

apiContext =  context.ApiContext(context.ApiEnvironmentType.PRODUCTION, '[API KEY]',  "ExportStatementClient")
apiContext.restore('D:/BunqApiContext')
bunq_client = client.ApiClient(apiContext)

response = bunq_client.get('user', [], [])
print (response.body_bytes)
```

I noted my userID in response to use it later.

Now I can get my `monetary-accountID` with following;

```
bunq_client = client.ApiClient(apiContext)
response = bunq_client.get('user/{userId}/monetary-account-bank', [], [])
print (response.body_bytes)
```

It returns all your accounts, so note your `monetary-accountID` in response to export its statements.

Now, as we have all the required parameters, we can export statements as PDF files for the last 90 days in one go without using dealing with multiple UI actions for each of them.

```
import requests
from datetime import date, timedelta
import time
import uuid
from bunq.sdk import context, client
import json

def dict_to_bytes(the_dict):
    return bytes(json.dumps(the_dict).encode('utf-8'))

if __name__ == "__main__":
    apiContext =  context.ApiContext(context.ApiEnvironmentType.PRODUCTION, '[API KEY]',  "ExportStatementClient")
    apiContext.restore('D:/BunqApiContext')
    bunq_client = client.ApiClient(apiContext)

    userId = XXXXX
    accountId = XXXX
    output_folder = 'D:/BunqStatements'

    today = date.today()
    first_date = today + timedelta(days=-90)
    current_date = first_date
    i = 0
    statements = []
    while i < 90:
        params = {
            "statement_format": "PDF",
            "date_start": current_date.strftime("%d-%m-%Y"),
            "date_end": (current_date+ timedelta(days=1)).strftime("%d-%m-%Y")
        }
        response = bunq_client.post('user/'+str(userId)+'/monetary-account/'+str(accountId)+'/customer-statement', dict_to_bytes(params), [])
        statement_id = json.loads(response.body_bytes)['Response'][0]['Id']['id']
        statements.append(statement_id)
        response = bunq_client.get('user/'+str(userId)+'/monetary-account/'+str(accountId)+'/customer-statement/'+str(statement_id)+'/content', [], [])
        f = open(output_folder + '\statement-'+current_date.strftime("%Y-%m-%d")+'.pdf', 'wb+')
        f.write(response.body_bytes)
        f.close()
        bunq_client.delete('user/'+str(userId)+'/monetary-account/'+str(accountId)+'/customer-statement/'+str(statement_id), [])
        i = i + 1
        current_date = first_date + timedelta(days=i)
        print (current_date.strftime("%d-%m-%Y")+' saved.')
```

That's all!

I attached them to my visa application as supporting documents, and eventually, my visa application was approved.
