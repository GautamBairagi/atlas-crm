# Port Forwarding Guide - Atlas CRM

## ✅ Server Status
- **Server Running:** Port 8000
- **Local IP:** 192.168.1.6
- **Status:** Ready for access

---

## 🌐 Access Methods

### 1. Local Access (Same Computer)
```
http://localhost:8000
http://127.0.0.1:8000
```

### 2. Network Access (Same WiFi/LAN)
```
http://192.168.1.6:8000
```
**Note:** दूसरे device को same WiFi network पर होना चाहिए

### 3. External Access (Internet से)

#### Option A: Router Port Forwarding
1. Router admin panel में जाएं (usually `192.168.1.1`)
2. Port Forwarding section में जाएं
3. Add new rule:
   - **External Port:** 8000
   - **Internal IP:** 192.168.1.6
   - **Internal Port:** 8000
   - **Protocol:** TCP
4. Save करें
5. Public IP check करें: `whatismyip.com`
6. Access: `http://YOUR_PUBLIC_IP:8000`

#### Option B: ngrok (Easiest - No Router Config)
```bash
# Install ngrok (if not installed)
# Download from: https://ngrok.com/download

# Run ngrok tunnel
ngrok http 8000

# You'll get a URL like: https://abc123.ngrok.io
# Share this URL with others
```

#### Option C: Cloudflare Tunnel (Free & Secure)
```bash
# Install cloudflared
# Run tunnel
cloudflared tunnel --url http://localhost:8000
```

---

## 🔥 Firewall Settings

### Windows Firewall
Firewall rule add करने के लिए **Administrator** के रूप में run करें:

```powershell
netsh advfirewall firewall add rule name="Django Server Port 8000" dir=in action=allow protocol=TCP localport=8000
```

या manually:
1. Windows Defender Firewall खोलें
2. "Advanced settings" जाएं
3. "Inbound Rules" → "New Rule"
4. Port → TCP → 8000 → Allow connection
5. Finish

---

## 📱 Mobile/Other Device से Access

### Same WiFi पर:
1. Mobile/device को same WiFi से connect करें
2. Browser में open करें: `http://192.168.1.6:8000`
3. Login करें

### Internet से (ngrok के साथ):
1. ngrok run करें: `ngrok http 8000`
2. मिले URL को share करें (जैसे: `https://abc123.ngrok.io`)
3. दूसरा user उस URL पर access कर सकता है

---

## 🔐 Login Credentials

### Super Admin
- Email: `superadmin@atlas.com`
- Password: `admin123`

### Admin
- Email: `admin@atlas.com`
- Password: `admin123`

### Seller
- Email: `seller@atlas.com`
- Password: `seller123`

### Call Center Agent
- Email: `callcenter@atlas.com`
- Password: `callcenter123`

### Manager
- Email: `manager@atlas.com`
- Password: `manager123`

### Stock Keeper
- Email: `stockkeeper@atlas.com`
- Password: `stock123`

### Packaging Agent
- Email: `packaging@atlas.com`
- Password: `package123`

### Delivery Agent
- Email: `delivery@atlas.com`
- Password: `delivery123`

---

## ⚠️ Important Notes

1. **Security:** Production में DEBUG=False रखें
2. **HTTPS:** External access के लिए HTTPS use करें
3. **Firewall:** Router firewall भी check करें
4. **Static IP:** Router में device को static IP assign करें

---

## 🚀 Quick Start (ngrok)

```bash
# Terminal 1: Django Server (already running)
# Server is running on port 8000

# Terminal 2: ngrok tunnel
ngrok http 8000

# Copy the ngrok URL (e.g., https://abc123.ngrok.io)
# Share with others - they can access immediately!
```

---

## 📞 Troubleshooting

### Connection Refused?
- Check firewall settings
- Verify server is running: `netstat -ano | findstr :8000`
- Check IP address: `ipconfig`

### Can't Access from Other Device?
- Ensure same WiFi network
- Check firewall on both devices
- Try disabling Windows Firewall temporarily to test

### ngrok Not Working?
- Check ngrok is installed: `ngrok version`
- Verify port 8000 is accessible locally
- Check ngrok account is authenticated

---

**Server is ready! Share the URL with others to access.** 🎉
