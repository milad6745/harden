البته! این هم فایل کامل `README.md` آماده برای پروژه شما:

```markdown
# Ansible Inventory and Usage Guide

این پروژه شامل فایل `inventory` برای مدیریت سرورها و توضیحات نحوه افزودن هاست جدید و اجرای playbookها با انسیبل است.

---

## ساختار فایل Inventory

فایل `inventory` لیست سرورها و تنظیمات اتصال به آنها را مشخص می‌کند.

### نمونه فایل inventory:

```

localhost ansible\_connection=local

webserver1 ansible\_host=192.168.1.50 ansible\_user=milad

dbserver ansible\_host=192.168.1.51 ansible\_user=milad

```

- `localhost`: اجرای دستورات روی خود ماشین لوکال.
- `webserver1` و `dbserver`: نام مستعار برای هر سرور.
- `ansible_host`: آدرس IP یا نام دامنه سرور.
- `ansible_user`: نام کاربری برای اتصال SSH.

---

## اضافه کردن هاست جدید

برای افزودن یک سرور جدید به `inventory`:

1. خط جدیدی با فرمت زیر اضافه کنید:

```

\<host\_alias> ansible\_host=\<ip\_or\_hostname> ansible\_user=<username>

```

2. مثال:

```

appserver ansible\_host=10.0.0.25 ansible\_user=milad

```

3. اگر پورت SSH غیر پیش‌فرض است، می‌توانید آن را با پارامتر `ansible_port` مشخص کنید:

```

webserver2 ansible\_host=192.168.1.52 ansible\_user=milad ansible\_port=2222

````

---

## نکات مهم

- اطمینان حاصل کنید کلید SSH کاربر `ansible_user` روی سرور مقصد اضافه شده باشد تا اتصال بدون پسورد امکان‌پذیر باشد.
- برای اجرای playbook روی همه سرورها:

```bash
ansible-playbook -i inventory your_playbook.yaml
````

* اجرای playbook فقط روی یک سرور خاص:

  ```bash
  ansible-playbook -i inventory your_playbook.yaml --limit webserver1
  ```

---

## نمونه اجرا

```bash
ansible-playbook -i inventory harden.yaml
```

---

## سوال یا مشکل داشتید، لطفا گزارش دهید.

```
```
