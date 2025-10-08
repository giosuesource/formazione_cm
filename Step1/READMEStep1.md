
## Step. 1
### Descrizione esercizio:

Lo scopo di questo esercizio è quello di creare un playbook Ansible che configuri un Docker registry (anche senza autenticazione)

### Tools utilizzati:
- Ansible (https://docs.ansible.com/)
- Docker (https://docs.docker.com/)

### Svolgimento:

Per iniziare è stato settato "localhost" come macchina su cui eseguire il playbook e "become: yes" per eseguire il tutto con i permessi di Root.

A seguire si inizia con i task, essendo su macchina host con sistema operativo MacOS, di deve utilizzare "ansible.builtin.command: "open -a Docker" per far partire Docker. Poi si deve andare a pullare l' immagine "registry", che si utilizzerà nell' ultimo taask per la creazione del container Registry, il quale è stato configurato su porta 5000.

Per eseguire il playbook si deve andare sul terminale del Mac ed utilizzare il comando "ansible-playbook Step1/container_playbookStep1.yml --ask-become-pass". In questo modo il playbook verrà eseguito e verrà richiesta la password di SUDO in Input.

Per verificare la creazione del Registry è possibile utilizzare il comando "docker ps -a", il quale ci elencherà tutti i container attivi, tra cui quello appena creato.
