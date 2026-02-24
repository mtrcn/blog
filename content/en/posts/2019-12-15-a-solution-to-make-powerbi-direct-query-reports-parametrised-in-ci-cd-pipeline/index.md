---
title: "A solution to make PowerBI Direct Query Reports parametrised in CI/CD pipeline"
date: 2019-12-15
tags: 
  - "cicd"
  - "mssql"
  - "powerbi"
  - "sql"
---

PowerBI REST APIs are very limited with restrictions for specific usages. One of the restriction is that you cannot update parameters on your PowerBI dataset via APIs if you're using Direct Query. It is a problem if you want to have a master template PowerBI report and create reports based on the master for each different project with different parameters.

<!--more-->

Assume that your report uses DirectQuery and API document says you cannot use [Update Parameters](https://docs.microsoft.com/en-us/rest/api/power-bi/datasets/updateparameters) endpoint. In this article, I presume that the report uses Direct Query with MS SQL Server. The only thing I can change via APIs is the connection parameters via [Update Datasource](https://docs.microsoft.com/en-us/rest/api/power-bi/gateways/updatedatasource) endpoint. Luckily, SQL Server 2016 introduced with [Row-Level Security](https://docs.microsoft.com/en-us/sql/relational-databases/security/row-level-security) that allows us to limit user's access to data at row level. We can create a master table to hold master data for each project, and the rest of the tables can make **inner join** with this table for Power BI reports. During the CI/CD process, we can call Update Datasource endpoint for the newly created dataset and update its user credential to limit its data for a specific project. It can be used as a solution until Microsft removes restrictions on Update Parameter's endpoint for Direct Query based reports. This solution makes a bit complicated, but it works. Hope you find it useful. Leave your comments if you have better a solution, love to hear it.
