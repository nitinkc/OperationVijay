1. **Create a new playlist (POST)**

   **Endpoint:** `/playlists`
   
   **Description:** Create a new playlist in the music store.
   
   **Request Body:**
   ```json
   {
     "name": "My Awesome Playlist"
   }
   ```
   
   **Response:**
   ```json
   {
     "id": 1,
     "name": "My Awesome Playlist"
   }
   ```

2. **Update an existing playlist (PUT)**

   **Endpoint:** `/playlists/{playlistId}`
   
   **Description:** Update an existing playlist in the music store.
   
   **Request Body:**
   ```json
   {
     "name": "New Playlist Name"
   }
   ```
   
   **Response:**
   ```json
   {
     "id": 1,
     "name": "New Playlist Name"
   }
   ```

3. **Delete a playlist (DELETE)**

   **Endpoint:** `/playlists/{playlistId}`
   
   **Description:** Delete a playlist from the music store.
   
   **Response:**
   ```json
   {
     "message": "Playlist deleted successfully"
   }
   ```

4. **Add a track to a playlist (PATCH)**

   **Endpoint:** `/playlists/{playlistId}/addTrack`
   
   **Description:** Add a track to an existing playlist in the music store.
   
   **Request Body:**
   ```json
   {
     "trackId": 12345
   }
   ```
   
   **Response:**
   ```json
   {
     "message": "Track added to the playlist successfully"
   }
   ```


5. **Create a new invoice (POST)**

   **Endpoint:** `/invoices`
   
   **Description:** Create a new invoice in the music store.
   
   **Request Body:**
   ```json
   {
     "customerId": 12345,
     "items": [
       {
         "trackId": 54321,
         "quantity": 2
       },
       {
         "trackId": 98765,
         "quantity": 1
       }
     ]
   }
   ```
   
   **Response:**
   ```json
   {
     "invoiceId": 1001,
     "customerId": 12345,
     "totalAmount": 9.98
   }
   ```

6. **Update an existing invoice (PUT)**

   **Endpoint:** `/invoices/{invoiceId}`
   
   **Description:** Update an existing invoice in the music store.
   
   **Request Body:**
   ```json
   {
     "items": [
       {
         "invoiceLineId": 1,
         "quantity": 3
       },
       {
         "invoiceLineId": 2,
         "quantity": 1
       }
     ]
   }
   ```
   
   **Response:**
   ```json
   {
     "invoiceId": 1001,
     "customerId": 12345,
     "totalAmount": 14.97
   }
   ```

7. **Delete an invoice (DELETE)**

   **Endpoint:** `/invoices/{invoiceId}`
   
   **Description:** Delete an invoice from the music store.
   
   **Response:**
   ```json
   {
     "message": "Invoice deleted successfully"
   }
   ```

8. **Add a new customer (POST)**

   **Endpoint:** `/customers`
   
   **Description:** Add a new customer to the music store.
   
   **Request Body:**
   ```json
   {
     "firstName": "John",
     "lastName": "Doe",
     "email": "john.doe@example.com",
     "address": "123 Main St",
     "city": "New York",
     "country": "USA"
   }
   ```
   
   **Response:**
   ```json
   {
     "customerId": 56789,
     "firstName": "John",
     "lastName": "Doe",
     "email": "john.doe@example.com",
     "address": "123 Main St",
     "city": "New York",
     "country": "USA"
   }
   ```

9. **Update customer details (PUT)**

   **Endpoint:** `/customers/{customerId}`
   
   **Description:** Update customer details in the music store.
   
   **Request Body:**
   ```json
   {
     "firstName": "Jane",
     "lastName": "Smith",
     "email": "jane.smith@example.com",
     "address": "456 Oak Ave",
     "city": "Los Angeles",
     "country": "USA"
   }
   ```
   
   **Response:**
   ```json
   {
     "customerId": 56789,
     "firstName": "Jane",
     "lastName": "Smith",
     "email": "jane.smith@example.com",
     "address": "456 Oak Ave",
     "city": "Los Angeles",
     "country": "USA"
   }
   ```

10. **Delete a customer (DELETE)**

    **Endpoint:** `/customers/{customerId}`
    
    **Description:** Delete a customer from the music store.
    
    **Response:**
    ```json
    {
      "message": "Customer deleted successfully"
    }
    ```

11. **Create a new employee (POST)**

    **Endpoint:** `/employees`
    
    **Description:** Create a new employee in the music store.
    
    **Request Body:**
    ```json
    {
      "firstName": "Michael",
      "lastName": "Johnson",
      "title": "Sales Manager",
      "birthDate": "1985-07-15",
      "hireDate": "2023-01-10",
      "address": "789 Elm St",
      "city": "Chicago",
      "country": "USA"
    }
    ```
    
    **Response:**
    ```json
    {
      "employeeId": 24680,
      "firstName": "Michael",
      "lastName": "Johnson",
      "title": "Sales Manager",
      "birthDate": "1985-07-15",
      "hireDate": "2023-01-10",
      "address": "789 Elm St",
      "city": "Chicago",
      "country": "USA"
    }
    ```

12. **Update an employee (PUT)**

    **Endpoint:** `/employees/{employeeId}`
    
    **Description:** Update employee details in the music store.
    
    **Request Body:**
    ```json
    {
      "firstName": "Emily",
      "lastName": "Anderson",
      "title": "Senior Sales Manager",
      "hireDate": "2022-05-20",
      "address": "456 Pine St",
      "city": "Seattle",
      "country": "USA"
    }
    ```
    
    **Response:**
    ```json
    {
      "employeeId": 24680,
      "firstName": "Emily",
      "lastName": "Anderson",
      "title": "Senior Sales Manager",
      "hireDate": "2022-05-20",
      "address": "456 Pine St",
      "city": "Seattle",
      "country": "USA"
    }
    ```