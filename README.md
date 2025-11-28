<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Engineer Stock Management</title>
    <link rel="stylesheet" href="style.css" />
</head>

<body>

<header>
    <h1>ENGINEER STOCK MANAGEMENT SYSTEM</h1>
    <p>ระบบจัดการสต็อกแผนก ENGINEER</p>
</header>

<div class="container">

    <!-- Form Add/Edit -->
    <div class="form-box">
        <h2>เพิ่ม / แก้ไขรายการสต็อก</h2>

        <input id="itemName" type="text" placeholder="ชื่ออุปกรณ์ (เช่น Cable,1310nm 3-Ports Circulator FC/APC,SM-G.652D-FC/UPC+FC/UPC+FC/APC-1M-2.0mm )">
        <input id="itemCode" type="text" placeholder="รหัส (เช่น 240-0325)">
        
        <select id="itemCategory">
            <option value="">เลือกหมวดหมู่</option>
            <option value="Tools">Tools</option>
            <option value="Electrical">Electrical</option>
            <option value="Mechanical">Mechanical</option>
            <option value="Spare Part">Spare Part</option>
            <option value="Safety">Safety</option>
        </select>

        <input id="itemQty" type="number" placeholder="จำนวน">
        <input id="itemMin" type="number" placeholder="สต็อกขั้นต่ำ (แจ้งเตือน)">

        <button id="saveBtn" onclick="saveItem()">บันทึก</button>
        <button id="cancelBtn" class="hidden" onclick="cancelEdit()">ยกเลิก</button>
    </div>

    <!-- Search -->
    <div class="search-box">
        <input id="searchBar" type="text" placeholder="ค้นหาชื่อ / รหัส / หมวดหมู่..." onkeyup="searchItem()">
    </div>

    <!-- Table -->
    <table id="stockTable">
        <thead>
            <tr>
                <th>ชื่ออุปกรณ์</th>
                <th>รหัส</th>
                <th>หมวดหมู่</th>
                <th>จำนวน</th>
                <th>ขั้นต่ำ</th>
                <th>สถานะ</th>
                <th>หมายเหตุ</th>
            </tr>
        </thead>
        <tbody></tbody>
    </table>

</div>

<script src="script.js"></script>

</body>
</html>
