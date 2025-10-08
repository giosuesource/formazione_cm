
## Step. 2
### Descrizione esercizio:

Lo scopo di questo esercizio è quello di utilizzare Ansible per creare dei playbooks che facciano la build di almeno due container con OS differenti
Queste build devono generare dei container che siano sempre in ascolto sulla porta 22, abbiano attivo il servizio ssh e abbiano un utente abilitato a collegarsi tramite ssh key, il quale possa fare sudo

### Tools utilizzati:
- Ansible (https://docs.ansible.com/)
- Docker (https://docs.docker.com/)

### Svolgimento:

Per iniziare bisogna andare a creare 2 Dockerfile che ci serviranno per buildare l' immagine dei containers. Il primo Dockerfile avrà Ubuntu:22.04 come "immagine di partenza", mentre l' altro avrà "kalilinux/kali-rolling". 

Tramite i Dockerfile si deve installare openssh-server ed aggiungere "EXPOSE 22", per configurare la porta utilizzabile per la connessione SSH. Inoltre si dovranno andare a creare le cartelle che conterranno le chiavi SSH. Dopo la creazione che si effettuerà nel passaggio successivo, si potranno andare a copiare al loro interno le chiavi pubbliche e private che saranno generate nella macchina host.

Nella macchina host si potrà utilizzare il comando "ssh-keygen -t rsa -b 4096 -f /file/path/id_key_genericuser" per andare a generare le chiavi. Questo comando andrà a specificare la lunghezza della chiave e il path.

Infine si dovrà andare a creare l'utente "genericuser", il quale verrà abilitato alla connessione SSH utilizzando la chiave pubblica. 

Si dovranno poi andare a scrivere i playbook: al loro interno si dovrà effettuare la build delle immagini Docker e successivamente si potrà effettuare la creazione dei container in ascolto sulla porta 22.
