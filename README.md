<Engineering>
<html lang="th">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Stock engineer system</title>
    <link rel="stylesheet" href="style.css" />
</head>
<body>

<h2>📦 ระบบเช็คสต็อกสินค้า</h2>

<div class="container">

    <div class="form">
        <h3>เพิ่ม / แก้ไขสินค้า</h3>

        <input id="productName" type="text" placeholder="ชื่อสินค้า">
        <input id="productCode" type="text" placeholder="รหัสสินค้า">
        <input id="productQty" type="number" placeholder="จำนวน">
        <input id="productLow" type="number" placeholder="แจ้งเตือนเมื่อสต็อกต่ำกว่า...">

        <button id="saveBtn" onclick="saveProduct()">บันทึกสินค้า</button>
        <button id="cancelEditBtn" onclick="cancelEdit()" class="hidden">ยกเลิกการแก้ไข</button>
    </div>

    <div class="search-box">
        <input id="searchInput" type="text" placeholder="ค้นหาสินค้า..." onkeyup="searchProduct()">
    </div>

    <div class="summary">
        <p><strong>จำนวนทั้งหมด:</strong> <span id="totalQty">0</span> ชิ้น</p>
        <button onclick="clearAll()" class="danger">ลบข้อมูลทั้งหมด</button>
    </div>

    <table id="stockTable">
        <thead>
            <tr>
                <th>ชื่อสินค้า</th>
                <th>รหัสสินค้า</th>
                <th>จำนวน</th>
                <th>แจ้งเตือนต่ำกว่า</th>
                <th>สถานะ</th>
                <th>การจัดการ</th>
            </tr>
        </thead>
        <tbody></tbody>
    </table>

</div>

<script src="script.js"></script>

</body>
</html>
