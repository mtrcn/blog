---

title: "Delete Azure Blob Files Only In a Folder"
slug: "delete-azure-blob-file-only-in-a-folder"
date: 2020-05-13
tags: 
  - "azure"
  - "blob"
  - "cli"
  - "storage"
---

If you are looking for a command to delete Azure blob files in a folder with one command, here is the solution;

<!--more-->

```
az storage blob delete-batch -s mycontainer --pattern '*[/]*'
```
