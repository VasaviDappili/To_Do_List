# Ex03 To-Do List using JavaScript
## Date:21/03/2025

## AIM
To create a To-do Application with all features using JavaScript.

## ALGORITHM
### STEP 1
Build the HTML structure (index.html).

### STEP 2
Style the App (style.css).

### STEP 3
Plan the features the To-Do App should have.

### STEP 4
Create a To-do application using Javascript.

### STEP 5
Add functionalities.

### STEP 6
Test the App.

### STEP 7
Open the HTML file in a browser to check layout and functionality.

### STEP 8
Fix styling issues and refine content placement.

### STEP 9
Deploy the website.

### STEP 10
Upload to GitHub Pages for free hosting.

## PROGRAM
## HTML
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>To-Do App</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="container">
        <h1>To-Do List</h1>
        <div class="input-section">
            <input type="text" id="task-input" placeholder="Add a new task...">
            <button onclick="addTask()">Add</button>
        </div>
        <ul id="task-list"></ul>
    </div>
    <script src="script.js"></script>
    <footer >
        <p>@2025 Dappili Vasavi 212223040030 | All rights reserved.</p>
    </footer>
</body>
</html>

```
## CSS
```
body {
    font-family: Arial, sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background-color: #f4f4f4;
}

.container {
    background: white;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    width: 350px;
    text-align: center;
}

.input-section {
    display: flex;
    gap: 10px;
    margin-bottom: 20px;
}

input {
    flex: 1;
    padding: 8px;
    border: 1px solid #ccc;
    border-radius: 4px;
}

button {
    background-color: #28a745;
    color: white;
    border: none;
    padding: 8px 12px;
    cursor: pointer;
    border-radius: 4px;
}

button:hover {
    background-color: #218838;
}

ul {
    list-style: none;
    padding: 0;
}

li {
    background: #eee;
    padding: 10px;
    margin: 5px 0;
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-radius: 4px;
}

li .delete-btn {
    background-color: red;
    color: white;
    border: none;
    padding: 4px 8px;
    cursor: pointer;
    border-radius: 4px;
}

li .delete-btn:hover {
    background-color: darkred;
}
footer {
    width: 100%;
    text-align: center;
    padding: 10px;
    background: #333;
    color: white;
    position: fixed;
    bottom: 0;
    left: 0;
}

```
## Javascript
```
document.addEventListener("DOMContentLoaded", loadTasks);

function addTask() {
    let taskInput = document.getElementById("task-input");
    let taskText = taskInput.value.trim();

    if (taskText === "") {
        alert("Please enter a task.");
        return;
    }

    let taskList = document.getElementById("task-list");
    let li = document.createElement("li");

    li.innerHTML = `
        <span class="task-text">${taskText}</span>
        <button class="delete-btn">Delete</button>
    `;

    
    li.querySelector(".delete-btn").addEventListener("click", function () {
        removeTask(li);
    });

    taskList.appendChild(li);
    saveTasks();
    taskInput.value = "";
}

function removeTask(li) {
    li.remove();
    saveTasks();
}

function saveTasks() {
    let tasks = [];
    document.querySelectorAll("#task-list li .task-text").forEach(span => {
        tasks.push(span.innerText);
    });
    localStorage.setItem("tasks", JSON.stringify(tasks));
}

function loadTasks() {
    let savedTasks = localStorage.getItem("tasks");
    if (savedTasks) {
        let taskList = document.getElementById("task-list");
        taskList.innerHTML = "";
        JSON.parse(savedTasks).forEach(task => {
            let li = document.createElement("li");
            li.innerHTML = `
                <span class="task-text">${task}</span>
                <button class="delete-btn">Delete</button>
            `;

            
            li.querySelector(".delete-btn").addEventListener("click", function () {
                removeTask(li);
            });

            taskList.appendChild(li);
        });
    }
}

```


## OUTPUT
![Screenshot 2025-03-21 214531](https://github.com/user-attachments/assets/4dc6918d-1809-40c6-be26-7a3db9a9dae4)



## RESULT
The program for creating To-do list using JavaScript is executed successfully.
