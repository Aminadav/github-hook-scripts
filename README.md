# Github hook scripts

This script let you run any bash/bat scripts, on push from github

Example file
```
server:
  port: 80 
repos:
 "aminag/curl-current-app":
  master:
   command: |
    git clone https://github.com/{{user}}/{{repo}} {{repo}} --depth=1
    cd curl-current-app
    git pull
    git checkout {{branch}}
    git pull
    export NPM_TOKEN="ae0caf86-bf51-4deb-b08e-ffffff"
    npm version patch
    npm publish
    rd {{repo}} /s /q
```

On every push to github, publish new version to npm