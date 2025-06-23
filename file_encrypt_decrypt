import cryptography.fernet
"import os"
import tkinter as tk
from tkinter import filedialog, messagebox

def generate_key():
        key = cryptography.fernet.Fernet.generate_key()
        with open("secret.key", "wb") as key_file:
            key_file.write(key)
        messagebox.showinfo("Key Generated", "New key generated and saved as secret.key")

def load_key():
        """Loads the encryption key from the 'secret.key' file."""
        try:
            with open("secret.key", "rb") as key_file:
                return key_file.read()
        except FileNotFoundError:
            messagebox.showerror("Error", "'secret.key' not found. Please generate a key first.")
            return None

def encrypt_file():
        file_path = filedialog.askopenfilename()
        if file_path:
            key = load_key()
            if key:
                f = cryptography.fernet.Fernet(key)
                try:
                    with open(file_path, "rb") as file:
                        file_data = file.read()
                except FileNotFoundError:
                    messagebox.showerror("Error", f"File not found at '{file_path}'")
                    return

                encrypted_data = f.encrypt(file_data)
                encrypted_file_path = file_path + ".encrypted"
                with open(encrypted_file_path, "wb") as encrypted_file:
                    encrypted_file.write(encrypted_data)
                messagebox.showinfo("Encryption Successful", f"File '{file_path}' encrypted and saved as '{encrypted_file_path}'")

def decrypt_file():
        encrypted_file_path = filedialog.askopenfilename()
        if encrypted_file_path:
            key = load_key()
            if key:
                f = cryptography.fernet.Fernet(key)
                try:
                    with open(encrypted_file_path, "rb") as encrypted_file:
                        encrypted_data = encrypted_file.read()
                except FileNotFoundError:
                    messagebox.showerror("Error", f"File not found at '{encrypted_file_path}'")
                    return

                try:
                    decrypted_data = f.decrypt(encrypted_data)
                    original_file_path_base = encrypted_file_path.replace(".encrypted", "")
                    with open(original_file_path_base + ".decrypted", "wb") as decrypted_file:
                        decrypted_file.write(decrypted_data)
                    messagebox.showinfo("Decryption Successful", f"File '{encrypted_file_path}' decrypted and saved as '{original_file_path_base}.decrypted'")
                except Exception as e:
                    messagebox.showerror("Decryption Failed", f"Decryption failed: {e}")


window = tk.Tk()
window.title("File Encryptor/Decryptor")
window.geometry("300x200")
window.resizable(False, False)

button_style = {'padx': 10, 'pady': 5, 'width': 20}

generate_button = tk.Button(window, text="Generate Key", command=generate_key, **button_style)
generate_button.pack(pady=5)

encrypt_button = tk.Button(window, text="Encrypt File", command=encrypt_file, **button_style)
encrypt_button.pack(pady=5)

decrypt_button = tk.Button(window, text="Decrypt File", command=decrypt_file, **button_style)
decrypt_button.pack(pady=5)

exit_button = tk.Button(window, text="Exit", command=window.quit, **button_style)
exit_button.pack(pady=5)

window.mainloop()
