
# Step. 3
### Descrizione esercizio:

Lo scopo di questo esercizio è quello di creare dei ruoli Ansible utilizzando le task dello step precedente. Le task devono avere le seguenti caratteristiche:
- Creazione e configurazione di un registry 
- Build di almeno due container 
- Push delle build sul registry precedentemente creato
- Run dei container in modo che non vadano in conflitto di porte tra loro

### Tools utilizzati:
- Ansible (https://docs.ansible.com/)
- Docker (https://docs.docker.com/)
- Roles (https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_reuse_roles.html)

### Svolgimento:

Per la creazione dei Roles serviranno degli step preliminari: bisogna andare nella directory .ansible e creare una nuova sottodirectory chiamata Roles. Dopo averla creata ci si deve spostare al suo interno e si deve utilizzare il comando ansible-galaxy init nome_role. In questo modo verrà creata una struttura ad albero contenente directory e files vari, che verranno riempiti con le task e altro. 

Adesso si inizia con i task: per creare i primi task si deve modificare il file tasks/main.yaml, andando ad aggiungere i vari tasks che verranno poi usati nel main_playbook. Proprio per questo nel main_playbook, prima di inserire le tasks, si devono dichiarare i roles che si utilizzeranno e i 2 Dockerfile su con cui andremo a lavorare.
