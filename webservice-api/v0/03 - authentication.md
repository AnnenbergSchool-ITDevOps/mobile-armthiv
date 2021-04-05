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
[link](http://hsmg.psych.illinois.edu/armt-hiv/v0/user_login.php)
