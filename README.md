# 🔐 File Encryptor/Decryptor (Fernet Cipher + GUI)

A simple and secure file encryption and decryption tool built with Python, using the Fernet symmetric encryption from the `cryptography` library. It features a minimal Tkinter-based GUI for ease of use.

## 📆 Features

* Generate a secure key and save it locally (`secret.key`)
* Encrypt any file using Fernet cipher (AES-based)
* Decrypt `.encrypted` files to recover the original content
* Simple and intuitive graphical interface

## 💠 Requirements

* Python 3.6+
* `cryptography` library
* Tkinter (included in standard Python distribution)

## 📦 Installation

1. **Clone this repository**

   ```bash
   git clone https://github.com/your-username/file-encryptor-decryptor.git
   cd file-encryptor-decryptor
   ```

2. **Install dependencies**

   ```bash
   pip install cryptography
   ```

## 🚀 Usage

Run the script:

```bash
python encryptor_gui.py
```

Then use the GUI to:

* **Generate Key**: Creates and saves a `secret.key` file
* **Encrypt File**: Choose a file to encrypt (creates a `.encrypted` file)
* **Decrypt File**: Choose a `.encrypted` file to decrypt (creates a `.decrypted` file)
* **Exit**: Closes the application

> ⚠️ Always keep your `secret.key` file safe. Losing it means you won’t be able to decrypt your files!

## 📁 File Structure

```
.
├── encryptor_gui.py       # Main application script
├── secret.key             # (Generated) encryption key
├── README.md              # Project documentation
└── .gitignore             # Ignored files
```

## 📟 License

This project is licensed under the [MIT License](LICENSE).

## 🙌 Acknowledgments

* [Python Cryptography](https://cryptography.io/)
* [Tkinter GUI Toolkit](https://docs.python.org/3/library/tkinter.html)
