
    
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

  h2 {
    text-align: center;
    margin-bottom: 20px;
  }

  .todo {
    margin-bottom: 20px;
  }

  .todo label {
    display: block;
    margin-bottom: 10px;
  }

  .todo input[type="text"] {
    width: calc(100% - 20px);
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 5px;
    margin-bottom: 10px;
  }

  .todo select {
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 5px;
    margin-bottom: 10px;
  }

  .todo button {
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    background-color: #007bff;
    color: #fff;
    cursor: pointer;
  }

  .list {
    list-style-type: none;
    padding: 0;
  }

  .list li {
    padding: 10px;
    border-bottom: 1px solid #ddd;
  }

  .list li.completed {
    text-decoration: line-through;
    color: #888;
  }

  .list li button {
    padding: 5px 10px;
    border: none;
    border-radius: 5px;
    background-color: #007bff;
    color: #fff;
    cursor: pointer;
    margin-left: 10px;
  }
</style>
</head>
<body>
<div class="container">
  <h2>To-Do List</h2>
  
  <!-- 전체 할 일 -->
  <div class="todo" id="allTodo">
    <h3>전체 할 일</h3>
    <ul class="list" id="allList"></ul>
  </div>

  <!-- 완료된 할 일 -->
  <div class="todo" id="completedTodo">
    <h3>완료된 할 일</h3>
    <ul class="list" id="completedList"></ul>
  </div>

  <!-- 미완료된 할 일 -->
  <div class="todo" id="uncompletedTodo">
    <h3>미완료된 할 일</h3>
    <ul class="list" id="uncompletedList"></ul>
  </div>
  
  <div class="add-todo">
    <label for="priority">우선순위:</label>
    <select id="priority">
      <option value="low">낮음</option>
      <option value="normal">보통</option>
      <option value="high">높음</option>
      <option value="very-high">아주 높음</option>
    </select>
    <br>
    <label for="task">할 일:</label>
    <input type="text" id="task">
    <button onclick="addTask()">추가하기</button>
  </div>
</div>

<script>
  let tasks = [];

  function renderList() {
    const allList = document.getElementById('allList');
    const completedList = document.getElementById('completedList');
    const uncompletedList = document.getElementById('uncompletedList');
    allList.innerHTML = '';
    completedList.innerHTML = '';
    uncompletedList.innerHTML = '';
    
    tasks.forEach((task, index) => {
      const listItem = document.createElement('li');
      listItem.textContent = `${index + 1}. [${task.priority}] ${task.content}`;
      if (task.completed) {
        listItem.classList.add('completed');
        completedList.appendChild(listItem);
      } else {
        uncompletedList.appendChild(listItem);
      }
      
      const toggleButton = document.createElement('button');
      toggleButton.textContent = task.completed ? '미해결' : '해결';
      toggleButton.addEventListener('click', () => {
        tasks[index].completed = !tasks[index].completed;
        renderList();
      });
      listItem.appendChild(toggleButton);
    });
  }

  function addTask() {
    const priority = document.getElementById('priority').value;
    const content = document.getElementById('task').value





