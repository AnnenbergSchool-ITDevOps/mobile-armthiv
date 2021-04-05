**Twitter Retweet**
----
  Retweet Twitter message with user email and message id. 
 

* **URL**

  /twitter/retweet

* **Method:**

  `POST`

*  **Params**

   **Required:**

   `email=[string]`
   `id=[string]`

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** `{"success":true,"posted":{"retweet":"success"}}`<br />
     OR <br />
    **Content:** `{"success":false,"posted":{"retweet":"Sorry, that page does not exist"}}`

* **Sample Call:**

  ```javascript
    $.ajax({
      url: "/twitter/userinfo",
      dataType: "json",
      type : "POST",
      success : function(r) {
        console.log(r);
      }
    });
  ```
  
  
* **example**

  **https://hsmg.psych.illinois.edu/armt-hiv/v1/twitter/retweet/?email=xxx@gmail.com&id=1270095772227379209**
