**User Authentication**
----
  Check user password and return user information

* **URL**

  /auth

* **Method:**

  `POST`

*  **Params**

   **Required:**

   `email=[string]`
   `password=[string]`


* **Success Response:**

  * **Code:** 200 <br />
    **Content:** `{"success":true,"posted":{"_id":{"$oid":"5dd1d302099ac658e7455042"},"email":"chris@gmail.com","verified":true,"county":"Champaign","firstname":"Chris","gender":"M","lastname":"West","state":"IL"}}`<br />
     OR <br />
    **Content:** `{"success":false,"posted":"User not found"}`

* **Sample Call:**

  ```javascript
    $.ajax({
      url: "/auth",
      dataType: "json",
      type : "POST",
      success : function(r) {
        console.log(r);
      }
    });
  ```
*  **Test URL**<br>
[http://sal.asc.upenn.edu/armt-hiv/v1/user_login.php](http://sal.asc.upenn.edu/armt-hiv/v1/user_login.php)


___________

### CURL POST REQUEST


```bash
curl -d "email=etiennej@upenn.edu&password=P@1407w0rd" -H "Content-Type: application/x-www-form-urlencoded" -X POST https://sal.asc.upenn.edu/armt-hiv/v1/auth/
```

- returns the following (notice this is now verified!)

`{"success":true,"posted":{"_id":{"$oid":"6138d4014fda713a7140bcf2"},"email":"etiennej@upenn.edu","verified":"true","county":null,"firstname":"Etienne","gender":"Male","lastname":"Jacquot","notification":null,"state":"PA"}}`

__________

Further testing ... 

verification test for `jacquot.etienne@gmail.com` which current shows as unverified but fails?



```bash
# External Personal Gmail SIGNUP
curl -d "email=jacquot.etienne@gmail.com&password=P@$$w0rd" -H "Content-Type: application/x-www-form-urlencoded" -X POST https://sal.asc.upenn.edu/armt-hiv/v1/signup/
```

- I guess you should not use $ in password? `P@$$w0rd` turns into `P@177w0rd` in the database

```bash
# Attempt to Auth
curl -d "email=jacquot.etienne@gmail.com&password=P@177w0rd" -H "Content-Type: application/x-www-form-urlencoded" -X POST https://sal.asc.upenn.edu/armt-hiv/v1/auth/
```
but returns `{"success":false,"posted":"user not verified"}` so maybe it's the userInfo that verifies... SMTP to my gmail isn't going through, so I don't get the code but I can get from backend and add here (for example, `w5pSjVVa`):

```bash
# Update User Info
curl -d "email=jacquot.etienne@gmail.com&password=P@177w0rd&firstname=Etienne&lastname=Jacquot&gender=Male&state=PA&country=USA&code=w5pSjVVa" -H "Content-Type: application/x-www-form-urlencoded" -X POST https://sal.asc.upenn.edu/armt-hiv/v1/userinfo/
```

- this does in fact verify! **the 02 - userInfo is what verifies after you get SMTP email w/ code**... so again now we try to auth given the verification is true:


```bash
# Attempt to Auth
curl -d "email=jacquot.etienne@gmail.com&password=P@177w0rd" -H "Content-Type: application/x-www-form-urlencoded" -X POST https://sal.asc.upenn.edu/armt-hiv/v1/auth/
```

- And this works! For example: 
`/
{"success":true,"posted":{"_id":{"$oid":"613a69634b00d9230b621a92"},"email":"jacquot.etienne@gmail.com","verified":"true","county":null,"firstname":"Etienne","gender":"Male","lastname":"Jacquot","notification":null,"state":"PA"}}`