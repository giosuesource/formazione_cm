
# Step. 1
### Descrizione esercizio:

Lo scopo di questo esercizio è quello di creare un playbook Ansible che configuri un Docker registry (anche senza autenticazione)

### Tools utilizzati:
- Ansible (https://docs.ansible.com/)
- Docker (https://docs.docker.com/)

### Svolgimento:

Per iniziare è stato settato "localhost" come macchina su cui eseguire il playbook e "become: yes" per eseguire il tutto con i permessi di Root.

A seguire si inizia con i task, bisogna scaricare Docker e farlo partire. Abbiamo utilizzato "state: present", questo comando scarica Docker solamente se non è già presente sulla macchina.

Successivamente bisogna pullare l' immagine "registry", che poi si utilizzerà per la creazione del container Registry.