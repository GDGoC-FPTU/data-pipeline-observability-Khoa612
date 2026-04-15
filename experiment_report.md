# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** 2A202600066
**Name:** Ho Nhat Khoa
**Date:** 2026-04-15

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Based on my data, the best choice is Laptop at $1200. | 9/10 | San pham dung, gia hop le sau khi ETL loc du lieu |
| Garbage Data (`garbage_data.csv`) | Based on my data, the best choice is Nuclear Reactor at $999999. | 1/10 | Gia tri bat thuong lam sai ket qua goi y |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Khi agent chay tren `garbage_data.csv`, no tra ra ket qua hoan toan sai lech do co bon van de chat luong du lieu trong bo du lieu nay.

**Gia tri bat thuong (nguyen nhan chinh):** Ban ghi "Nuclear Reactor" co gia $999,999 — mot gia tri khong thuc te, lam cho logic `idxmax()` cua agent luon chon san pham nay. Vi agent chon san pham electronics co gia cao nhat, gia tri bat thuong nay luon thang, ghi de len cac san pham thuc su co gia tri nhu Laptop $1,200.

**ID trung lap:** ID so `1` xuat hien hai lan (Laptop va Banana), gay ra tinh trang nhap nho trong cac pipeline phuc tap hon. Trong bai nay, no tao ra ban ghi thua lam sai lech ket qua tong hop.

**Sai kieu du lieu:** Ban ghi "Broken Chair" co truong price la chuoi `"ten dollars"` thay vi so. Khi pandas goi `idxmax()` tren cot co kieu du lieu hon hop, no co the nem ngoai le hoac ep kieu ngam, dan den hanh vi khong the du doan.

**Gia tri null:** Ban ghi "Ghost Item" co `None` cho ca `id` lan `category`, va price bang `0`. Category null khien bo loc chuoi cua agent (`str.lower() == 'electronics'`) bi loi am, lam cho bo du lieu tro nen khong dang tin cay.

Tom lai, khong co van de nao trong so nay vuot qua duoc buoc `validate()` cua ETL pipeline. Thi nghiem cho thay mot AI agent chi chinh xac tuong duong voi du lieu no su dung — mot prompt tot khong the bu dap cho du lieu bi loi.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** Dong y hoan toan.

Du prompt co chinh xac va ky loi den dau, ket qua cua agent van bi gioi han boi chat luong cua nguon du lieu. Trong thi nghiem nay, cung mot logic agent va cung mot cau hoi nhung cho ra ket qua dung voi du lieu sach va ket qua sai nghiem trong voi du lieu bi loi. Vi vay, kiem tra chat luong du lieu thong qua ETL pipeline la dieu kien tien quyet de xay dung cac he thong AI dang tin cay, khong phai buoc tuy chon.
