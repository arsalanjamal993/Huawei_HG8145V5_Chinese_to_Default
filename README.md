<h1 align="center">Huawei HG8145V5 Unlock & Wi-Fi Fix Guide</h1>

<p align="center">
A professional step-by-step guide to unlock the Huawei HG8145V5 router, remove Chinese/ISP restrictions, switch the interface to English, and disable Wi-Fi MAC filtering.<br/>
Compatible with <strong>Windows</strong> and <strong>Linux</strong> systems.
</p>

<p align="center">
  <a href="#"><img src="https://img.shields.io/badge/License-Personal%20Use-blue.svg" alt="License"></a>
  <a href="#"><img src="https://img.shields.io/badge/Device-Huawei%20HG8145V5-green.svg" alt="Device"></a>
  <a href="#"><img src="https://img.shields.io/badge/Platform-Windows%20%7C%20Linux-orange.svg" alt="Platform"></a>
</p>

<hr/>

<h2>Project Overview</h2>

<ul>
  <li>Remove ISP/China Telecom restrictions from Huawei HG8145V5 routers</li>
  <li>Switch router interface to <strong>Global (English)</strong></li>
  <li>Disable Wi-Fi MAC filtering for all devices</li>
  <li>Step-by-step instructions for <strong>Windows and Linux</strong></li>
  <li>Backup instructions for safety</li>
</ul>

<hr/>

<h2>Prerequisites</h2>

<ul>
  <li>Huawei HG8145V5 router</li>
  <li>Laptop or PC running <strong>Windows</strong> or <strong>Linux</strong></li>
  <li>Telnet client installed: 
    <ul>
      <li>Windows: <strong>Windows Terminal</strong> (<a href="https://apps.microsoft.com/detail/9n0dx20hk701?ocid=webpdpshare" target="_blank">Download Link</a>)</li>
      <li>Linux: use <code>telnet</code> via terminal (<code>sudo apt install telnet</code> / <code>sudo dnf install telnet</code>)</li>
    </ul>
  </li>
  <li>LAN cable (optional: Wi-Fi connection)</li>
</ul>

<hr/>

<h2>Steps</h2>

<h3>Step 1: Connect to Router</h3>

<pre><code>
# Windows
telnet 192.168.100.1

# Linux
telnet 192.168.100.1
</code></pre>

> Connect using LAN (recommended) or Wi-Fi.

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

> Wait ~2 minutes for router to restart.

<h3>Step 6: Disable Wi-Fi MAC Filter</h3>

<pre><code>
1. Open browser: http://192.168.100.1
2. Login:
   Username: telecomadmin
   Password: admintelecom
3. Navigate: Security → WLAN MAC Filter
4. Uncheck "Enable WLAN MAC Filter" and click Apply
</code></pre>

<hr/>

<h2>Expected Results</h2>

<ul>
  <li>Router interface in English</li>
  <li>Wi-Fi open for all devices</li>
  <li>MAC filtering disabled</li>
  <li>Router fully functional</li>
</ul>

<hr/>

<h2>Safety Notes</h2>

<ul>
  <li>Follow steps exactly</li>
  <li>Always back up configuration files before making changes</li>
  <li>Guide intended for educational and personal use</li>
  <li>Users are responsible for any device modifications</li>
</ul>

<hr/>

<h2>License</h2>
<p>This guide is intended for personal and educational use only.</p>

<hr/>

<h2>Author</h2>
<p>Developed by <strong>Arsalan Jamal</strong> — focusing on practical, cross-platform networking solutions.</p>
