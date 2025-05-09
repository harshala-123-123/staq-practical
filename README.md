
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Digital Notice Board</title>
  <link rel="stylesheet" href="style.css">
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;700&display=swap" rel="stylesheet">
</head>
<body>
  
<a href="module1.html">Go to Module 1</a>
<a href="module2.html">Go to Module 2</a>


  <!-- Dark Mode Toggle -->
  <div class="toggle-container">
    <label class="switch">
      <input type="checkbox" id="darkModeToggle">
      <span class="slider"></span>
    </label>
  </div>

  <!-- Header -->
  <header>
    <h1>📢 Digital Notice Board</h1>
  </header>

  <!-- Search and Category Filter -->
  <section class="search-filter">
    <input type="text" id="searchInput" placeholder="Search notices...">
    <select id="categoryFilter">
      <option value="">All Categories</option>
      <option value="General">General</option>
      <option value="Event">Event</option>
      <option value="Exam">Exam</option>
    </select>
  </section>

  <!-- Recent Notices Slider -->
  <section class="recent-notices" id="recentNotices">
    <h2>Recent Notices</h2>
    <div class="recent-slider" id="slider">
      <!-- Sliding notices here -->
    </div>
  </section>

  <!-- Notices Section -->
  <section class="notices" id="noticeBoard">
    <!-- Dynamic Notices -->
  </section>

  <!-- Upload Notice Section -->
  <section class="upload-section">
    <h2>Post a New Notice</h2>
    <form id="noticeForm">
      <input type="text" id="noticeTitle" placeholder="Notice Title" required>
      <textarea id="noticeDescription" placeholder="Notice Description" required></textarea>
      <select id="noticeCategory" required>
        <option value="">Select Category</option>
        <option value="General">General</option>
        <option value="Event">Event</option>
        <option value="Exam">Exam</option>
      </select>
      <input type="file" id="noticeFile">
      <span id="fileNamePreview"></span>
      <button type="submit">Post Notice</button>
    </form>
  </section>

  <!-- Footer -->
  <footer>
    <p>&copy; 2025 Digital Notice Board. All rights reserved.</p>
  </footer>

  <script src="script.js"></script>
</body>
</html>
<style>
  /* Reset */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Poppins', sans-serif;
  background: #f0f2f5;
  color: #333;
  transition: background 0.3s, color 0.3s;
}

/* Dark Mode */
body.dark-mode {
  background: #1a1a2e;
  color: #e0e0e0;
}

header {
  background-color: #0077b6;
  color: white;
  text-align: center;
  padding: 20px;
}

.search-filter {
  margin: 20px auto;
  display: flex;
  justify-content: center;
  gap: 10px;
}

.search-filter input, .search-filter select {
  padding: 10px;
  border-radius: 8px;
  border: 1px solid #ccc;
}

.notices {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(270px, 1fr));
  gap: 20px;
  margin: 20px;
  padding: 10px;
}

.notice-card {
  background: white;
  padding: 20px;
  border-radius: 15px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  position: relative;
  transition: transform 0.3s;
}

.notice-card:hover {
  transform: translateY(-5px);
}

.notice-card h3 {
  margin-bottom: 10px;
}

.notice-card p {
  margin-bottom: 8px;
  font-size: 14px;
}

.notice-card .category {
  background-color: #caf0f8;
  padding: 5px 10px;
  border-radius: 5px;
  font-size: 12px;
  display: inline-block;
}

.notice-card button {
  background: red;
  color: white;
  padding: 5px 10px;
  border: none;
  border-radius: 8px;
  position: absolute;
  top: 10px;
  right: 10px;
  cursor: pointer;
}

.upload-section {
  background: #f1f1f1;
  padding: 30px;
  margin: 20px;
  border-radius: 10px;
}

.upload-section form {
  display: flex;
  flex-direction: column;
}

.upload-section input, 
.upload-section textarea,
.upload-section select {
  margin-bottom: 15px;
  padding: 10px;
  border-radius: 8px;
  border: 1px solid #ccc;
}

.upload-section button {
  padding: 10px;
  background: #0077b6;
  color: white;
  border: none;
  border-radius: 8px;
  cursor: pointer;
}

