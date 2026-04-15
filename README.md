[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23572424&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student ID:** 2A202600066
**Name:** Ho Nhat Khoa

---

## Mo ta

Bai lab nay xay dung mot ETL Pipeline tu dong xu ly du lieu san pham tu file JSON, kiem tra chat luong du lieu, ap dung business logic (giam gia 10%, chuan hoa category), va luu ket qua ra CSV. Dong thoi, bai lab khao sat tac dong cua du lieu bi loi ("garbage data") den do chinh xac cua AI Agent.

---

## Cach chay (How to Run)

### Prerequisites
```bash
pip install pandas
```

### Chay ETL Pipeline
```bash
python solution.py
```

### Chay Agent Simulation (Stress Test)
```bash
# Buoc 1: Tao garbage data
python generate_garbage.py

# Buoc 2: Chay agent voi ca 2 bo du lieu
python agent_simulation.py
```

### Chay Tests
```bash
python -m pytest tests/test_autograder.py -v
```

---

## Cau truc thu muc

```
├── solution.py              # ETL Pipeline (extract, validate, transform, load)
├── raw_data.json            # Du lieu dau vao (5 records)
├── processed_data.csv       # Output sau ETL (3 records hop le)
├── garbage_data.csv         # Du lieu loi dung cho stress test
├── agent_simulation.py      # RAG-like agent demo
├── generate_garbage.py      # Tao du lieu bi loi
├── experiment_report.md     # Bao cao thi nghiem
└── README.md                # File nay
```

---

## Ket qua

Pipeline xu ly **5 records** tu `raw_data.json`:
- **3 records hop le** duoc luu vao `processed_data.csv` (Laptop, Chair, Monitor)
- **2 records bi loai**: Mystery Box (price = -10) va Phone (category rong)

Tat ca records dau ra co cot `discounted_price` (giam 10%), category chuan Title Case, va timestamp `processed_at`.
