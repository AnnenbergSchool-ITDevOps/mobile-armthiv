**Update user password**
----
  Update user password

* **URL**

  /password

* **Method:**

  `POST`

*  **Params**

   **Required:**

   `email=[string]`
   `opw=[string]`
   `pw=[string]`


* **Success Response:**

  * **Code:** 200 <br />
    **Content:** `{"success":true,"posted":"password updated"}`<br />
     OR <br />
    **Content:** `{"success":false,"posted":"User not found"}`<br />
     OR <br />
    **Content:** `{"success":false,"posted":"password incorrect"}`<br />
    
* **Sample Call:**

  ```javascript
    $.ajax({
      url: "/password",
      dataType: "json",
      type : "POST",
      success : function(r) {
        console.log(r);
      }
    });
  ```

