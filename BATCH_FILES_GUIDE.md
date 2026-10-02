# 🖱️ DIRAM Batch Files Guide
## Easy Windows Commands for DIRAM System

This guide explains all the `.bat` files that make running DIRAM super easy on Windows!

---

## 🚀 **Quick Start (Recommended)**

### **For First Time Setup:**
```batch
complete_setup.bat
```
- ✅ Installs all dependencies
- ✅ Sets up database with sample data
- ✅ Tests all components
- ✅ Starts DIRAM system automatically
- **Perfect for beginners!**

---

## 📋 **All Available Batch Files**

### **1. 🚀 start_diram.bat**
**Main command to start DIRAM**
```batch
start_diram.bat
```
**What it does:**
- Checks if Python is installed
- Checks if database exists (creates it if missing)
- Starts the FastAPI server on http://localhost:8000
- Shows all important URLs

**Use when:** You want to start DIRAM normally

---

### **2. 💾 setup_database.bat**
**Set up database and dependencies**
```batch
setup_database.bat
```
**What it does:**
- Installs Python packages from requirements.txt
- Creates SQLite database with tables
- Adds admin user (admin/admin123)
- Adds sample articles for testing

**Use when:** First time setup or after errors

---

### **3. 🧪 test_diram.bat**
**Test all system components**
```batch
test_diram.bat
```
**What it does:**
- Tests database connection
- Tests enhanced scrapers
- Tests alert system
- Tests background processor
- Shows component status

**Use when:** You want to verify everything works

---

### **4. 📊 check_database.bat**
**Check database status and info**
```batch
check_database.bat
```
**What it does:**
- Shows database statistics (users, articles, alerts)
- Shows database file size and location
- Displays when database was last modified

**Use when:** You want to see system status

---

### **5. ⚠️ reset_database.bat**
**Reset database completely**
```batch
reset_database.bat
```
**What it does:**
- ⚠️ **WARNING: Deletes ALL data!**
- Removes existing database file
- Creates fresh database
- Adds default admin user

**Use when:** You want to start completely fresh

---

### **6. 🚀 complete_setup.bat**
**Complete setup and start (All-in-one)**
```batch
complete_setup.bat
```
**What it does:**
- Checks Python installation
- Installs all dependencies
- Sets up database if needed
- Tests all components
- Starts DIRAM system
- **Perfect for first-time users!**

---

## 🎯 **Common Usage Scenarios**

### **Scenario 1: First Time User**
```batch
# Run this once:
complete_setup.bat
```
This will do everything automatically!

### **Scenario 2: Daily Use**
```batch
# Just double-click:
start_diram.bat
```
Your daily command to start DIRAM.

### **Scenario 3: Having Problems?**
```batch
# Test everything:
test_diram.bat

# Check what's in database:
check_database.bat

# If still broken, reset:
reset_database.bat
```

### **Scenario 4: Clean Installation**
```batch
# Reset everything:
reset_database.bat

# Then setup fresh:
setup_database.bat

# Or do both at once:
complete_setup.bat
```

---

## 🔧 **Troubleshooting**

### **Issue: "Python is not installed"**
**Solution:**
1. Download Python 3.8+ from https://python.org
2. During installation, check "Add to PATH"
3. Run the batch file again

### **Issue: "Database setup failed"**
**Solution:**
```batch
reset_database.bat
```

### **Issue: "Port 8000 already in use"**
**Solution:**
- Close other applications using port 8000
- Or kill the existing DIRAM process
- Then run `start_diram.bat` again

### **Issue: "Dependencies failed to install"**
**Solution:**
```batch
# Manually install:
pip install -r requirements.txt

# Then run:
setup_database.bat
```

---

## 📱 **Access Your System**

After running any start command, access DIRAM at:

- **🏠 Main System:** http://localhost:8000
- **📚 API Documentation:** http://localhost:8000/docs
- **❤️ Health Check:** http://localhost:8000/health

---

## 🔑 **Default Login**

```
Username: admin
Password: admin123
Email: admin@diram.ma
```

---

## 💡 **Pro Tips**

### **Tip 1: Create Desktop Shortcuts**
1. Right-click on `start_diram.bat`
2. Select "Create shortcut"
3. Drag shortcut to desktop
4. Now you can start DIRAM with one click!

### **Tip 2: Always Check First**
Before reporting issues, run:
```batch
test_diram.bat
check_database.bat
```

### **Tip 3: Weekly Maintenance**
Once a week, run:
```batch
test_diram.bat
```
To make sure everything is healthy.

### **Tip 4: Development Mode**
For development, use:
```batch
start_diram.bat
```
It shows detailed logs in the console.

---

## 🆘 **Need Help?**

1. **Check the batch file output** - it shows helpful error messages
2. **Run test_diram.bat** - to diagnose issues
3. **Try reset_database.bat** - if database is corrupted
4. **Use complete_setup.bat** - for fresh installation

---

## 🎉 **You're All Set!**

Just double-click **`start_diram.bat`** to begin your diplomatic intelligence journey!

**Welcome to DIRAM - Your AI-powered diplomatic intelligence system! 🇲🇦🤖** 
