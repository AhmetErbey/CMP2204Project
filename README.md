# CMP2204Project
Computer Networks Python Project
# 🔐 Peer-to-Peer Secure Chat Application

This project is a peer-to-peer chat application developed for the CMP2204 course. It supports both secure (DES-encrypted) and unsecure text messaging between users on the same network.

## 📦 Project Structure

```
.
├── chat_initiator.py         # User interface to send messages
├── chat_responder.py         # Receives and decrypts messages
├── service_announcer.py      # Broadcasts username across network
├── peer_discovery.py         # Listens for users on the network
├── users.json                # Stores discovered users
├── history.txt               # Stores sent messages
├── chatlog.txt               # Stores received messages
└── README.md                 # Project documentation
```

## ⚙️ Requirements

- Python 3.10+
- `pyDes` library  
  Install via:
  ```bash
  pip install -r requirements.txt
  ```

## 🧠 Features

- ✅ Peer discovery using UDP broadcast
- ✅ Chat with selected peers using TCP
- ✅ Diffie-Hellman key exchange for secure chats
- ✅ DES encryption with base64 encoding
- ✅ Message logging (history & received logs)
- ✅ Supports both secure and unsecure messaging
- ✅ Wireshark validated secure message exchange

## 🚀 How to Run

**Step 1: Start these on both machines**
```bash
python service_announcer.py
python peer_discovery.py
```

**Step 2: On the receiver machine**
```bash
python chat_responder.py
```

**Step 3: On the sender machine**
```bash
python chat_initiator.py
```

## 🔐 Encryption

Secure messages are exchanged via:

1. Diffie-Hellman Key Exchange
2. DES Encryption (ECB + PKCS5)
3. Base64 Encoding

## 👤 Kullanıcı Senaryoları

### Senaryo 1: Ahmet sends secure message to Zeynep
1. Both launch announcer and discovery.
2. Zeynep runs chat_responder.py
3. Ahmet selects Zeynep from list and chooses secure chat.
4. DH exchange → DES encryption → base64 → sent.
5. Message decrypted and logged.

## 🛠️ Troubleshooting & Common Errors

| Issue | Cause | Solution |
|------|-------|----------|
| Peer not appearing | Broadcast IP mismatch | Check BROADCAST_IP based on subnet |
| Message fails | Antivirus blocking socket | Allow Python in Windows Firewall |
| Decryption fails | Wrong DH key | Ensure same p, g and proper key input |

## 🧪 Wireshark Proofs

- `secure_sent1.0.jpg`
- `received_secure2.0.jpg`
- `unsecure.jpg`

## 📁 Commands Summary

```bash
# Start network services
python service_announcer.py
python peer_discovery.py

# Start chat interfaces
python chat_responder.py
python chat_initiator.py

# Optional: clear logs
del history.txt chatlog.txt users.json
```

## 👥 Team

- Ahmet [Your Name]
- [Friend 1]
- [Friend 2]

## 📄 License

For educational purposes only. Do not distribute for commercial use.
