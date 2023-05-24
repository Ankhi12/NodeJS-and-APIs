# API Documentation
This test API documentation is to show how Axios http methods interact with the backend.
# Fetching data from the backend
1. Http get method is used to fetch data from the backend.
Example - Fetching students data from the backend with URL - https://localhost:3000/students (this is not a working URL, so kindly don't click it. This URL link is only for illustration purpose.)

The above URL will fetch all the stucent details from the backend to the frontend axios.get request.
Syntax for axios get method (frontend) - 
  axios.get(url)
        .then()
        .catch()
   - axios returns a promise object. Therefore, we need to handle the promise either using **then & catch** method or using **async/await** 

Fetching data while sending parameters or extra information with the get request-
A URL Paramteres can be anything that comes after the "?" mark.

Example - https://localhost:3000/student?name=test

Syntax for axios get method with parameter (frontend) - 
axios.get(url, {
  parameterName: parameterValue
})
     .then()
     .catch()
     
   # Sending data to the backend
2. Http post method is used to send data to the backend.
   The sent data is in JavaScript format.
   axios.post(url, {
          keyName: ValueName,
          KeyName1: ValueName2
   })
         .then()
         .catch()
  
  # Editing backend data
  3. Http put method is for sending a update request to the backend.
      axios.put(url, {
      keyName: ValueName}
      )
      The KeyName and ValueName are the values you want to change in the backend.
  
  # Delete data 
  4. Http delete method sends a delete request to the backend.
      An id needs to be mentioned with delete method. This id identifies which data to delete from the database.
      axios.delete(url)
            .then()
            .catch()
       
       Please note the url will have id attached to it.
 
  
  # Refer the following to know how server handles these requests
  [Server handling requests](https://github.com/Ankhi12/NodeJS-and-APIs/blob/main/axios%20request%20cheatSheet.md)
   
