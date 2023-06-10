
```
sudo apt install python3-pip virtualenv
mkdir -p ~/Documents/ansible/playbooks
mkdir -p ~/Documents/ansible/roles
cd ~/Documents/ansible
virtualenv -p python3 .venv
. .venv/bin/activate
cd playbooks
git clone <URL>
cd <repo_dir>
pip3 install -r requirements.txt
```

Add to /etc/sudoers (replace MY_USER w/ user that will run ansible):
```
<MY_USER>	ALL=(ALL:ALL) NOPASSWD:ALL
```
comment out other groups (%)  with sudo 


Change to directory with playbooks
```
cd workstation
```

Confirm/update hosts.yml:
```
cat hosts.yml
```

Run playbook:
```
ansible-playbook -v playbooks/prom-node-exporter.yml
```

Check for Prometheus port:
```
$ netstat -tunl | grep 9101
tcp        0      0 192.168.1.x:9101      0.0.0.0:*               LISTEN
```

Test Prometheus node agent:
```
curl http://<IP_FROM_ABOVE>:9101/metrics
```

