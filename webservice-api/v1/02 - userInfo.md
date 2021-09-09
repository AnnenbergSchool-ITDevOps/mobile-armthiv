**Update User Infomation**
----
  Update user infomation

* **URL**

  /userinfo

* **Method:**

  `POST`

*  **Params**

   **Required:**

   `email=[string]`<br />
   `password=[string]`<br />
   `firstname=[string]`<br />
   `lastname=[string]`<br />
   `gender=[string]`<br />
   `state=[string]`<br />
   `county=[string]`<br />
   `code=[string]`<br />
   `notification=Array([boolean], [boolean], [boolean], [boolean], [boolean], [boolean], [boolean])`<br />
   `twitter=[oauth_token:"string", oauth_token_secret:"string"]`<br />
   
*  **Description** <br />
The notification is a boolean array, start with Sunday.
The call is added 'code' for entering verification code. If the user is not verified, include the 'code' in the call and it will complete the update.
If the user is verified, it will check the password before the update.  

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** `{"success":true,"posted":"user updated"}`<br />
     OR <br />
    **Content:** `{"success":false,"posted":"No User found"}`<br />
     OR <br />
    **Content:** `{"success":false,"posted":"password incorrect"}`

* **Sample Call:**

  ```javascript
    $.ajax({
      url: "/userinfo",
      dataType: "json",
      type : "POST",
      success : function(r) {
        console.log(r);
      }
    });
  ```

*  **Test URL**<br>
[http://sal.asc.upenn.edu/armt-hiv/v1/user_complete_info.php](http://sal.asc.upenn.edu/armt-hiv/v1/user_complete_info.php)


___________

### CURL POST REQUEST

> Not sure about this one? 

```bash
curl -d "email=epj@asc.upenn.edu&password=P@$$w0rd&firstname=Etienne&lastname=Jacquot&gender=Male&state=PA&country=USA&code=Co1gtBsi&notification=Array([True], [True], [True], [True], [True], [True], [True])&twitter=[oauth_token:1022129459741245440-jYNRUhV819RjJ2WxKiGxqvaH0s4L6N, oauth_token_secret:cPKOIS7sw2xjGdnlpUYt2dZhzvI2RG2fdbY3nb1MZMBVK]" -H "Content-Type: application/x-www-form-urlencoded" -X POST https://sal.asc.upenn.edu/armt-hiv/v1/userinfo/
```

As a response I get `{"success":true,"posted":"user updated"}`!

what about the new user without twitter oauth? 

```bash
curl -d "email=etiennej@upenn.edu&password=P@1407w0rd&firstname=Etienne&lastname=Jacquot&gender=Male&state=PA&country=USA&code=ENceOcHE" -H "Content-Type: application/x-www-form-urlencoded" -X POST https://sal.asc.upenn.edu/armt-hiv/v1/userinfo/
```

Yes this does work, I get `{"success":true,"posted":"user updated"}` returned and in the db:

```mongo
> db.users.find({'email':'etiennej@upenn.edu'})

{ "_id" : ObjectId("6138d4014fda713a7140bcf2"), "email" : "etiennej@upenn.edu", "password" : "P@1407w0rd", "verifyCode" : "ENceOcHE", "verified" : "true", "county" : null, "firstname" : "Etienne", "gender" : "Male", "lastname" : "Jacquot", "notification" 
: null, "state" : "PA" }
```