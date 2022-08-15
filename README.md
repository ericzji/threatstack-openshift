# threatstack-openshift


❯ git clone https://github.com/threatstack/threatstack-helm.git
❯ cd threatstack-helm
❯ helm repo add threatstack https://pkg.threatstack.com/helm
"threatstack" has been added to your repositories
❯ helm install threatstack-agent --values values.yaml threatstack/threatstack-agent
NAME: threatstack-agent

❯ oc get pods |grep threat
threatstack-agent-g4jcw                             1/1     Running   1             18d
threatstack-agent-kubernetes-api-77d57bd6fc-p7qdm   1/1     Running   0             18d
threatstack-agent-xc28r                             1/1     Running   0             18d
threatstack-agent-zc6d8                             1/1     Running   0             18d

❯ oc exec -it threatstack-agent-g4jcw -- tsagent status
  UP Threat Stack Agent Daemon
  UP Threat Stack Backend Connection
  UP Threat Stack Heartbeat Service
  UP Threat Stack Login Collector
  UP Threat Stack Log Scan Service
  UP Threat Stack Vulnerability Scanner
  UP Threat Stack Audit Collection

  ❯ oc exec -it threatstack-agent-xpf6l -- bash
root@ip-10-0-141-120:/# service threatstack status
root@ip-10-0-141-120:/# ps aux | grep audi
root@ip-10-0-141-120:/# sysctl stop auditd
root@ip-10-0-141-120:/# apt-get install threatstack-agent-support

❯ helm delete threatstack-agent
release "threatstack-agent" uninstalled