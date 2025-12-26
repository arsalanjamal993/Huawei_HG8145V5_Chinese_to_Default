<h1 align="center">Huawei HG8145V5 Unlock & Wi-Fi Fix Guide</h1>

<p align="center">
A professional, step-by-step guide to unlock your Huawei HG8145V5 router, remove Chinese/ISP restrictions, switch the interface to English, and disable Wi-Fi MAC filtering.<br/>
Designed for clarity, safety, and beginner-friendly usage.
</p>

<p align="center">
  <a href="#"><img src="https://img.shields.io/badge/license-Personal%20Use-blue.svg" alt="License"></a>
  <a href="#"><img src="https://img.shields.io/badge/Device-Huawei%20HG8145V5-green.svg" alt="Device"></a>
  <a href="#"><img src="https://img.shields.io/badge/Platform-Windows-orange.svg" alt="Platform"></a>
</p>

<hr/>

<h2>Project Overview</h2>

<ul>
  <li>Step-by-step guide to unlock Huawei HG8145V5 routers</li>
  <li>Switch router interface to Global (English)</li>
  <li>Disable Wi-Fi MAC filtering to allow all devices</li>
  <li>Includes safety backup instructions</li>
</ul>

<hr/>

<h2>Prerequisites</h2>

<ul>
  <li>Laptop or PC running Windows</li>
  <li><strong>Windows Terminal</strong> installed (<a href="https://apps.microsoft.com/detail/9n0dx20hk701?ocid=webpdpshare" target="_blank">Download Link</a>)</li>
  <li>LAN cable (Wi-Fi connection also works)</li>
</ul>

<hr/>

<h2>Installation & Steps</h2>

<h3>Step 1: Connect to Router</h3>
<pre><code>
1. Connect LAN cable from router to laptop (optional: Wi-Fi)
2. Open Windows Terminal
3. Telnet to router: 192.168.100.1
4. Connection Type: Telnet
5. Click Open
</code></pre>

<h3>Step 2: Login</h3>
<p>Note: Password input will not be visible.</p>
<pre><code>
Login: root
Password: adminHW

Commands:
su
shell

Expected Output:
WAP(Dopra Linux) #
</code></pre>

<h3>Step 3: Backup Configuration</h3>
<pre><code>
cd /mnt/jffs2
cp hw_boardinfo hw_boardinfo.bak
cp hw_ctree.xml hw_ctree.xml.bak
</code></pre>

<h3>Step 4: Switch Router to Global (English)</h3>
<pre><code>
sed -i 's/"CHINATELECOM"/"COMMON"/g' hw_boardinfo
sed -i 's/"CHINA"/"COMMON"/g' hw_boardinfo
rm -rf hw_default_ctree.xml
cp -rf /etc/wap/hw_default_ctree.xml /mnt/jffs2/hw_default_ctree.xml
rm -rf hw_ctree.xml
</code></pre>

<h3>Step 5: Restart Router</h3>
<pre><code>
reboot
</code></pre>
<p>Wait ~2 minutes for router to restart.</p>

<h3>Step 6: Disable Wi-Fi MAC Filter</h3>
<pre><code>
1. Open browser: http://192.168.100.1
2. Login: 
   Username: telecomadmin
   Password: admintelecom
3. Navigate: Security → WLAN MAC Filter
4. Uncheck Enable WLAN MAC Filter and click Apply
</code></pre>

<hr/>

<h2>Expected Results</h2>

<ul>
  <li>Router interface displayed in English</li>
  <li>Wi-Fi accessible to all devices</li>
  <li>MAC restrictions removed</li>
  <li>Router fully functional</li>
</ul>

<hr/>

<h2>Safety Notes</h2>

<ul>
  <li>Follow steps exactly</li>
  <li>Always back up configuration files</li>
  <li>Guide intended for educational/personal use only</li>
  <li>Users are responsible for any device modifications</li>
</ul>

<hr/>

<h2>License</h2>
<p>This guide is intended for personal and educational use only.</p>

<hr/>

<h2>Author</h2>
<p>Developed by <strong>Arsalan Jamal</strong> — focusing on practical, user-friendly networking and Linux solutions.</p>
