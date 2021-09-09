**Twitter Authorization**
----
  To get twitter authorization for armt-hiv App.
  Open the URL in a web broswer/view. Enter the twitter credentials to get authorization tokens. 
  The tokens will be stored in collection `user->twitter` object. 

* **URL**

  /twitter/auth

*  **Params**

   **Required:**

   `email=[string]`

*  **Example URL**<br>

> using `abc@gmail.com`

[https://sal.asc.upenn.edu/armt-hiv/v1/twitter/auth/?email=abc@mail.com](https://sal.asc.upenn.edu/armt-hiv/v1/twitter/auth/?email=abc@mail.com)


___________

### CURL POST REQUEST

- I think you need a valid Twitter account, I may need to make one for `etiennej@upenn.edu` to test & confirm with my dummy oauth callback app ... TBD

```bash
curl -d "email=etiennej@upenn.edu" -H "Content-Type: application/x-www-form-urlencoded" -X POST https://sal.asc.upenn.edu/armt-hiv/v1/twitter/auth/
```

**OH wait oops I don't think this is a POST ???**

you probably can just try to navigate in browser
> does the email need to match the twitter email account?

[https://sal.asc.upenn.edu/armt-hiv/v1/twitter/auth/?email=etiennej@upenn.edu](https://sal.asc.upenn.edu/armt-hiv/v1/twitter/auth/?email=etiennej@upenn.edu)

- this hangs on *Redirecting you back to the application. This may take a few moments.* ... I tried using my epj@asc.upenn.edu twitter account!
- **YOU SHOULD PROBABLY DO THIS ON MOBILE BROWSER WITH APP, SO THE OAUTH CAN REDIRECT YOU BACK PROPERLY!**
  - I maybe need to recreate my etiennej@upenn.edu user info to fresh, as the twitter oauth tokens DO actually make it into the database (just the redirection is broken, obviously, because we do not own the app). for example:
  - ```bash
      > db.users.find({'email':'etiennej@upenn.edu'})

      { "_id" : ObjectId("613a6d99d4adce74b41f1922"), "email" : "etiennej@upenn.edu", "password" : "abcd1234", "verifyCode" : "UBY8aOU8", "verified" : "true", "county" : null, "firstname" : "Etienne", "gender" : "Male", "lastname" : "Jacquot", "notification" : null, "state" : "PA", "twitter" : "{\"oauth_token\":\"1022129459741245440-...\",\"oauth_token_secret\":\"cPKOIS7sw2...\",\"username\":\"JacquotEtienne\",\"id_str\":\"1022129459741245440\"}" }
    ```
