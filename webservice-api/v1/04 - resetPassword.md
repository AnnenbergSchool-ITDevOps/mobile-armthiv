**Reset User Password**
----
  Reset User Password and send the password to user's email

* **URL**

  /resetpassword

* **Method:**

  `POST`

*  **Params**

   **Required:**

   `email=[string]`   

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** `{"success":true,"posted":"Mail has been sent successfully!"}`<br />
     OR <br />
    **Content:** `{"success":false,"posted":"User not found"}`

* **Sample Call:**

  ```javascript
    $.ajax({
      url: "/resetpassword",
      dataType: "json",
      type : "POST",
      success : function(r) {
        console.log(r);
      }
    });
  ```
*  **Test URL**<br>
[http://sal.asc.upenn.edu/armt-hiv/v1/reset_password.php](http://sal.asc.upenn.edu/armt-hiv/v1/reset_password.php)



___________

### CURL POST REQUEST


```bash
# Initiate Password Reset
curl -d "email=jacquot.etienne@gmail.com" -H "Content-Type: application/x-www-form-urlencoded" -X POST https://sal.asc.upenn.edu/armt-hiv/v1/resetpassword/
```

- works, returns `{"success":true,"posted":"Mail has been sent successfully!"}` though my gmail is not getting the SMTP... trying again for internal


```bash
# Initiate Password Reset
curl -d "email=etiennej@upenn.edu" -H "Content-Type: application/x-www-form-urlencoded" -X POST https://sal.asc.upenn.edu/armt-hiv/v1/resetpassword/
```

- this basically scrambles the password! I checked on the DB and it's now `"email" : "etiennej@upenn.edu", "password" : "BfUqJvuw",` though I'm not seeing the SMPT email for etiennej@upenn.edu ....

okay I think there is a mistake in that the v1 verfy index.php still points to v0 verifyCode (https://bitbucket.org/annenbergschoolupenn/armt-hiv/src/2c6419b38d2ce9fd9f37c649cd780d22e4a748d7/v1/verify/index.php#lines-73) 

- After changing to v1 and then manually updating the SMTP configs to remove username & pw it worked! I received the following note (but does not open on mobile app):

`https://sal.asc.upenn.edu/armt-hiv/v1/password/?email=etiennej@upenn.edu&opw=I7ezBNqG&pw=`

in the 05 - updatePassword you can reset via curl post