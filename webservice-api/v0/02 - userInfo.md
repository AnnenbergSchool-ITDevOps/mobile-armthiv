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
   `notification=Array([boolean], [boolean], [boolean], [boolean], [boolean], [boolean], [boolean])`

*  **Description** <br />
the notification is a boolean array, start with Sunday.

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
[link](http://hsmg.psych.illinois.edu/armt-hiv/v0/user_complete_info.php)
