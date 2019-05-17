CVE-2019-5786 and CVE-2019-0808 Chrome 72.0.3626.119 stable Windows 7 x86 exploit chain. 

This exploit uses site-isolation to brute-force CVE-2019-5786. `host1_wrapper/iframe.html` is the wrapper script that loads the exploit  repeatedly into an iframe. The actual chain resides in the `host2_single_run` directory. The sandbox escape exploit for CVE-2019-0808 is in the file `host2_single_run/shellcode.js`, converted from its .dll form via [sRDI][https://github.com/monoxgas/sRDI] and msfvenom.

* serve the contents of the `host1_wrapper` directory on one site and the contents of `host2_single_run` on another
* change line 14 in `host1_wrapper/iframe.html` to the URL of `host2_single_run/exploit.html`
* navigate to iframe.html