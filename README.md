let stockList = JSON.parse(localStorage.getItem("engineer_stock")) || [];
let editIndex = null;

function saveItem() {
    const name = itemName.value;
    const code = itemCode.value;
    const category = itemCategory.value;
    const qty = Number(itemQty.value);
    const min = Number(itemMin.value);

    if (!name || !code || !category || !qty || !min) {
        alert("กรุณากรอกข้อมูลให้ครบ");
        return;
    }

    const item = { name, code, category, qty, min };

    if (editIndex !== null) {
        stockList[editIndex] = item;
        editIndex = null;
        saveBtn.textContent = "บันทึก";
        cancelBtn.classList.add("hidden");
    } else {
        stockList.push(item);
    }

    saveToLocal();
    renderTable();
    clearForm();
}

function renderTable() {
    const tbody = document.querySelector("#stockTable tbody");
    tbody.innerHTML = "";

    stockList.forEach((item, i) => {
        let statusClass = "normal";
        let statusText = "เพียงพอ";

        if (item.qty <= item.min) {
            statusClass = "low";
            statusText = "สต็อกอันตราย!";
        } else if (item.qty <= item.min + 3) {
            statusClass = "warn";
            statusText = "ใกล้หมด";
        }

        tbody.innerHTML += `
            <tr class="${statusClass}">
                <td>${item.name}</td>
                <td>${item.code}</td>
                <td>${item.category}</td>
                <td>${item.qty}</td>
                <td>${item.min}</td>
                <td>${statusText}</td>
                <td>
                    <button onclick="editItem(${i})">แก้ไข</button>
                    <button class="red" onclick="deleteItem(${i})">ลบ</button>
                </td>
            </tr>
        `;
    });
}

function editItem(i) {
    const item = stockList[i];

    itemName.value = item.name;
    itemCode.value = item.code;
    itemCategory.value = item.category;
    itemQty.value = item.qty;
    itemMin.value = item.min;

    editIndex = i;
    saveBtn.textContent = "บันทึกการแก้ไข";
    cancelBtn.classList.remove("hidden");
}

function cancelEdit() {
    clearForm();
    editIndex = null;
    saveBtn.textContent = "บันทึก";
    cancelBtn.classList.add("hidden");
}

function deleteItem(i) {
    if (confirm("ต้องการลบรายการนี้หรือไม่?")) {
        stockList.splice(i, 1);
        saveToLocal();
        renderTable();
    }
}

function searchItem() {
    const keyword = searchBar.value.toLowerCase();
    const rows = document.querySelectorAll("#stockTable tbody tr");

    rows.forEach(row => {
        row.style.display = row.innerText.toLowerCase().includes(keyword) ? "" : "none";
    });
}

function clearForm() {
    itemName.value = "";
    itemCode.value = "";
    itemCategory.value = "";
    itemQty.value = "";
    itemMin.value = "";
}

function saveToLocal() {
    localStorage.setItem("engineer_stock", JSON.stringify(stockList));
}

renderTable();
