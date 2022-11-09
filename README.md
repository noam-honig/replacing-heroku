# replacing-heroku
A list of Heroku replacements, now that Heroku announced that they no longer provide a free tier

# Node server + Postgres Database
1. railway.app 👍 - easiest to install, great dev experience - only hosted on westcoast so slow to Israel (200ms latency) :(
   1. https://blog.railway.app/p/automated-postgresql-backups
   2. Deploy via github repo
3. fly.io 👍 - installs via cli, docs is pretty technical and scary - but it works - followed this article:
   * https://fly.io/docs/languages-and-frameworks/node/
   * 120ms latency
   * deploy via cdn
4. render - [Only one free db and will be deleted after 90 days](https://render.com/docs/free#free-postgresql-databases)
   1. https://www.freecodecamp.org/news/how-to-deploy-nodejs-application-with-render/
   2. have project on github
   3. create project type "Web Service" and connect to github
   4. create new postgres database (as opposed to heroku - the database is separate from the website)
   5. You'll need to add "npm i" to your package.json file, because 'render' doesn't automatically run npm i when you deploy.
   6. I needed to specify the node version to use, because render was using an old version of node (<15). To specify the node version, set an environment variable called "NODE_VERSION" and set it to the version you want:(16.13.1) in my case
   7. 105 latency
   8. As opposed to heroku, railway & fly.io - you'll need to manually set the DATABASE_URL environment variable for your postgres database.
   9. Positive:
      1. better management consule
      2. sends an email when the web site crashes - really wanted that in heroku
      3. 

**explore database backup**
**explore database remote connection**

# node js:
1. AWS Elastic beanstalk - [aws setup notes created with Asaf](deploy-to-aws.md)
2. Google cloud run 



# Fullstack
1. https://www.deta.sh/
2. https://domcloud.co/docs/deploying/node
2. https://adaptable.io/pricing
2. https://www.koyeb.com/pricing
2. https://qoddi.com/postgresql/
3. DigitalOcean App Platform



# Server less
2. Vercel.
1. https://www.cyclic.sh/ -⭐ - has good free tier - supports dynamo db - looks nice
2. Netlify, very short serverless functions
3. Cloudflare - seems partial support for serverless functions
4. Firebase - https://towardsdev.com/host-a-nodejs-app-with-firebase-87c771489bea
5. https://www.honeybadger.io/blog/node-elastic-beanstalk/?fbclid=IwAR2xibyOEO_AtqdG482kE0B2h09eXJNRpsEV2xYM8wr6lCePJtixqrEZqUk


## Postgres:
1. ElephantSQL
2. supabase.com - see explanation at: https://deno.com/deploy/docs/tutorial-postgres#setup-postgres

## Other:
https://caprover.com/ - creates a docker and deploys it to gidital ocean or anything else

## Things to check on any platform
1. How to see cosole log
2. How to deploy on commit
3. SSL
4. postgres
5. Server side http events
6. 

