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
