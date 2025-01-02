
# Step. 5
### Descrizione esercizio:

Lo scopo di questo esercizio è quello di creare un container che oltre ai requisiti dello Step 2 abbia anche il servizio Docker o Podman attivo.
Inoltre si deve configurare una pipeline Jenkins che esegua una build di un'immagine e la tagghi in modo progressivo, facendo poi il push dell'immagine sul registry

### Tools utilizzati:
- Docker (https://docs.docker.com/)
- Jenkins (https://www.jenkins.io/doc/)

### Svolgimento:

Per iniziare bisogna andare a crare un Dockerfile contenente una struttura basilare, che servirà più avanti. Poi si potrà creare il container avente l' immagine "jenkins/jenkins:lts" utilizzando il comando "docker run -d    --name ContainerStep5    -p 8080:8080 -p 50000:50000     -v /var/run/docker.sock:/var/run/docker.sock     -v jenkins_home:/var/jenkins_home    jenkins/jenkins:lts". In questo modo si andrà a creare il container andando a specificare il nome, le porte, i volumi che ci permetteranno di utilizzare Docker e l' immagine. 
Una volta creato si dovrà utiizzare il comando "docker exec ContainerStep5 cat /var/jenkins_home/secrets/initialAdminPassword" sul terminale, al fine di ottenere la password di accesso a Jenkins.
Adesso si dovrà andare ad aprire una shell Root del container con il comando "docker exec --user root -it ContainerStep5 bash". Da qui si potrà fare il comando "apt get-update && apt get-install docker.io".
In questo modo verrà scaricato Docker e si dovrà poi modificare le proprietà del volume con il comando "chown root:docker /var/run/docker.sock", modificare i permessi del volume con il comando "chmod 660 /var/run/docker.sock" e aggiungere l' utente Jenkins al gruppo Docker con il comando "usermod -aG docker jenkins". 
Infine possiamo uscire dalla shell del container ed utilizzare il comando "docker restart ContainerStep5" per restartare.
Adesso si potrà creare un nuovo Jenkinsfile nel quale fra poco andremo a scrivere la pipeline e nel frattempo si potrà navigare dal browser locale sulla pagina "http://localhost:8080" per fare l' accesso su Jenkins con le credenziali ricavate in precedenza. Successivamente si potranno andare a configurare i plugin, le credenziali e la source repository all' interno della pagina di Jenkins. 
A questo punto si potrà andare a configurare la pipeline, andando a fare inizialmente un "checkout SCM", per poi andare a taggare progressivamente, buildare e pushare l' immagine docker creata in precedenza sul Registry Locale creato nello step 1.