Had a great talk with Asaf, where together we've deployed both static files and a nodejs server to aws.

I'm still a newby in this, so I got as far as working - I'm not sure about best practices :)

# Deploy static files to S3 and open them to the web:
In AWS 
1. Search for `s3` in the search bar on top and select `S3`
2. Click `Create bucket` button
   1. Give unique name (In my test it was `replace-heroku-static`) , and select region. 
   2. Under the topic `Block Public Access settings or this bucket` 
      1. uncheck all checkboxes
      2. check the `I achnowledge that.....`
      This will allow anyone to access the files in this s3 - which is what you want for a your front end files.
   3. Scroll down and click `create bucket`
3. In the list - click on the newly created bucket
   1. goto `Properties` 
      1. Scroll down to `Static website hosting`
         1. Edit
         2. Enable
         3. Specify the `index document` and `error document` - in my case I just put `index.html`
         4. Save
   2. goto `Permissions`
      1. `Bucket policy` - click edit
      2. Set the policy - you can click on policy examples where you can find policies - I've used the second one called:`Granting read-only permission to an anonymous user
`.
         
         Copy the json from there and replace the `DOC-EXAMPLE-BUCKET` with your bucket name (In my test it was `replace-heroku-static`)
         ```json
         {
             "Version": "2012-10-17",
             "Statement": [
                 {
                     "Sid": "PublicRead",
                     "Effect": "Allow",
                     "Principal": "*",
                     "Action": [
                         "s3:GetObject",
                         "s3:GetObjectVersion"
                     ],
                     "Resource": [
                         "arn:aws:s3:::DOC-EXAMPLE-BUCKET/*"
                     ]
                 }
             ]
         }
         ```
         * Make sure to replace `DOC-EXAMPLE-BUCKET` with your bucket name
         * Make sure to delete all trailing spaces, otherwise you'll get an in valid json error (for some reason it started with a space I had to remove)
         * Click save
   3. Goto `Objects` and upload your files (In react or angular this will be all the index.html, and javascript  and css files created when you build your project) In my case it was just a simple index.html (you can simply drag and drop them to the browser) and click `Upload`
   4. In the `Objects` list, click on `index.html` 
   5. Copy the `Object URL` into your browser and you're ready to go.
   
# Deploying node js server
1. Search for `Elastic Beanstalk` in the search bar on top and select `Elastic Beanstalk`
2. Prepare your app for deployment:
   3. Add a file called `procfile` (no extention) in the root folder of your project and write in it `node:` and the node js starting point. in my case it looks like this:
      ```
      node:dist/server/index.js
      ```
   4. Run npm install and also build your code.
   5. If you have environment variables, store them in a .env file - you will not be able to set them on the server yourself like you did in heroku or railway.
   6. create a zip file with all that - you'll use it later.
4. Click `Create a new environment`
   3. Select `Web server environment` and click `Select`
   4. Set application name (in my case `replace-heroku-node`)
   5. Select `Platform` `Node.js`
   6. `Application code` select `Upload your code`
   7. Upload the zip file you've created in item 2.
   8. Click `Create environment`
   9. wait for it to complete :)
   10. Once it's done you'll have a url at the top with a link that should work :)

## Notes
* Viewing console log done by node js
  1. On the left, click `logs` 
     2. Request logs
     3. download the file and in it there will be a section called: `/var/log/web.stdout.log`

## To add to this document
1. Configure SSL
2. Connect to postgres database
3. Things I don't know yet....
