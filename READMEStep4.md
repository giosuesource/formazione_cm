
# Step. 4
### Descrizione esercizio:

Lo scopo di questo esercizio è oscurare tutte le password (come quella degli utenti nei Dockerfile o user e password per il registry) utilizzando Ansible Vault.

### Tools utilizzati:
- Ansible (https://docs.ansible.com/)
- Docker (https://docs.docker.com/)
- Ansible Vault (https://docs.ansible.com/ansible/2.9/user_guide/vault.html)

### Svolgimento:

Ansible vault è uno strumento che consente di criptare valori e strutture dati all’interno di file di progetto Ansible, proteggendoli da accessi non autorizzati.

Per iniziare ad utilizzarlo ci si deve posizionare nella directory dove è posizionato il Playbook Ansible e si deve utilizzare il comando "ansible-vault create vault.yml". In questo modo verrà creato un encrypted file.

Dopo aver digitato questo comando, verrà richiesto di aggiungere una password e verrà chiesto il percorso dove andare a posizionare questo contenuto. 
A questo punto è possibile verificare che il file sia criptato usando il comando cat.

Se il file è correttamente criptato, possiamo usare il comando "ansible-vault edit vault.yml" per andare a modificarlo.

Quando facciamo partire un playbook che usa Vault password memorizzate in un tool di terze parti, bisogna specificare allo script il percorso del file Vault con il flag --vault-id. 
