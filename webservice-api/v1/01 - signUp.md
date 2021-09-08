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


- result, check MongoDB to confirm user is added... and check email to confirm you received an email!
