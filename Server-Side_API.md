### **📌Writing a Server-Side API with Flask**  

#### **Title:** *Building a Simple REST API with Flask*  

#### **Content:**  
✅ **Goal:** Create a **custom API** that provides data via HTTP requests.  
✅ **Tech Stack:** Python (`Flask`), JSON, REST API principles.  

### **🔹 Step 1: Install Flask**  
- If Flask is not installed, run:  
  ```bash
  pip install flask
  ```

### **🔹 Step 2: Create a Basic Flask API**  
- Save this as **`app.py`** and run it.  
  ```python
  from flask import Flask, jsonify

  app = Flask(__name__)

  @app.route("/api/greet")
  def greet():
      return jsonify({"message": "Hello, World!"})

  if __name__ == "__main__":
      app.run(debug=True)
  ```
- **How It Works:**  
  - Starts a web server on `http://127.0.0.1:5000/api/greet`.  
  - Returns a **JSON response** when accessed.

### **🔹 Step 3: Test the API in a Browser or Postman**  
- Open:  
  ```
  http://127.0.0.1:5000/api/greet
  ```
- Expected JSON response:
  ```json
  {
      "message": "Hello, World!"
  }
  ```

### **🔹 Step 4: Extend the API with Dynamic Endpoints**  
- Allow users to **pass parameters** via the URL.
  ```python
  @app.route("/api/greet/<name>")
  def greet_name(name):
      return jsonify({"message": f"Hello, {name}!"})
  ```
- **Example Request:**  
  ```
  http://127.0.0.1:5000/api/greet/Alex
  ```
- **Response:**  
  ```json
  {
      "message": "Hello, Alex!"
  }
  ```

### **🔹 Step 5: Deploying the API (Optional)**  
- Deploy on **Render, Heroku, or AWS Lambda**.  
- Make it **publicly accessible** using Flask’s built-in `host` argument:
  ```python
  if __name__ == "__main__":
      app.run(host="0.0.0.0", port=5000)
  ```

#### **Activity:**  
🛠️ Students:  
   - Create a **Flask API** that returns a **random joke**.  
   - Modify the API to accept **user input** (e.g., a name or category).  
   - Test the API using **Postman or a web browser**.  