footer {
  text-align: center;
  padding: 15px;
  background: #0077b6;
  color: white;
  margin-top: 20px;
}

.toggle-container {
  position: absolute;
  top: 20px;
  right: 20px;
}

.switch {
  position: relative;
  display: inline-block;
  width: 50px;
  height: 24px;
}

.switch input {
  opacity: 0;
  width: 0;
  height: 0;
}

.slider {
  position: absolute;
  cursor: pointer;
  background-color: #ccc;
  border-radius: 24px;
  top: 0; left: 0;
  right: 0; bottom: 0;
  transition: .4s;
}

.slider:before {
  position: absolute;
  content: "";
  height: 18px;
  width: 18px;
  left: 3px;
  bottom: 3px;
  background-color: white;
  border-radius: 50%;
  transition: .4s;
}

input:checked + .slider {
  background-color: #2196F3;
}

input:checked + .slider:before {
  transform: translateX(26px);
}

.recent-notices {
  margin: 20px;
  padding: 10px;
}

.recent-slider {
  overflow-x: auto;
  white-space: nowrap;
}

.recent-slider div {
  display: inline-block;
  background: white;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 10px;
  box-shadow: 0 2px 6px rgba(0,0,0,0.1);
}

</style>
<script>
  const form = document.getElementById('noticeForm');
const noticeBoard = document.getElementById('noticeBoard');
const searchInput = document.getElementById('searchInput');
const categoryFilter = document.getElementById('categoryFilter');
const darkModeToggle = document.getElementById('darkModeToggle');
const fileNamePreview = document.getElementById('fileNamePreview');
const slider = document.getElementById('slider');

let notices = [];

// Post a new notice
form.addEventListener('submit', function(event) {
  event.preventDefault();

  const title = document.getElementById('noticeTitle').value;
  const description = document.getElementById('noticeDescription').value;
  const category = document.getElementById('noticeCategory').value;
  const fileInput = document.getElementById('noticeFile');

  let fileName = "";
  if (fileInput.files.length > 0) {
    fileName = fileInput.files[0].name;
  }

  const newNotice = {
    id: Date.now(),
    title,
    description,
    category,
    fileName,
    date: new Date().toLocaleDateString()
  };

  notices.unshift(newNotice);
  displayNotices();
  updateSlider();
  form.reset();
  fileNamePreview.textContent = "";
});

// Display notices
function displayNotices(filteredNotices = notices) {
  noticeBoard.innerHTML = '';

  filteredNotices.forEach(notice => {
    const card = document.createElement('div');
    card.className = 'notice-card';

    card.innerHTML = `
      <button onclick="deleteNotice(${notice.id})">X</button>
      <h3>${notice.title}</h3>
      <p>${notice.description}</p>
      <p><strong>Date:</strong> ${notice.date}</p>
      <span class="category">${notice.category}</span><br>
      ${notice.fileName ? `<a href="#">📄 ${notice.fileName}</a>` : ""}
    `;

    noticeBoard.appendChild(card);
  });
}

// Delete a notice
function deleteNotice(id) {
  notices = notices.filter(n => n.id !== id);
  displayNotices();
  updateSlider();
}

// Search Notices
searchInput.addEventListener('input', filterNotices);
categoryFilter.addEventListener('change', filterNotices);

function filterNotices() {
  const searchText = searchInput.value.toLowerCase();
  const selectedCategory = categoryFilter.value;

  const filtered = notices.filter(notice => 
    (notice.title.toLowerCase().includes(searchText) ||
    notice.description.toLowerCase().includes(searchText)) &&
    (selectedCategory === "" || notice.category === selectedCategory)
  );

  displayNotices(filtered);
}

// Dark Mode Toggle
darkModeToggle.addEventListener('change', function() {
  document.body.classList.toggle('dark-mode');
});

// File name preview
document.getElementById('noticeFile').addEventListener('change', function() {
  fileNamePreview.textContent = this.files[0]?.name || "";
});

// Update Recent Notices Slider
function updateSlider() {
  slider.innerHTML = '';
  notices.slice(0, 5).forEach(notice => {
    const slide = document.createElement('div');
    slide.textContent = notice.title;
    slider.appendChild(slide);
  });
}

</script>
