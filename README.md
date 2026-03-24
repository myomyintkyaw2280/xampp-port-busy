# Fix Apache Not Starting in XAMPP (Port 80 Conflict)

If Apache fails to start in XAMPP, it’s usually because another service is already using **Port 80**. Below are three methods to resolve the issue.

---

## ✅ Method 1: Stop World Wide Web Publishing Service (Quick Fix)

This Windows service often uses Port 80.

### Steps:
1. Press `Win + R`
2. Type `services.msc` and press Enter
3. Find **World Wide Web Publishing Service**
4. Right-click → **Stop**
5. (Optional) Prevent auto-start:
   - Right-click → **Properties**
   - Set **Startup type** to `Manual`

### Result:
- Apache should now start normally in XAMPP.

---

## ✅ Method 2: Change Apache Port (Conflict-Free Way)

Instead of stopping services, you can change Apache to use another port (e.g., 8080).

### Steps:
1. Open **XAMPP Control Panel**
2. Click **Config** next to Apache → select `httpd.conf`
3. Find:


Listen 80


Change to:
```
Listen 8080
```
4. Find:
```
ServerName localhost:80
```

Change to:
```
ServerName localhost:8080
```

5. Save the file
6. Restart Apache

### Access your project:
```
[http://localhost:8080/your-project](http://localhost:8080/your-project)
```

---

## ✅ Method 3: Stop SQL Server Reporting Services

If you have SQL Server installed, it may occupy Port 80.

### Steps:
1. Open `services.msc`
2. Find **SQL Server Reporting Services**
3. Right-click → **Stop**

---

## 🔍 Tips

- Only one service can use a port at a time
- Port 80 is commonly used by:
  - IIS (World Wide Web Publishing Service)
  - Skype (older versions)
  - SQL Server Reporting Services

---

## 🚀 Recommendation

- Use **Method 1** for quick fix  
- Use **Method 2** for long-term stability (recommended for developers)

---

## 📌 Author Notes

- Tested on Windows with XAMPP
- Works for Apache (Laravel, PHP projects, etc.)

---
