<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>To-Do List</title>
<style>
  body {
    font-family: Arial, sans-serif;
  }
  
  .container {
    max-width: 600px;
    margin: 0 auto;
    padding: 20px;
    background-color: #f9f9f9;
    border-radius: 5px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  }
  
  .input-group {
    display: flex;
    margin-bottom: 10px;
  }
  
  .input-group input[type="text"] {
    flex: 1;
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 5px 0 0 5px;
    outline: none;
  }
  
  .input-group button {
    padding: 10px 20px;
    border: none;
    border-radius: 0 5px 5px 0;
    background-color: #007bff;
    color: #fff;
    cursor: pointer;
  }
  
  ul {
    list-style-type: none;
    padding: 0;
  }
  
  li {
    padding: 10px;
    border-bottom: 1px solid #ddd;
    display: flex;
    align-items: center;
  }
  
  li input[type="checkbox"] {
    margin-right: 10px;
  }
</style>
</head>
<body>
<div class="container">
  <div class="input-group">
    <input type="text" id="taskInput" placeholder="할 일을 입력하세요...">
    <button onclick="addTask()">추가하기</button>
  </div>
  <ul id="taskList"></ul>
</div>

<script>
  function addTask() {
    var input = document.getElementById("taskInput");
    var task = input.value.trim();
    if (task === "") return;
    var listItem = document.createElement("li");
    listItem.innerHTML = '<input type="checkbox"><span>' + task + '</span>';
    document.getElementById("taskList").appendChild(listItem);
    input.value = "";
  }
</script>
</body>
</html>
