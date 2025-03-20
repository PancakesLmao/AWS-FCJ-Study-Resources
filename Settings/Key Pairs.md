A set of credentials that you use to prove your identity when connecting to an Amazon EC2 Instance
A key pair consists of 
- A public key that AWS stores
- A private key file that you store
# Connecting to your instance with your key pair
- Window AMIs use the private key to obtain the administrator password that you need to log in to your instance through Remote Desktop Protocol (RDP)
- Linux AMIs use the private key to use Secure Shell (SSH) to securely connect to your instance