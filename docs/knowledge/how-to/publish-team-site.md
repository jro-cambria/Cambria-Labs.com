---
title: "How to Publish Team Site"
tags: [how-to, website]
---
# How to Edit & Publish Team Site (This site)
Version: 2024-01-29 / JRO

## Finder
- `Work > Cambria Labs > _PUBLIC > Websites > Cambria-labs.com`

## Open Git App (GitHub Desktop)

## Get latest version of site
- (Git command to pull)

## Edit content
- Drag Website folder into Visual Studio Code
- Open Content To-Write page
- Add / Edit content

## Commit changes
### Visual Studio Code
- Source Control (Option+Shift+G)
- Review changes
- Add comment (commit message)
- Commit changes
- Publish changes to repository
- Review published changes on Repository (GitHub)

## Manual deployment
- Open Website folder in Terminal
- `mkdocs build`
- Open File transfer client (CyberDuck)
- Open connection to Website folder on Server (AWS S3)
- Drag `site` folder into root folder
- In AWS / CloudFront, invalidate cache `/*`
  - TO-DO: Only invalidate content which has changed
  

## Automated deployment
- `mkdocs build`
- (AWS CLI Sync from local folder to remote)
- (AWS CLI update cache)
- (Check site for broken links)

## Related topics
- AWS CLI
- MkDocd