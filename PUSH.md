# ขึ้น GitHub

ผมสร้าง repo ให้จากเซสชันนี้ไม่ได้ (GitHub ถูกล็อกไว้เฉพาะ repo ที่ตั้งค่าไว้ล่วงหน้า)
แต่ไฟล์ทั้งหมดพร้อม push แล้ว — รันสามคำสั่งนี้บนเครื่องคุณ

```bash
# 1. สร้าง repo เปล่าชื่อ tbt-landing-style ที่ github.com/new (เลือก Public, ไม่ต้องติ๊ก README)

# 2. ในโฟลเดอร์นี้
git init -b main
git add -A
git commit -m "Add tbt-landing-style skill"

# 3. แทน <user> ด้วยชื่อ GitHub ของคุณ
git remote add origin https://github.com/<user>/tbt-landing-style.git
git push -u origin main
```

ถ้ามี `gh` ติดตั้งอยู่ ย่อเหลือคำสั่งเดียวได้

```bash
gh repo create tbt-landing-style --public --source=. --push
```
