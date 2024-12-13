
# Step. 2
### Descrizione esercizio:

Lo scopo di questo esercizio è quello di utilizzare Ansible per creare dei playbooks che facciano la build di almeno due container con OS differenti
Queste build devono generare dei container che siano sempre in ascolto sulla porta 22, abbiano attivo il servizio ssh e abbiano un utente abilitato a collegarsi tramite ssh key, il quale possa fare sudo

### Tools utilizzati:
- Ansible (https://docs.ansible.com/)
- Docker (https://docs.docker.com/)

### Svolgimento:

Per iniziare, come negli step precedenti, bisogna scaricare e startare Docker.
Si deve poi pullare l' immagine scelta, in questo caso sono state scelte "kalilinux/kali-rolling" e "ubuntu:latest", per poi creare il container.

Come da traccia, il container deve restare in ascolto sulla porta 22. Per cui si deve settare "exposed_ports: 22" per specificare la porta esposta e poi bisogna mappare la porta 22 del container alla porta 22 dell' host per consentire la connessione SSH, andando ad inserire "published_ports: 22:22". 

Successivamente si passa alla generazione della coppia di chiavi SSH con il modulo  community.crypto.openssh_keypair, al quale si deve specificare il percorso in cui salvare la chiave pubblica. 

Si prosegue configurando la chiave SSH pubblica per la connessione con il modulo ansible.posix.authorized_key nella macchina host, per poi andare a scaricare il client ssh e sudo. dopo di ciò è possibile creare lo user giosue e aggiungerlo al gruppo sudo.

Infine si può copiare la chiave pubblica inserita inizialmente nella macchina Host, all' interno del container. Così facendo la configurazione SSH sarà pronta, pertanto si potrà startare ed abilitare la connessione.