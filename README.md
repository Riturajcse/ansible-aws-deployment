# ansible-aws-deployment

This is a basic example to learn deploying applications on aws ec2 instance using anisble

# prerequisite
- python 2.6 =>
- boto module
- aws account with aws_access_key + aws_secret_key
- aws ec2.py file under /etc/ansible/hosts and a configured ansible.cfg file
- aws keypair to connect to aws (uploaded to aws as well as located somewhere where your ssh config can find it and use it).

# creating ec2 instance

```
ansible-playbook create.yaml
```
* Output

```
PLAY [aws provison play] ************************************************************************************************************************************************************************************

TASK [Gathering Facts] **************************************************************************************************************************************************************************************
ok: [localhost]

TASK [Launch ec2 instance] **********************************************************************************************************************************************************************************
changed: [localhost]

TASK [Add new instance to host group] ***********************************************************************************************************************************************************************
changed: [localhost] => XXXX

TASK [Wait for SSH to come up] ******************************************************************************************************************************************************************************
ok: [localhost] => XXXX

PLAY RECAP **************************************************************************************************************************************************************************************************
localhost                  : ok=4    changed=2    unreachable=0    failed=0
```

# add id-address of newly created instance in Hosts file

# running script on the newly created instance to deploy your application

```
ansible-playbook -i Hosts start-application.yaml
```
* Output 

```
PLAY [Installing sample node application] *******************************************************************************************************************************************************************

TASK [Gathering Facts] **************************************************************************************************************************************************************************************
The authenticity of host '54.191.18.28 (54.191.18.28)' can't be established.
ECDSA key fingerprint is 00:7a:03:4d:48:8e:8xx:xx:xx:xx:xx:xx.
Are you sure you want to continue connecting (yes/no)? yes
ok: [54.191.18.28]

TASK [Transfer the script now!] *****************************************************************************************************************************************************************************
changed: [54.191.18.28]

PLAY RECAP **************************************************************************************************************************************************************************************************
54.191.18.28               : ok=2    changed=1    unreachable=0    failed=0 
```

# terminate aws instance 
```
ansible-playbook terminate.yaml
```
* Output
```
PLAY [Delete EC2 instance] **********************************************************************************************************************************************************************************

TASK [Terminate instance] ***********************************************************************************************************************************************************************************
changed: [localhost -> localhost]

PLAY RECAP **************************************************************************************************************************************************************************************************
localhost                  : ok=1    changed=1    unreachable=0    failed=0
```


