**User Sign Up**
----
  Initiate user setup in database and send out an email for verification.

* **URL**

  /signup

* **Method:**

  `POST`

*  **Params**

   **Required:**

   `email=[string]`
   `password=[string]`


* **Success Response:**

  * **Code:** 200 <br />
    **Content:** `{ "success" : true, "posted":"Mail has been sent successfully!" }`<br />
     OR <br />
    **Content:** `{ "success" : fail, "posted":"Email cannot be blank" }`

* **Sample Call:**

  ```javascript
    $.ajax({
      url: "/signup",
      dataType: "json",
      type : "POST",
      success : function(r) {
        console.log(r);
      }
    });
  ```
*  **Test URL**<br>

[http://sal.asc.upenn.edu/armt-hiv/v1/user_signup.php](http://sal.asc.upenn.edu/armt-hiv/v1/user_signup.php)

___________

### CURL POST REQUEST

Helpful demonstration for curl POST request formatting [here](https://gist.github.com/subfuzion/08c5d85437d5d4f00e58)

- For example, using `WWW Encoded`:

```bash
# Internal UPenn email
curl -d "email=etiennej@upenn.edu&password=P@$$w0rd" -H "Content-Type: application/x-www-form-urlencoded" -X POST https://sal.asc.upenn.edu/armt-hiv/v1/signup/

# External Personal Gmail
curl -d "email=jacquot.etienne@gmail.com&password=P@$$w0rd" -H "Content-Type: application/x-www-form-urlencoded" -X POST https://sal.asc.upenn.edu/armt-hiv/v1/signup/
```

- Check MongoDB if the account was added to the database:

```mongo
use armt-hiv

db.users.find({'email':'etiennej@upenn.edu'}) 

db.users.find({'email':'jacquot.etienne@gmail.com'}) 
```

- You will see *NOT* verified... that is because you need to check the verification email! This probably routes into the app so not yet sure about verification...
> - https://sal.asc.upenn.edu/armt-hiv/v1/verify/?email=etiennej@upenn.edu&code=ENceOcHE

- *also my external gmail did NOT get an email ... maybe SMTP is not beyond PennO365?*