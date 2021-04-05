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
[link](http://hsmg.psych.illinois.edu/armt-hiv/v0/reset_password.php)
