# nodejs-render-aiven-lab

Part 1: Create a GitHub Repository
Step 1: Open https://github.com
Step 2: Click New Repository
Step 3: Name the repository:
nodejs-render-aiven-lab
Step 4: Set repository to Public
Step 5: Click Create Repository
Step 6: Clone the repository using Visual Studio Code
git clone https://github.com/YOUR_USERNAME/nodejs-render-aiven-lab.git

Part 2: Create Node.js Application
Step 1: Open terminal inside project folder
Step 2: Initialize project
npm init -y
Step 3: Install dependencies
npm install express mysql2
Step 4: Create file:
app.js
Step 5: Copy sample code
const express = require("express");
const mysql = require("mysql2");

const app = express();

const db = mysql.createConnection({
      host: "YOUR_AIVEN_HOST",
        user: "YOUR_USERNAME",
          password: "YOUR_PASSWORD",
            database: "defaultdb",
              port: "YOUR_PORT"
});

app.get("/", (req, res) => {
      db.query("SELECT NOW()", (err, result) => {
            if(err) throw err;
                res.send("Database Connected Successfully: " + result[0]["NOW()"]);
      });
});

const PORT = process.env.PORT || 3000;

app.listen(PORT, () => {
      console.log("Server running on port " + PORT);
});
Step 6: Create start script in package.json
"start": "node app.js"

Part 3: Setup Aiven MySQL Database
Step 1: Login to https://aiven.io
Step 2: Create MySQL Service
Step 3: Copy the following credentials:
Hostname
Username
Password
Port
Database Name
Step 4: Replace credentials inside app.js
Example:
host: mysql-xxxx.aivencloud.com
Save changes.

Part 4: Upload Project to GitHub
Step 1: Open terminal
Step 2: Run commands
git add .
git commit -m "Initial commit"
git push
Verify repository uploaded successfully.

Part 5: Deploy Application Using Render
Step 1: Login to https://render.com
Step 2: Click New +
Step 3: Select Web Service
Step 4: Connect GitHub repository
Step 5: Select repository
nodejs-render-aiven-lab
Step 6: Configure deployment settings
Runtime:
Node
Build Command:
npm install
Start Command:
npm start
Step 7: Click Create Web Service
Wait until deployment completes.

Part 6: Test the Deployment
Step 1: Copy generated Render URL
Example:
https://nodejs-render-aiven-lab.onrender.com
Step 2: Open browser
Step 3: Verify output:
Database Connected Successfully
Take screenshot as proof.

Student Activity Tasks
Perform the following:
Task 1: Create GitHub repository
Task 2: Build Node.js application
Task 3: Connect Aiven MySQL database
Task 4: Deploy using Render
Task 5: Submit screenshot of working URL

Guide Questions
What is the role of GitHub in this activity?
Why is Aiven used in this deployment?
What is the function of Render platform?
What happens if database credentials are incorrect?
What is the purpose of environment PORT variable?

Submission Requirements
Students must submit:
GitHub repository link
Render deployment URL
Screenshot of successful database connection
End of Laboratory Activity