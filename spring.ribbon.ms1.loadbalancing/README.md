# spring.ribbon.ms1.loadbalancing
loadbalancing avec Ribbon sans eureka. 

ms1 + Ribbon
--- ms2 instance 1 ( port 8200 )
--- ms2 instance 2 ( port 8201 )
				  
http://localhost:8080/getmicro2

Il faut désactiver eureka et ajouter la liste des serveurs
Application.properties
micro1.ribbon.eureka.enabled = false
micro1.ribbon.listOfServers = localhost:8200, localhost:8201 

Notice : 
- Démarrer 2 instances du serveur spring.ribbon.ms2  en changeant le port. 
- Démarrer spring.ribbon.ms.loadbalancing
- Accèder l'URL http://localhost:8080/getmicro2, l'algorithme par défault de loadbalancing, RoundRobin, tapera tantot une instance puis l'autre.
La page HTML affichera "Currently hitting instance running on port: 8200" ou "Currently hitting instance running on port: 8201"

Référence:
https://www.studytonight.com/post/load-balancing-spring-boot-microservices-using-netflixs-ribbon 