document.getElementById("addButton").addEventListener("click", addTask);
document.getElementById("taskInput").addEventListener("keypress", function(e) {
    if (e.key === "Enter") {
        addTask();
    }
});

function addTask() {
    let taskInput = document.getElementById("taskInput");
    let taskValue = taskInput.value.trim();

    if (taskValue !== "") {
        let taskList = document.getElementById("taskList");

        // Create list item
        let li = document.createElement("li");

        // Add task text
        let taskText = document.createTextNode(taskValue);
        li.appendChild(taskText);

        // Create delete button
        let deleteButton = document.createElement("button");
        deleteButton.textContent = "Delete";
        deleteButton.addEventListener("click", function() {
            li.remove();
        });

        li.appendChild(deleteButton);

        // Append to list
        taskList.appendChild(li);

        // Clear input field
        taskInput.value = "";
    } else {
        alert("Please enter a task!");
    }
}
