# OTP
Build an MFA integrating with Google Authenticator in few lines of Python code

!pip install pyotp qrcode

import pyotp  
import time  

totp = pyotp.TOTP(pyotp.random_base32())  
otp = totp.now()

otp_uri = totp.provisioning_uri(name='justin@google.com', issuer_name='Justin App')

import qrcode  
qr = qrcode.make(otp_uri)  
qr.save("otp_qrcode.jpg")

from IPython.display import Image  
Image(filename = "otp_qrcode.jpg", width=500, height=500)  
![image](https://github.com/user-attachments/assets/6eff5bc1-75e4-4041-b45a-2f8eb8133e65)


## Check Google Authenticator
When you check Google Authenticator, you should see the OTP will match below

print("Current OTP:", totp.now())
