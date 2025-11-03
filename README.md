# 🧠 MLOPS-DVC  
### Implement Data Versioning Control using DVC (Data Version Control)

---

## 📘 Introduction  
This project demonstrates how to integrate **DVC (Data Version Control)** with **Git** to manage and track different versions of datasets efficiently in an **MLOps workflow**.  
By combining Git and DVC, we can version both **code and data**, ensuring full reproducibility and traceability in machine learning pipelines.

---

## 📂 Project Overview  
DVC helps manage datasets just like Git manages code — by storing lightweight metadata in the repository and pushing actual data to a remote storage (e.g., S3).  
This setup enables multiple versions of data to be synchronized and tracked seamlessly without bloating your Git repository.

### 🔧 Repository Structure  
```
MLOPS-DVC/
│
├── .dvc/                 # DVC internal files and cache links
├── S3/files/md5/         # Remote directory (simulated S3 storage)
├── .dvcignore            # Files ignored by DVC
├── .gitignore            # Files ignored by Git
├── LICENSE               # MIT License
├── README.md             # Project documentation
├── data.dvc              # DVC metadata file tracking dataset
├── my_code.py            # Python script generating or updating data
├── projectflow.txt       # Workflow explanation
├── requirements.txt      # Dependencies file
└── ...
```

---

## ⚙️ Requirements  
Install the required dependencies before running the project:

```bash
pip install -r requirements.txt
```

Or install DVC directly:

```bash
pip install dvc
```

---

## 🚀 Step-by-Step Implementation  

### **Step 1. Initialize Git Repository**
Create and clone a Git repository locally.

### **Step 2. Create Data Generation Script**
Create a file `my_code.py` that generates a CSV file and saves it inside a `data/` folder.

### **Step 3. Commit Initial Files**
```bash
git add .
git commit -m "first commit before DVC"
git push origin main
```

### **Step 4. Initialize DVC**
```bash
dvc init
```
This command creates `.dvc/` and `.dvcignore` files.

### **Step 5. Configure Remote Storage**
Create a simulated S3 directory and link it with DVC:
```bash
mkdir S3
dvc remote add -d myremote S3
```

### **Step 6. Track Data with DVC**
```bash
dvc add data/
git add .gitignore data.dvc
git commit -m "dvc with data version 1"
dvc push
```

➡️ **At this point:** You have your first version of data (V1) saved.

### **Step 7. Update Dataset**
Modify `my_code.py` to append new rows or update the data.

### **Step 8. Commit New Data Version**
```bash
dvc commit
dvc push
git add .
git commit -m "2nd version of data saved"
git push
```

➡️ **Now you have Version 2 (V2) of your dataset.**

### **Step 9. Repeat for More Versions**
Repeat steps 7–8 for additional versions (V3, V4, ...).

---

## 🧩 DVC Command Reference  

| Command | Description |
|----------|--------------|
| `dvc init` | Initialize DVC in the project |
| `dvc add <data_path>` | Start tracking data with DVC |
| `dvc commit` | Commit modifications to DVC-tracked files |
| `dvc push` | Upload data to remote storage |
| `dvc pull` | Download data from remote storage |
| `dvc status` | Display status of DVC-tracked files |

---

## 💡 Example Workflow Summary  

1. Initialize Git and DVC  
2. Add data and push the first version  
3. Modify your dataset through `my_code.py`  
4. Use `dvc commit` and `dvc push` to save new versions  
5. Check version status anytime using:
   ```bash
   dvc status
   ```
6. Each version can be restored anytime using:
   ```bash
   dvc checkout
   ```

---

## 🧠 Key Learnings  

- Integrated **DVC with Git** for dataset versioning.  
- Practiced **data reproducibility** across experiments.  
- Implemented **remote storage synchronization** via S3 simulation.  
- Maintained a **clean and lightweight Git repo** by ignoring raw data files.  

---

## 📜 License  
This project is licensed under the **MIT License**.  
See the [LICENSE](./LICENSE) file for details.

---

## 👨‍💻 Author  
**Vivek Kumar**  
📧 [GitHub: Vivekk-007](https://github.com/Vivekk-007)
