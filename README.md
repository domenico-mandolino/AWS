# AWS
Architecte AWS
Pas comme “numérobis”

Introduction du sujet

Il est temps de mettre en pratique les compétences que vous avez acquises
durant la semaine passée sur AWS.

Jusqu’ici, vous avez appris à utiliser les différents services individuellement, le
but maintenant est de les utiliser tous ensemble et faire de l’architecture de
solutions AWS.

Il sera impératif de documenter chacune des étapes de la réalisation du
sujet.



Job 1

Il est temps de voir les grands principes qui justifient l’utilisation de services
AWS, mais avant afin de s’assurer de quelque chose...

Commencez par rédiger une réponse de quelques lignes qui explique les
avantages d’utiliser un service comme AWS, quels sont ses points forts et
faibles et finir par citer un cas dans lequel vous jugerez bon de faire cela sur
AWS plutôt que sur une infrastructure sur site classique.

Job 2

Sur AWS, il existe une fonctionnalité de load balancing dans le service EC2 :

Commencez par indiquer sur votre documentation à quoi sert un load
balancer (en français un “équilibreur de charges”), quels sont les différents
Load Balancer que propose AWS avec leurs spécifications, à quelles
problématiques cela répond et donnez un cas d’utilisation.



Job 3

Revenez à vos consoles AWS et commencez par déployer deux instances
avec les spécifications suivantes :

- L'image d'exécution sera "Amazon Linux"
- le type d'instance sera la plus petite (renseignez-vous bien)
- comme on doit y avoir accès depuis SSH, il faudra générer une key pair
- il faut que le trafic soit ouvert pour tout le monde sur les ports 80 et 443
- comme storage, un disque gp2 de 8Go
- et dans la partie User Data, exécuter un script qui permet le déploiement
d’un serveur web ( bash )

une fois cette étape effectuée, déployez un ALB (Application Load Balancer)
en le déployant sur toutes les AZ (Availability Zone), créez également un
groupe de sécurité que vous nommerez “demo-sg-load-balancer” et pour
finir, créez un target group qui sera composé des deux instances que vous
avez créées précédemment.

Prenez le DNS name de votre load balancer et lancer la recherche depuis
votre navigateur : Bravo maintenant, vous avez déployé votre premier Load
Balancer



Job 4

Maintenant la chose est la suivante, vous pouvez toujours avoir accès à vos
instances EC2 directement par leurs adresses IP, mais il faut qu’elles soient
uniquement accessibles depuis le load balancer.

Bloquer l’accès aux instances par leurs IP public en éditant les règles
entrantes du ou des bons groupes de sécurité.

Job 5

Il est temps d’introduire le concept de Sticky Sessions :

Dans un premier temps, faites vos recherches dessus et intégrez dans votre
documentation le résultat de ces dernières tout en répondant aux questions
suivantes :

Quel est le but des sticky sessions ?
À quelle problématique répond cette fonctionnalité ?

Et pour finir, mettez en place les sticky sessions dans les règles de votre
“target group”.



Job 6

Chiffrez les communications vers votre load balancer avec un certificat
SSL/TLS.

Job 7

Abordons maintenant le principe du scaling :

Commencez par définir ce qu’est le scaling et citez les deux types de scaling
qui existent.

Une fois cela effectué, créez votre premier ASG (Auto Scaling Group),
commencez par configurer votre template en choisissant l’image, les
caractéristiques de la machine et placez dans la partie user data les
commandes nécessaires au déploiement d’un serveur web.

Et pour finir, il faut que votre group size ait les caractéristiques suivantes :

Desired capacity : 1
Minimum capacity : 1
Maximum capacity : 10



Job 8

On vient de voir le scaling, mais ça serait bien qu’il puisse se gérer lui-même
et scale-in ou scale-out sans qu’on ait à le faire manuellement :
Par exemple si j’ai un site e-commerce et que je sais par avance que je vais
avoir un pic d’activité ce week-end, car j’ai mis de belles promotions sur mes
articles.

Mettez en place une scaling policy qui scale-out si le CPU de vos instances
dépasse les 80% d’utilisation.

Job 9

Cela serait pas mal de pouvoir vérifier par des tests que le scale-out
fonctionne bien, effectuez un stress test du CPU sur votre instance en utilisant
le paquet suivant :
![image](https://github.com/user-attachments/assets/1b8c5a07-8ff6-4595-89c9-4c99183d3d8e)


Compétences visées

● Haute Disponibilité
● Sécurité cloud
● Administration infrastructure cloud

Base de connaissances

● AWS Load Balancer
● AWS Scaling Group
● AWS Scaling Policy
