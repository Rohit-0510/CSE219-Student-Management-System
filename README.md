<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Student Management System</title>
    <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gray-100 p-10">
    <h2 class="text-2xl font-semibold mb-6">Student Management System</h2>
    
    <div class="overflow-x-auto">
        <table class="min-w-full bg-white border border-gray-300 shadow-md rounded-lg">
            <thead class="bg-gray-200">
                <tr>
                    <th class="px-6 py-3 text-left text-sm font-medium text-gray-500">Student Name</th>
                    <th class="px-6 py-3 text-left text-sm font-medium text-gray-500">Roll No</th>
                    <th class="px-6 py-3 text-left text-sm font-medium text-gray-500">Course</th>
                    <th class="px-6 py-3 text-left text-sm font-medium text-gray-500">Action</th>
                </tr>
            </thead>
            <tbody id="studentList">
            </tbody>
        </table>
    </div>

    <script>
        const students = [
            { name: "John Doe", id: "S1234", course: "Computer Science" },
            { name: "Jane Smith", id: "S5678", course: "Mathematics" },
            { name: "Sam Brown", id: "S91011", course: "Physics" },
            { name: "Emily Clark", id: "S1213", course: "Biology" }
        ];

        function renderStudentsWithForEach() {
            let tableBody = document.getElementById("studentList");
            tableBody.innerHTML = ""; 

            students.forEach((student, index) => {
                let row = document.createElement("tr");
                row.classList.add("border-t", "border-gray-200");

                let nameCell = document.createElement("td");
                nameCell.textContent = student.name;
                nameCell.classList.add("px-6", "py-4", "text-sm", "font-medium", "text-gray-900");

                let idCell = document.createElement("td");
                idCell.textContent = student.id;
                idCell.classList.add("px-6", "py-4", "text-sm", "font-medium", "text-gray-900");

                let courseCell = document.createElement("td");
                courseCell.textContent = student.course;
                courseCell.classList.add("px-6", "py-4", "text-sm", "font-medium", "text-gray-900");

                let actionCell = document.createElement("td");
                actionCell.classList.add("px-6", "py-4");

                let removeButton = document.createElement("button");
                removeButton.textContent = "Remove";
                removeButton.classList.add("px-4", "py-2", "text-white", "bg-red-600", "rounded", "hover:bg-red-700", "transition");
                removeButton.onclick = function () {
                    removeStudent(index);  
                  };

                actionCell.appendChild(removeButton);
                row.appendChild(nameCell);
                row.appendChild(idCell);
                row.appendChild(courseCell);
                row.appendChild(actionCell);

                tableBody.appendChild(row);
            });
        }

        function removeStudent(index) {
            students.splice(index, 1);  
            renderStudentsWithForEach(); 
        }
        renderStudentsWithForEach();
    </script>
</body>
</html>
