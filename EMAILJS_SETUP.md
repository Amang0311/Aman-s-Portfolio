# 📧 EmailJS Setup Guide

## Cara Setup EmailJS untuk Contact Form

### Langkah 1: Daftar EmailJS Account
1. Pergi ke [https://www.emailjs.com/](https://www.emailjs.com/)
2. Klik "Sign Up" dan daftar dengan email anda
3. Pilih Free Plan (200 emails/bulan - cukup untuk portfolio)

### Langkah 2: Create Email Service
1. Selepas login, pergi ke **Email Services** (Dashboard → Email Services)
2. Klik **Add New Service**
3. Pilih email provider anda:
   - **Gmail** (Recommended - mudah setup)
   - **Outlook**
   - **Custom SMTP**
4. Ikut arahan untuk connect email anda
5. Simpan **Service ID** yang diberikan

### Langkah 3: Create Email Template
1. Pergi ke **Email Templates** (Dashboard → Email Templates)
2. Klik **Create New Template**
3. Pilih template "Blank" atau gunakan template sedia ada
4. Setup template dengan format berikut:

**Subject Line:**
```
Portfolio Contact: {{subject}}
```

**Content/Message Body:**
```
📧 New Message from Portfolio Contact Form

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

👤 Name: {{from_name}}

📧 Email: {{from_email}}

📌 Subject: {{subject}}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

💬 Message:
{{message}}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

📝 You can reply directly to this email to respond to {{from_name}}.

---
This email was sent from your portfolio contact form via EmailJS.
```

**Settings:**
- **Reply To:** `{{reply_to}}` (supaya boleh reply terus kepada sender)
- **From Name:** Your Portfolio (atau nama yang anda nak)

5. Klik **Save** dan simpan **Template ID** yang diberikan

**⚠️ PENTING:** Pastikan semua variable ini digunakan dalam template:
- `{{from_name}}` - Nama pengirim
- `{{from_email}}` - Email pengirim  
- `{{subject}}` - Subject mesej
- `{{message}}` - Isi mesej
- `{{reply_to}}` - Reply-to email (dalam Settings)

### Langkah 4: Get Your Public Key
1. Pergi ke **Account** → **General**
2. Cari **Public Key** di bahagian "API Keys"
3. Copy Public Key anda

### Langkah 5: Update Code
Buka `script.js` dan update 3 nilai ini:

1. **Public Key** (Line ~122):
   ```javascript
   emailjs.init("YOUR_PUBLIC_KEY"); // Replace dengan Public Key anda
   ```

2. **Service ID** (Line ~145):
   ```javascript
   const serviceID = 'YOUR_SERVICE_ID'; // Replace dengan Service ID anda
   ```

3. **Template ID** (Line ~146):
   ```javascript
   const templateID = 'YOUR_TEMPLATE_ID'; // Replace dengan Template ID anda
   ```

### Contoh Setup:
```javascript
emailjs.init("abcdefghijklmnop"); // Public Key
const serviceID = 'service_xyz123'; // Service ID
const templateID = 'template_abc456'; // Template ID
```

### Testing
1. Buka portfolio website anda
2. Pergi ke Contact section
3. Isi form dan submit
4. Check email anda untuk mesej baru!

### Troubleshooting

**Jika email tidak sampai:**
- Pastikan Public Key, Service ID, dan Template ID betul
- Check EmailJS Dashboard untuk error logs
- Pastikan email service sudah connected dengan betul
- Check spam/junk folder

**Free Plan Limits:**
- 200 emails per month
- Upgrade jika perlu lebih

### Security Note
⚠️ **PENTING**: Public Key akan terdedah dalam code. Ini selamat untuk EmailJS kerana:
- Public Key hanya untuk limit rate limiting
- Tidak boleh access account tanpa Private Key
- EmailJS sudah secure untuk public usage

---

**Tips:**
- Test dengan email sendiri dulu sebelum deploy
- Setup email notifications di EmailJS dashboard
- Monitor usage di dashboard untuk pastikan tidak exceed limit

Selesai! Contact form anda sekarang akan hantar email terus ke `amanlegend031111@gmail.com` 🎉

