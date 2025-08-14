# Linux Task-Based Assignment

## 1 - Use `cat /etc/passwd` and identify the different fields in one of the entries. Extract your own user's info and explain.
User info explained:

- sherif → username
- x → password placeholder (actual password is in /etc/shadow)
- 1000 → user ID (UID)
- 1000 → group ID (GID)
- sherif,,, → user’s comment
- /home/sherif → home directory
- /bin/bash → default shell

**Screenshot:**  
![Task 1](assets/1.PNG)  

---

## 2 - Explain the difference between the `cat` and `more` commands.
- `cat` → displays entire file content at once.
- `more` → displays file page by page; useful for large files.

**Screenshot:**  
![Task 2](assets/2.1.PNG)  
![Task 2](assets/2.2.PNG)  

---

## 3 - Explain the difference between the rm and rmdir commands.
- `rm` → removes files or directories (use `-r` for non-empty directories).  
- `rmdir` → removes only empty directories.

---

## 4 - Create directory structure and try removing dir11 using `rmdir` / `rm -r`
**Screenshot:**  
![Task 4](assets/4 tree.PNG)  
![Task 4](assets/4.1.PNG)  

**Explanation:**  
`rmdir` failed because `dir11` is not empty. Using `rm -r dir11` removes it recursively.

---

## 5 - Remove dir12 using `rmdir -p`
**Screenshot:**  
![Task 5](assets/5.PNG)  

**Explanation:**  
`rmdir -p` removes the directory and its parent if empty, simplifying hierarchy cleanup.

---

## 6 - Copy `/etc/passwd` to home and rename to mypassword
**Screenshot:**  
![Task 6](assets/6.PNG)  

---

## 7 - Rename mypassword to oldpasswd
**Screenshot:**  
![Task 7](assets/7.PNG)  

---

## 8 - Explain the fields in `/etc/shadow`
**Screenshot:**  
![Task 8](assets/8.PNG)  

**Explanation of fields:**

1. **Username** → `sherif`  
2. **Encrypted password** → `$y$j9T$l6odOyoHB3mXebTOdCL2F1$Xi2...`  
3. **Last password change** → `20273` (days since epoch)  
4. **Minimum password age** → `0` (days before user can change password)  
5. **Maximum password age** → `99999` (days before password must be changed)  
6. **Password warning period** → `7` (days before expiration user is warned)  
7. **Password inactivity period** → empty (`:`) → account inactive after password expires  
8. **Account expiration date** → empty → account never expires  
9. **Reserved field** → empty

---

## 9 - List all available Unix shells
**Screenshot:**  
![Task 9](assets/9.PNG)  

---

## 10 - From `/usr/bin`, list 4 ways to go back to home
**Screenshot:**  
![Task 10](assets/10.PNG)  

---

## 11 - Display the first 4 lines of `/etc/passwd`
**Screenshot:**  
![Task 11](assets/11.PNG)  

---

## 12 - Display the last 7 lines of `/etc/passwd`
**Screenshot:**  
![Task 12](assets/12.PNG)  

---

## 13 - Display the users who are currently logged in
**Screenshot:**  
![Task 13](assets/13.PNG)  

---

## 14 - Display the number of user accounts in the system
**Screenshot:**  
![Task 14](assets/14.PNG)  

---

## 15 - Create user islam
**Screenshot:**  
![Task 15](assets/15.PNG)  

---

## 16 - Create user baduser
**Screenshot:**  
![Task 16](assets/16.PNG)  

---

## 17 - Create supplementary group pgroup
**Screenshot:**  
![Task 17](assets/17.PNG)  

---

## 18 - Create supplementary group badgroup
**Screenshot:**  
![Task 18](assets/18.PNG)  

---

## 19 - Add islam to pgroup as secondary group
**Screenshot:**  
![Task 19](assets/19.PNG)  

---

## 20 - Change islam’s password to password
**Screenshot:**  
![Task 20](assets/20.PNG)  

---

## 21 - Set islam’s password to expire after 30 days
**Screenshot:**  
![Task 21](assets/21.PNG)  

---

## 22 - Lock the baduser account
**Screenshot:**  
![Task 22](assets/22.PNG)  

---

## 23 - Delete the baduser account
**Screenshot:**  
![Task 23](assets/23.PNG)  

---

## 24 - Delete the badgroup supplementary group
**Screenshot:**  
![Task 24](assets/24.PNG)  

---

## 25 - Create folder myteam and change permissions
**Screenshot:**  
![Task 25](assets/25.PNG)  

**Explanation:**  
Permissions changed to read-only for owner (`chmod 400 myteam`).

---

## 26 - Log in as another user and try to cd into myteam
**Screenshot:**  
![Task 26](assets/26.PNG)  

**Explanation:**  
Other users cannot access folder because of restrictive permissions.

---

## 27 - Minimum permissions for file/directory operations 

**Explanation:**  
- Copy directory → read + execute  
- Copy file → read  
- Delete file → write + execute on parent dir  
- Change to directory → execute  
- List contents → read + execute  
- View file content → read  
- Modify file → write  

---

## 28 - Create file with 444 permissions and test
**Screenshot:**  
![Task 28](assets/28.1.PNG)  

**Explanation:**  
Cannot edit file (read-only), but can delete if parent directory allows write.

---

## 29 - Difference between x permission for file vs directory

**Explanation:**  
- File → allows execution if it's script
- Directory → allows entering/traversing  "cd into Directory"

---

## 30 - Configure a static IP address
**Screenshot:**  
![Task 30](assets/30.1.PNG)  
![Task 30](assets/30.2.PNG)  

---

## 31 - Test network connectivity using ping, traceroute, nslookup
**Screenshot:**  
![ping](assets/31.1.PNG)  
![traceroute](assets/31.2.PNG)  
![nslookup](assets/31.3.PNG)  

---

## 32 - Firewall setup, enable, and allow port

**Explanation:**  
A firewall is a security tool that controls incoming and outgoing network traffic based on defined rules. It helps protect your system from unauthorized access while allowing authorized connections.

### On Ubuntu (UFW)
```bash
# Enable the firewall
sudo ufw enable

# Allow HTTP port 80
sudo ufw allow 80/tcp

# Check firewall status
sudo ufw status verbose
```
### On RHEL/CentOS (firewalld)
```bash
# Enable and start the firewall service
sudo systemctl enable firewalld
sudo systemctl start firewalld

# Allow HTTP port 80 permanently
sudo firewall-cmd --permanent --add-port=80/tcp

# Reload firewall to apply changes
sudo firewall-cmd --reload

# Check status and active rules
sudo firewall-cmd --list-all
```

---

## 33 - Run `sleep 50` in background, send it to background, find PID, and kill

**Screenshot:**  
![task33](assets/33.PNG)

**Explanation:**  
- `sleep 50 &` → Start the command in the background.  
- `Ctrl+Z` then `bg` → Suspend a running job and move it to the background.  
- `jobs` → List background jobs with their PIDs.  
- `kill -9 <PID>` → Forcefully terminate the process using its PID.
