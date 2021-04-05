**Get Recommended Message**
----
  Get recommended message by date

* **URL**

  /recMsg

* **Method:**

  `POST`

*  **Params**

   **Optional:**

   `date=[string]` in YYYYMMDD<br />
   
*  **Description** <br />
Default is return today's recommended message. If 'date' is inputed, it will return the recommended message on 'date'  <br />
Since the database's messages generation is not finish yet, only the date between 20200601 to 20200610 have message. <br />
for example,<br />
http://hsmg.psych.illinois.edu/armt-hiv/v1/recMsg/?date=20200604

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
