# PowerToken
This PowerShell module weaponizes various user privileges that are assigned to a user token (whoami /priv), which provides the opportunity for privilege escalation.

### Cmdlets:
* **Get-UserPrivileges** - parses the output from *whoami /priv* into a PowerShell object
* **Enable-UserPrivileges** - enables all privileges in an disabled state for the specified user token via a process handle
* **Abuse-RestoreAndBackupPrivileges** - sets full control on the specified directory for the current user which allows access to all file system objects in said directory
* **Copy-FileBackupPrivilege** - uses the CreateFile Win32 API function with FILE_FLAG_BACKUP_SEMANTICS to allow the current user with the sebackupprivilege to read the contents of files that they normally wouldn't have access to
* **Create-ShadowCopyBackupPrivilege** - create a shadow copy of the specified drive or file system object using diskshadow or wbadmin (restore, copy or overwrite file permission with the following cmdlets above)
* **Delete-ShadowCopy** - delete the shadow copy you made via the alias specified during creation 
* **Restore-FileRestorePrivilege** - uses the CreateFile Win32 API function with FILE_FLAG_BACKUP_SEMANTICS to copy file contents and WriteFile Win32 API function to write the copied contents to a new location



### Based on the research and information below:
* https://medium.com/palantir/windows-privilege-abuse-auditing-detection-and-defense-3078a403d74e
* https://foxglovesecurity.com/2017/08/25/abusing-token-privileges-for-windows-local-privilege-escalation/
* https://hackinparis.com/data/slides/2019/talks/HIP2019-Andrea_Pierini-Whoami_Priv_Show_Me_Your_Privileges_And_I_Will_Lead_You_To_System.pdf
* https://decoder.cloud/2018/02/12/the-power-of-backup-operatos/
* https://book.hacktricks.xyz/windows/windows-local-privilege-escalation#token-manipulation
* https://github.com/hatRiot/token-priv/blob/master/abusing_token_eop_1.0.txt
* https://ired.team/offensive-security-experiments/active-directory-kerberos-abuse/privileged-accounts-and-token-privileges
* https://www.exploit-db.com/exploits/42556
* https://labs.portcullis.co.uk/blog/se-and-you/
* https://m0chan.github.io/2019/07/30/Windows-Notes-and-Cheatsheet.html#-sebackupprivlege---dump-ntdsdit
* https://heynowyouseeme.blogspot.com/2019/08/the-useage-of-9-permissions-for-windows.html
