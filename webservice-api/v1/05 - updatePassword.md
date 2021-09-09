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

*  **Test URL**<br>

[http://sal.asc.upenn.edu/armt-hiv/v1/password](http://sal.asc.upenn.edu/armt-hiv/v1/password)


___________

### CURL POST REQUEST

- this assumes you reset using 04 - resetPassword to automatically force a pw reset via SMTP email

```bash
# testing for pw reset after receiving email
curl -d "email=etiennej@upenn.edu&opw=I7ezBNqG&pw=abcd1234" -H "Content-Type: application/x-www-form-urlencoded" -X POST https://sal.asc.upenn.edu/armt-hiv/v1/password/
```

- great this works, pw is reset via that curl!

> TAKEAWAY IS THAT YOU REALLY NEED TO PROPERLY SET THE SMTP SETTINGS IN RESPECTIVE INDEX.PHP... the grep & sed commands I did were not enough given I was not able to comment out in php with `//`