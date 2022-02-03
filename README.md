# WSL + microk8s + ingress-controller + metallb


sudo apt update
  
sudo snap install microk8s --classic
  * Caso de erro, habilite o daemod
  * snap --version

sudo usermod -a -G microk8s $LOGNAME
  
sudo microk8s config view  

---

### habilitar adom microk8s 
sudo microk8s enable helm3 ingress dns

* sudo microk8s enable helm3 storage ingress dns

* no WSL executar o comando 'ip addr | grep eth0' para pegar o IP da maquina.
* sudo microk8s enable metallb:IP_ACIMA-IP_ACIMA
    * sudo microk8s enable metallb:172.20.154.9-172.20.154.9


### snapd unavailable -  Habilitando o daemod
  
    sudo apt-get update && sudo apt-get install -yqq daemonize dbus-user-session fontconfig
	sudo daemonize /usr/bin/unshare --fork --pid --mount-proc /lib/systemd/systemd --system-unit=basic.target
	
	
	### toda a vez que for precisar o snap precisa executa a linha abaixo
	exec sudo nsenter -t $(pidof systemd) -a su - $LOGNAME

	snap version
	
	
## exemplo
   ### ingress controller
   * kubectl apply -f ingress.yml

   ### aplicação exemplo: deploy + service + ingress 
   * kubectl apply -f nginx.yml

---
## Dashboard
  * sudo microk8s enable dashboard
  * sudo microk8s dashboard-proxy
```
Checking if Dashboard is running.
Waiting for Dashboard to come up.
Dashboard will be available at https://127.0.0.1:10443
Use the following token to login:
eyJhbGciOiJSUzI1NiIsImtpZCI6InFTOD...
```
    * troque o 127.0.0.1:10443 por IP_DO_WSL:10443
  
## portainer - UI gerenciado do cluster  - porta 30777 
  * sudo microk8s enable portainer

  *  http://IP_DO_WSL:30777
