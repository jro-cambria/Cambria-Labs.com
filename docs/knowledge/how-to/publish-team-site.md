---
title: "How to Publish Team Site"
tags: [how-to, website]
---
# How to Edit & Publish Team Site (This site)

## Get latest version of site

## Edit content
- Drag Website folder into Visual Studio Code
- Add / Edit content

## Commit changes
### Visual Studio Code
- Source Control (Option+Shift+G)
- Review changes
- Add comment (commit message)
- Commit changes
- Publish changes to repository

## Manual deployment
- Open Website folder in Terminal
- `mkdocs build`
- Open File transfer client (CyberDuck)
- Open connection to Website folder on Server (AWS S3)
- Drag `site` folder into root folder
- In AWS / CloudFront, invalidate cache `/*`
  - TO-DO: Only invalidate content which has changed