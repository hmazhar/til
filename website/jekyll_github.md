# Simplest way to automatically regenerate jekyll website on push

Install hookshot: https://github.com/coreh/hookshot

```npm install -g hookshot```

run 
```hookshot -p 8080 -r refs/heads/develop 'echo pushed to develop'```

```hookshot -p 8080 -r refs/heads/develop './custom_script.sh'```

forever start -a hookshot -p 8080 -r refs/heads/develop './custom_script.sh'

```
#!/bin/bash
pushd /home/sbel-bot/Repositories/chrono
git pull
jekyll build -s website -d /home/websites/sites/projectchrono.org
```