# OSCP Exam DNS fix for VPN Connection
It is required to add the Google DNS information into the `resolvconf` file in Kali Linux VM, for the OSCP exam to be successfully connected to the exam lab environment. The below steps will show you how to configure this with **resolvconf** tool. 

This will reduce huge overhead during the exam and may avoid the VPN and Network issues. Make sure to test this prior to the exam and ensure your network is working as intended. 

Good Luck and wish you all the best with your OSCP exam. 


---


#### **Step 1:** Install *resolvconf* tool
```bash
sudo apt install resolvconf
```


#### **Step 2:** Enable *resolvconf* service
```bash
sudo systemctl enable resolvconf.service
```


#### **Step 3:** Start *resolvconf* service
```bash
sudo systemctl start resolvconf.service
```


#### **Step 4:** Check Status of *resolvconf* service
```bash
sudo systemctl status resolvconf.service
```


#### **Step 5:** Add Google DNS into *base* file
```bash
sudo nano /etc/resolvconf/resolv.conf.d/base

# Add these Google DNS nameserver info:
nameserver 8.8.8.8
nameserver 8.8.4.4
```


#### **Step 6:** Add Google DNS into *interfaces* file
```bash
sudo nano /etc/network/interfaces

# Add these Google DNS nameserver info:
dns-nameservers 8.8.8.8 8.8.4.4
```


#### **Step 7:** Restart *networking* service
```bash
sudo systemctl restart networking
```


#### **Step 8:** Restart *resolvconf* service
```bash
sudo systemctl restart resolvconf.service
```


#### **Step 9:** Confirm the added Google DNS info
```bash
cat /etc/resolv.conf
```

![Screen Shot 2022-09-25 at 6 00 17 pm](https://user-images.githubusercontent.com/6763366/192138917-e026403e-b977-4bff-94de-019c19a98c5d.png)


---


