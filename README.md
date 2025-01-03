<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Biểu Mẫu Nhập Thông Tin Nhóm</title>
    <style>
        /* Nền trang với hình ảnh dễ thương */
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-image: url('https://via.placeholder.com/1600x900.png?text=Background+Cute+Image'); /* Sử dụng hình ảnh nền dễ thương */
            background-size: cover;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            flex-direction: column;
            box-sizing: border-box;
        }

        /* Tiêu đề trang với hình ảnh dễ thương */
        header {
            background-color: rgba(0, 0, 0, 0.7);
            color: white;
            padding: 1rem;
            width: 100%;
            text-align: center;
            font-size: 30px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
            margin-bottom: 2rem;
            border-radius: 5px;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        /* Thêm hình ảnh vào header */
        header img {
            width: 50px;
            margin-right: 10px;
        }

        /* Chứa biểu mẫu và các thành phần */
        .form-container {
            background-color: #ffffff;
            border-radius: 12px;
            padding: 2rem;
            width: 80%;
            max-width: 800px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
            margin-bottom: 20px;
            background-color: #f7f7f7;
        }

        h2 {
            color: #333;
            text-align: center;
            margin-bottom: 20px;
            font-size: 24px;
            font-weight: 600;
        }

        /* Các thành phần trong form */
        label {
            font-weight: bold;
            color: #333;
            margin-bottom: 5px;
            display: block;
            font-size: 16px;
        }

        input[type="text"] {
            width: 100%;
            padding: 12px;
            border-radius: 8px;
            border: 1px solid #ddd;
            margin-bottom: 15px;
            box-sizing: border-box;
            font-size: 16px;
            transition: border 0.3s ease-in-out;
        }

        input[type="text"]:focus {
            border-color: #4CAF50;
            outline: none;
        }

        /* Các nút */
        .button {
            width: 100%;
            padding: 12px;
            font-size: 16px;
            border-radius: 8px;
            border: none;
            background-color: #4CAF50;
            color: white;
            cursor: pointer;
            transition: background-color 0.3s, transform 0.3s;
            margin-top: 20px;
        }

        .button:hover {
            background-color: #45a049;
            transform: scale(1.05);
        }

        .add-member-btn, .delete-member-btn {
            background-color: #f0ad4e;
            color: white;
            border-radius: 6px;
            padding: 10px 20px;
            margin-top: 10px;
            cursor: pointer;
            transition: background-color 0.3s, transform 0.3s;
            font-size: 14px;
        }

        .add-member-btn:hover {
            background-color: #ec971f;
            transform: scale(1.05);
        }

        .delete-member-btn {
            background-color: #d9534f;
        }

        .delete-member-btn:hover {
            background-color: #c9302c;
            transform: scale(1.05);
        }

        /* Căn giữa các phần tử trong các thành viên */
        .group-member {
            background-color: #ffffff;
            border-radius: 8px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.05);
            transition: transform 0.3s ease;
            display: flex;
            align-items: center;
        }

        .group-member:hover {
            transform: scale(1.02);
        }

        .group-member img {
            width: 40px;
            height: 40px;
            margin-right: 10px;
        }

        .group-member h3 {
            margin-top: 0;
            color: #333;
        }

        /* Bảng kết quả */
        .result-table {
            margin-top: 30px;
            width: 100%;
            max-width: 800px;
            border-collapse: collapse;
            background-color: #ffffff;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
        }

        .result-table th, .result-table td {
            border: 1px solid #ddd;
            padding: 12px;
            text-align: left;
            font-size: 16px;
        }

        .result-table th {
            background-color: #4CAF50;
            color: white;
        }

        .result-table tr:nth-child(even) {
            background-color: #f2f2f2;
        }

        /* Footer cho tác giả */
        footer {
            font-size: 16px;
            text-align: center;
            color: #333;
            margin-top: 30px;
            font-style: italic;
        }
    </style>
</head>
<body>

<header>
    <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRrq7XzpOyj8hHYVqp_onHKI9la344T742jVw&s"> <!-- Hình ảnh minh họa header -->
    <h1>Biểu Mẫu Nhập Thông Tin Nhóm</h1>
</header>

<div class="form-container">
    <h2>Vui lòng điền thông tin cho nhóm và từng thành viên</h2>

    <form id="infoForm" onsubmit="generateReport(event)">
        <!-- Thêm trường cho tên nhóm và tên bài thuyết trình -->
        <div class="form-group">
            <label for="groupName">Tên Nhóm:</label>
            <input type="text" id="groupName" name="groupName" required>
        </div>

        <div class="form-group">
            <label for="presentationTitle">Tên Bài Thuyết Trình:</label>
            <input type="text" id="presentationTitle" name="presentationTitle" required>
        </div>

        <div id="members-container"></div>

        <button class="add-member-btn" type="button" onclick="addMember()">Thêm Thành Viên</button>
        <br><br>

        <button type="submit" class="button">In Báo Cáo</button>
    </form>

    <br><br>
    <div id="report-container"></div>
</div>

<footer>
    <p>Tác giả: Bùi Anh Khôi</p>
</footer>

<script>
// Code to add members and handle form submission
let memberCount = 0;

function addMember() {
    memberCount++;

    const newMember = document.createElement('div');
    newMember.classList.add('group-member');
    newMember.id = `member-${memberCount}`;
    newMember.innerHTML = `
        <div>
            <h3>Thành viên ${memberCount}</h3>
            <label for="task${memberCount}">Việc Làm:</label>
            <input type="text" id="task${memberCount}" name="task${memberCount}" required>

            <label for="studentId${memberCount}">Mã Số Học Sinh:</label>
            <input type="text" id="studentId${memberCount}" name="studentId${memberCount}" required>

            <label for="studentName${memberCount}">Tên Học Sinh:</label>
            <input type="text" id="studentName${memberCount}" name="studentName${memberCount}" required>

            <!-- Nút xóa thành viên -->
            <button type="button" class="delete-member-btn" onclick="deleteMember(${memberCount})">Xóa Thành Viên</button>
        </div>
    `;

    document.getElementById('members-container').appendChild(newMember);
}

// Hàm xóa thành viên
function deleteMember(memberId) {
    const memberDiv = document.getElementById(`member-${memberId}`);
    memberDiv.remove();
}

function generateReport(event) {
    event.preventDefault();  // Ngừng gửi biểu mẫu

    const groupName = document.getElementById('groupName').value;
    const presentationTitle = document.getElementById('presentationTitle').value;

    // Bắt đầu tạo bảng báo cáo
    let reportHTML = `<h2>Báo Cáo Nhóm: ${groupName}</h2>`;
    reportHTML += `<h3>Tên Bài Thuyết Trình: ${presentationTitle}</h3>`;
    reportHTML += `<table class="result-table">
                    <tr>
                        <th>STT</th>
                        <th>Việc Làm</th>
                        <th>Mã Số Học Sinh</th>
                        <th>Tên Học Sinh</th>
                    </tr>`;

    // Lặp qua các thành viên và tạo dòng báo cáo
    for (let i = 1; i <= memberCount; i++) {
        const task = document.getElementById(`task${i}`).value;
        const studentId = document.getElementById(`studentId${i}`).value;
        const studentName = document.getElementById(`studentName${i}`).value;

        reportHTML += `<tr>
                        <td>${i}</td>
                        <td>${task}</td>
                        <td>${studentId}</td>
                        <td>${studentName}</td>
                    </tr>`;
    }

    reportHTML += `</table>`;

    // Hiển thị báo cáo trong phần 'report-container'
    document.getElementById('report-container').innerHTML = reportHTML;
}
</script>

</body>
</html>
