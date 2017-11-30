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


