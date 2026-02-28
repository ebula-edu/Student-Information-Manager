# **Listah Documentation**

### *Student Information Manager*

This document provides a comprehensive guide for starting, understanding, and maintaining the **Listah** project. It includes step-by-step instructions, function explanations, and references to all files and assets used.

---

## **Table of Contents**

1. [Project Overview](#project-overview)    
2. [Project Structure](#project-structure)    
3. [Getting Started](#getting-started)    
4. [HTML Files](#html-files)    
5. [CSS Styling](#css-styling)    
6. [JavaScript Functions](#javascript-functions)    
7. [Assets](#assets)    
8. [Usage Instructions](#usage-instructions)    
9. [Development Notes](#development-notes)    

---

## **Project Overview**

**Listah** is a responsive and user-friendly student information manager created for **Computer Programming 1**.  

It allows users to:

- Add, view, and delete student records  
- Save data locally in the browser using `localStorage`  
- Experience a visually engaging interface with animations and responsive design  

The project emphasizes:

- Simplicity and clarity for beginner programmers  
- Modern design principles  
- Practical implementation of JavaScript, CSS, and HTML  

---

## **Project Structure**

```bash
Listah/
├─ assets/             # Folder for images
│   ├─ LISTAH.jpg      # Project logo
│   ├─ eldrex.png      # Eldrex profile image
│   ├─ marvs.png       # Marvin alternate image
│   ├─ marvin.png      # Marvin profile image
│   ├─ mark.png        # Mark profile image
│   ├─ jimwel.png      # Jimwel profile image
│   └─ renzo.png       # Renzo profile image
├─ css/
│   └─ main.css        # Styling for the project
├─ js/
│   └─ main.js         # JavaScript functions
├─ main.html           # Main student management page
├─ index.html          # Loading screen page
└─ README.md           # Project documentation


---

Getting Started

1. Clone the repository:



git clone https://github.com/eldrexdelosreyesbula/Student-Information-Manager.git

2. Open index.html in a browser to view the loading screen.


3. After the loading animation, it automatically redirects to main.html where you can manage student records.


4. No server setup is required; the project runs entirely in the browser.




---

HTML Files

index.html

Loading screen with animated student images and text

Progress bar and humorous notes display

Redirects to main.html after 7 seconds


main.html

Main student management page

Contains:

Header with project title and About link

Button to add new student (Add New Student)

Student list container (#list)

Overlay form to input Name, Year, and Section

Buttons to save or cancel form inputs


Scripts included: js/main.js



---

CSS Styling

css/main.css

1. Global Styles



* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
body {
    background: #f5f5f5;
    font-family: Arial, sans-serif;
}

2. Header



.header {
    background: #4a6fa5;
    color: white;
    padding: 20px;
    text-align: center;
    font-size: 24px;
    font-weight: bold;
    display: flex;
    justify-content: center;
    align-items: center;
    position: relative;
}

3. Student List & Items



White card-like container with shadows and spacing

Empty-message shows when no data is present

Animations applied to empty state images


4. Overlay Form



Centered popup (#overlay)

Inputs for name, year, and section

Buttons: Save (adds student) and Cancel (closes form)


5. Responsiveness



Mobile-friendly using media queries

Flex adjustments for student items and buttons



---

JavaScript Functions

js/main.js

Variables

let data = []; // array storing student objects

1. load()

Retrieves saved data from localStorage

Parses JSON string to object

Calls show() to display the student list


function load() {
    let saved = localStorage.getItem("list");
    data = saved ? JSON.parse(saved) : [];
    show();
}

2. save()

Converts data array to JSON string

Saves to localStorage

Calls show() to update UI


function save() {
    localStorage.setItem("list", JSON.stringify(data));
    show();
}

3. show()

Updates student list dynamically

Handles empty state with an image and message

Loops through data to create elements for each student


<div class="student-item">
    <div class="student-info">
        <h3>Student Name</h3>
        <p>Year: X | Section: Y</p>
    </div>
    <div class="student-actions">
        <button class="delete-btn">Delete</button>
    </div>
</div>

4. showForm() & hideForm()

function showForm() {
    document.getElementById("overlay").style.display = "flex";
    document.getElementById("name").focus();
}

function hideForm() {
    document.getElementById("overlay").style.display = "none";
    clear();
}

5. clear()

Resets all form inputs (name, year, section)


function clear() {
    document.getElementById("name").value = "";
    document.getElementById("year").value = "";
    document.getElementById("section").value = "";
}

6. add()

Validates input fields

Adds student object to data


function add() {
    let n = document.getElementById("name").value;
    let y = document.getElementById("year").value;
    let s = document.getElementById("section").value;

    if (n === "" || y === "" || s === "") {
        alert("Please fill all fields");
        return;
    }

    let obj = { name: n, year: y, section: s };
    data.push(obj);
    alert("Student added!");
    save();
    hideForm();
}

7. remove(index)

Confirms deletion with confirm()

Removes student object from data using splice()

Saves updated array


function remove(index) {
    if (confirm("Are you sure you want to delete this student?")) {
        data.splice(index, 1);
        save();
    }
}

8. Initialization

window.onload = function() {
    load();
    document.getElementById("addBtn").onclick = function() {
        clear();
        showForm();
    };
    document.getElementById("saveBtn").onclick = add;
    document.getElementById("cancelBtn").onclick = hideForm;
};


---

Assets

File	Description

LISTAH.jpg	Project logo
eldrex.png	Eldrex profile image
marvs.png	Marvin alternate image
marvin.png	Marvin profile image
mark.png	Mark profile image
jimwel.png	Jimwel profile image
renzo.png	Renzo profile image


> Note: All images are for educational use only and must not be reused outside this project.




---

Usage Instructions

1. Open index.html in a browser.


2. Observe the loading screen animations.


3. After loading, the main page appears with student management options.


4. Click Add New Student to open the overlay form.


5. Fill in Name, Year, and Section.


6. Click Save to add student.


7. Use Delete button to remove students.


8. All changes are saved in browser localStorage and persist on refresh.




---

Development Notes

Designed for educational purposes and local usage only.

Uses vanilla JavaScript, HTML, and CSS.

No backend is required; persistent data is handled with localStorage.

Empty state animations improve user feedback.

Fully responsive and works on mobile and desktop.



---

> Listah demonstrates core programming concepts: DOM manipulation, event handling, array operations, JSON handling, and responsive UI design for beginner-level developers.

