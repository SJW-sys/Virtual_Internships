# File Permission Correction
## Task
**Important -** Please note that these task can have slight variation such as usernames, filepaths, files, etc

> After conducting a security audit within the Stratos DC, the Nautilus security team discovered misconfigured permissions on critical files. To address this, corrective actions are being taken by the production support team. Specifically, the file named /etc/resolv.conf on Nautilus App 3 server requires adjustments to its Access Control Lists (ACLs) as follows:
>
> 1. The file's user owner and group owner should be set to root.
> 2. Others should possess read only permissions on the file.
> 3. User siva must not have any permissions on the file.
> 4. User ryan should be granted read only permission on the file.

## Solution
**Important -** While there are more exact commands to make this as quick as possible, I will be as expressive as possible to show a step by step guide with optional verification steps.

1. Connect to target server, login details found in the 'company' wiki. (In a real world this would be in a vault,or you be accessing via your own assigned identity, not a shared identity.)

    ssh banner@stapp03

2.  check files current full permissions (acl and basic file permissions)

    getfacl /etc/resolv.conf

3. adjust file owners (user and group)

    sudo chown root:root /etc/resolv.conf

4. If you need to set others to allow read only

    sudo chmod o-wx /etc/resolv.conf

5. deny siva any access to file

    sudo setfacl -m u:siva:--- /etc/resolv.conf

6. allow ryan read only to file

    sudo setfacl -m u:ryan:r-- /etc/resolv.conf

7. verify all permissions

    getfacl /etc/resolv.conf


## My Comments
NA


