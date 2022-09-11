# replacing-heroku
A list of Heroku replacements, now that Heroku announced that they no longer provide a free tier

# Node server + Postgres Database
1. railway.app 👍 - easiest to install, great dev experience - only hosted on westcoast so slow to Israel (200ms latency) :(
2. fly.io 👍 - installs via cli, docs is pretty technical and scary - but it works - followed this article:
   * https://fly.io/docs/languages-and-frameworks/node/
   * 120ms latency
3. render - [Only one free db and will be deleted after 90 days](https://render.com/docs/free#free-postgresql-databases)
   1. https://www.freecodecamp.org/news/how-to-deploy-nodejs-application-with-render/
   2. have project on github
   3. create project type "Web Service" and connect to github
   4. create new postgres database (as opposed to heroku - the database is separate from the website)
   5. currently failed to deploy - doesn't show why :( 😒



# node js:
2. Vercel.
3. netlify
4. https://www.honeybadger.io/blog/node-elastic-beanstalk/?fbclid=IwAR2xibyOEO_AtqdG482kE0B2h09eXJNRpsEV2xYM8wr6lCePJtixqrEZqUk

# Fullstack
1. https://www.deta.sh/
2. fly.io
2. https://domcloud.co/docs/deploying/node
2. https://adaptable.io/pricing
2. https://www.koyeb.com/pricing
2. https://qoddi.com/postgresql/
3. DigitalOcean App Platform


# Server less
1. https://www.cyclic.sh/ -⭐ - has good free tier - supports dynamo db - looks nice
2. Netlify, very short serverless functions
3. Cloudflare - seems partial support for serverless functions
4. Firebase - https://towardsdev.com/host-a-nodejs-app-with-firebase-87c771489bea


## Postgres:
1. ElephantSQL
2. supabase.com

## Other:
https://caprover.com/ - creates a docker and deploys it to gidital ocean or anything else
