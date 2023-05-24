
# Server Handling Frontend HTTP Requests to manipulate Database

We are using express.js as server.

  ``const express= require('express')`` // 1st. npm install express, 2nd. importing express file via require method.

  ``const mongoose = require('mongoose')`` // mongoose - A driver to connect to MongoDB.
  
  ``const app = express()`` // Express routing - it listens to incoming request type and route to appropriate route methods like get()/post()/put()/delete()
  
  ``const port = 3033`` // A port number for server up and running
  
  ``const cors = require('cors')``// Enables cross origin resource sharing. Please import cors and enable cors if and only if you want to allow cross origin connection.
  
  ``app.use(cors())`` // use - uploads a middleware function.
  ``app.use(express.json())`` // use - uploads a middleware function.
  
  ``mongoose.connect('mongodb://127.0.0.1:27017/[your database name will go here]')
          .then(db=> console.log('Connected to DB.'))
          .catch(err=> console.log('Error Occured!', err))``
          
`` const {Schema} = mongoose`` // Object destructuring to get the Schema property from mongoose.
 
 const [insert your collectionName] = new Schema(

 {
 
  field1:
  
  {
  
  type: String,
  
  required: true,
  
  unique: true
  
  },
  
  field2:
  
  {
  
  type: Number,
  
  required: true
  },
  
  field3:
  
  {
  
  type: Schema.Types.ObjectId // To refer to other collection field name. For joining two collections.
  
  ref: [other collectionName]
  },
  
  field4:
  
  {
  
  type: Array,
  
  default: []
  
  }
  
 }
 
 ``
 const [ModelName] = mongoose.model('[ModelName]',[collectionName - same as that of line 25]) // A model helps server to talk with MongoDB database based on HTTP request
 ``
 
 **Server handling Get request**
 
 app.get('/student', (req, res)=>{
 
       ModelName.find()
       
                 .then(result=> res.json(result))  // json() is express middleware, that parses incoming request with JSON payloads. Then the fetched data is sent to the frontend.
       
                  .catch(err=> res.json(err))
                  
 })
 
 
  app.get('/student/:id', (req, res)=>{
 
       ModelName.find({id: req.params.id}) // id is sent as get parameter. Hence, using params , Also you can use find() or findById()
       
                 .then(result=> res.json(result))  // json() is express middleware, that parses incoming request with JSON payloads. Then the fetched data is sent to the frontend.
       
                  .catch(err=> res.json(err))
                  
 })
 
  **Server handling Post request**
 
 app.post('/student', (req, res)=>{
      
       const {body} = req // Post send data via request body. Hence destructuring body from req.
       
       const variableName = new ModelName(body) // We are creating a new Model Object. We are going to save this data in the backend.
       
       variableName.save()
                    
                    .then(result=> res.json('Data saved sucessfully!'))
                    
                    .catch(err=> res.json('Fault Occured!'))
                  
 })
 
  **Server handling Put request**
 
 app.put('/student/:id', (req, res)=>{ // Here we need id to update specific data.
      
       const {body} = req 
       
       ModelName.findByIdAndUpdate(body.id, {name: body.name}) // second parameter is the one that field you'll want to change for that record.
            
                 .then(result=> res.json('Updated Successfully!'))
                 
                 .catch(err=> res.json('Error Occured!'))
      
                  
 })
 
 **Server handling Delete request**
 
 app.delete('/student/:id', (req, res)=>{ // Here we need id to update specific data.
 
       
       ModelName.deleteOne({id: req.params.id})
      
                 .then(result=> res.json('Deleted Successfully!'))
                 
                 .catch(err=> res.json('Error Occured!'))
      
                  
 })
 
 
 
 # References
 1. https://mongoosejs.com/docs/schematypes.html
 2. https://expressjs.com/en/api.html#express.json
