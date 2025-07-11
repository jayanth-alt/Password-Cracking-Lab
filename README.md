# Password-Cracking-Lab
 A practical lab to demonstrate password cracking using John the Ripper, Hashcat, and real-world wordlists to highlight the importance of strong passwords.
#  Create Hashed Passwords
echo -n "password123" | openssl passwd -6 -stdin
echo -n "qwerty" | openssl passwd -6 -stdin

#  Save Hashes to File
nano hashes.txt

#  Unzip rockyou.txt Wordlist
gunzip /usr/share/wordlists/rockyou.txt.gz

# Crack with John the Ripper
john hashes.txt
john --wordlist=/usr/share/wordlists/rockyou.txt hashes.txt
john --show hashes.txt

#  Crack with Hashcat (SHA-512 = 1800)
hashcat -m 1800 -a 0 -o cracked.txt hashes.txt /usr/share/wordlists/rockyou.txt
cat cracked.txt

# Identify Hash Type
hashid [your_hash]

# Specify Format in John (optional)
john --format=sha512crypt hashes.txt

# Check GPU Support in Hashcat
hashcat -I
