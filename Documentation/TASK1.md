# TASK 1

*1 . Explain how the load balancer behaves when you open and refresh the URL <http://192.168.42.42> in your browser. Add screenshots to complement your explanations. We expect that you take a deeper a look at session management.*

La première requête nous envoie sur le serveur s2 et si nous rafraîchissons la page, nous arrivons sur le serveur s1. Après plusieurs rafraîchissements de la page web, nous pouvons remarquer que nous changeons de serveur.



 

![](/home/daniel/Documents/AIT/Teaching-HEIGVD-AIT-2019-Labo-Load-Balancing/Documentation/images/image-20191113153215238.png)



![image-20191113153339497](/home/daniel/Documents/AIT/Teaching-HEIGVD-AIT-2019-Labo-Load-Balancing/Documentation/images/TASK2.md)



Actuellement, nous avons un cookie "NODESESSID" qui correspond à un numéro de session. Nous pouvons nous apercevoir qu'il envoie à chaque requête son numéro de session mais que le serveur redéfini son id de session. Du coup, la session n'est pas préservé entre chaque requête.

![image-20191113153907662](/home/daniel/Documents/AIT/Teaching-HEIGVD-AIT-2019-Labo-Load-Balancing/Documentation/images/image-20191113153907662.png)

*<u>2. Explain what should be the correct behavior of the load balancer for session management.*</u>

Le comportement correct d'un load balancer concernant la gestion de session est de renvoyé un client toujours sur le même serveur. En effet, ainsi la session est maintenue. 
Prenons un exemple concret:
Si un utilisateur se connecte sur un site de e-commerce et rajoute un article dans le panier, et que en rajoutant un deuxième article, il est redirigé vers un autre serveur, le premier article sera perdu.
En redirigeant le serveur sur le même serveur, ce problème ne surviendrait pas et le panier serait toujours le même.



*3. Provide a sequence diagram to explain what is happening when one requests the URL for the first time and then refreshes the page. We want to see what is happening with the cookie. We want to see the sequence of messages exchanged (1) between the browser and HAProxy and (2) between HAProxy and the nodes S1 and S2.*![image-20191113163525757](/home/daniel/Documents/AIT/Teaching-HEIGVD-AIT-2019-Labo-Load-Balancing/Documentation/images/image-20191113163525757.png)

![img](blob:https://web.telegram.org/c153ac86-fa4d-424c-ae10-cad9f4742d80)

*4. Provide a screenshot of the summary report from JMeter.*

Nous pouvons remarquer, comme expliqué au point 1, que le load balancer distribue les requêtes uniformément à chaque serveur.

![image-20191113154354029](/home/daniel/Documents/AIT/Teaching-HEIGVD-AIT-2019-Labo-Load-Balancing/Documentation/images/image-20191113154354029.png)



*5. Run the following command:*

```bash
$ docker stop s1
```

*Clear the results in JMeter and re-run the test plan. Explain what is happening when only one node remains active. Provide another sequence diagram using the same model as the previous one.*

La performance est grandement impacté car le load balancer va tenter d'atteindre le serveur éteint. 

![image-20191113154805779](/home/daniel/Documents/AIT/Teaching-HEIGVD-AIT-2019-Labo-Load-Balancing/Documentation/images/image-20191113154805779.png)





