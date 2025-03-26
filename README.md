# Security in IoT

## 📌 Project Overview
The **Security in IoT** project is designed to enhance the security of IoT devices by implementing robust authentication, access control, and data encryption techniques. IoT devices are particularly vulnerable to various cyber threats, making it essential to enforce secure communication and data protection. This project aims to provide a foundation for securing IoT ecosystems through advanced cryptographic techniques and access management.

## 📂 Project Structure
```
Security_IoT/
├── Security_in_IoT.ipynb   # Main Jupyter Notebook with implementation
├── requirements.txt        # Python dependencies
└── README.md               # Project documentation (this file)
```

## 🛠️ Features
### 1. User Authentication
- Secure login system that verifies user credentials.
- Passwords are hashed using the **bcrypt** algorithm for enhanced security.
- Prevents unauthorized access through user validation.

### 2. Access Control (Role-Based)
- Implements **Role-Based Access Control (RBAC)** for different user levels.
- Define custom permissions for various user roles (e.g., 'admin', 'user').
- Granular control over which actions users can perform (e.g., 'read', 'write').

### 3. AES Encryption
- Data is encrypted and decrypted using **AES (Advanced Encryption Standard)**.
- Uses the **PBKDF2** function for secure key derivation.
- Ensures that sensitive data remains confidential during transmission.

### 4. Admin Control
- Admin can add new users and assign permissions.
- Ability to update or remove user access dynamically.

### 5. Secure Token Generation (Optional Extension)
- JWT-based token generation for user sessions.
- Ensures stateless and secure user session management.

## 🚀 Getting Started

### 1. Clone the Repository
First, clone the repository from GitHub:
```bash
git clone https://github.com/Vikas-Attrish/Security_IOT.git
cd Security_IOT
```

### 2. Set Up the Environment
It is recommended to use a virtual environment to manage dependencies:

```bash
python -m venv venv
source venv/bin/activate  # On Windows use: venv\Scripts\activate
```

### 3. Install Dependencies
Install all required Python packages using the `requirements.txt` file:
```bash
pip install -r requirements.txt
```

### 4. Run the Jupyter Notebook
Launch the Jupyter Notebook interface and open `Security_in_IoT.ipynb`:
```bash
jupyter notebook Security_in_IoT.ipynb
```

## 🔐 Security Implementation Details

### User Authentication
- Users are authenticated by verifying their hashed passwords.
- Passwords are stored in a securely hashed format using **bcrypt**.
- Authentication checks username-password combinations for validity.

### Role-Based Access Control (RBAC)
- Users are assigned roles with specific permissions.
- Permissions are verified before granting access to resources.
- Example roles: 
  - **Admin**: Full access (read, write, manage users)
  - **User**: Limited access (read-only)

### AES Encryption Process
1. **Key Derivation**: Uses PBKDF2 for secure key generation.
2. **Encryption**: Encrypts data using AES in EAX mode.
3. **Decryption**: Decrypts and verifies data integrity using the authentication tag.

**Example Encryption Code:**
```python
from Crypto.Cipher import AES
from Crypto.Protocol.KDF import PBKDF2
import base64

def encrypt_data(data, key):
    key = PBKDF2(key, b'salt', dkLen=32)
    cipher = AES.new(key, AES.MODE_EAX)
    ciphertext, tag = cipher.encrypt_and_digest(data.encode())
    return base64.b64encode(cipher.nonce + tag + ciphertext).decode()
```

## 🧪 Usage Examples

### Example 1: Authenticate a User
```python
Enter your username: user1
Enter your password: password1
✅ Welcome, user1!
```

### Example 2: Check Permissions
```python
Enter action: write
❌ Permission denied for 'user'.
```

### Example 3: Encrypt and Decrypt Data
```python
Original Data: "Hello IoT"
Encrypted Data: "7Hd83d..."
Decrypted Data: "Hello IoT"
```

## 📊 Future Enhancements
1. **Multi-Factor Authentication (MFA):** Add an extra layer of security using OTP.
2. **Audit Logging:** Track user actions for improved monitoring and security analysis.
3. **Device Authentication:** Implement mutual authentication between IoT devices and servers.
4. **Secure APIs:** Integrate token-based authentication for API communications.
5. **Real-Time Alerts:** Notify administrators of suspicious activity.

## 🤝 Contributing
Contributions are welcome! Follow these steps to contribute:
1. Fork the repository on GitHub.
2. Create a new branch for your feature (`git checkout -b feature/new-feature`).
3. Commit your changes (`git commit -m "Add new feature"`).
4. Push your branch to GitHub (`git push origin feature/new-feature`).
5. Open a pull request for review.

## 📜 License
This project is licensed under the **MIT License**. For more details, check the [LICENSE](LICENSE) file.

## 📧 Contact
For any questions, feedback, or suggestions, open an issue on GitHub or reach out via:
- GitHub Issues: [Security in IoT](https://github.com/Vikas-Attrish/Security_IOT/issues)
- Email: Your contact information (optional)

