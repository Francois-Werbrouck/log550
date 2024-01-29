LABO #1 TODO ->  samedi 24 février 2024 à 23 :59

Lundi 22 Janvier - Rencontre #1 postponed
Lundi 29 Janvier - Rencontre: division des taches, établir un calendrier des attentes selon les tâches
Lundi 05 Février - Touchbase #1: Discussion des avancement du code - plan de match pour amorcer le code
Vendredi 09 Février - Update message discord sur nos avancé + plan de match d'ici le touchbase #2
Lundi 12 Février - Touchbase #2 - Code devrait être +- terminer
Vendredi 16 Février - Touchbase (après cours? ou update message discord dépendant de l'avancé) update dernier bugs restant + plan de match fds avant les tests
Lundi 19 Février - Test de performance + discussion rapport
Vendredi 23 Février - Mise au propre rapport
Samedi 24 Février - Remise


L’objectif de ce laboratoire est de développer le programme d’acquisition sur le microcontrôleur
STM32L4S5VIT6 sur carte de développement B-L4S5I-IOT01A. Ce programme permettra de faire
l’échantillonnage à taux constant d’un signal analogique et l’acquisition d’un capteur numérique. Les
échantillonsseront envoyés vers le port série. Puisque le port de la carte B-L4S5I-IOT01A est relié à un
PC, il sera possible de visualiser les données numériques reçues en temps réel. Les fonctionnalités
exigées de ce programme sont décrites plus loin.

Spécifications codes:

Opération des diodes lumineuses (LEDs) (20%)

• Indications de fonctionnement
  Le LED1 doit clignoter à une fréquence de 4Hz pour démontrer l’opération de votre programme. Le
  LED2 doit clignoter à une fréquence de 4Hz pour démontrer que votre programme est en acquisition.
  Les LEDS 1 et 2 doivent être synchronisés ensemble s’il y a lieu.y lieu.
  Il est important de noter qu’une fréquence de 1Hz (1 cycle/seconde) signifie 1 séquence complète ONOFF par seconde.
• Alarme – Détection de dépassement au convertisseur ADC
  Le LED3 doit s’allumer et rester allumé si un dépassement est survenu au niveau du ADC (Si
  l’interruption de fin de conversion du ADC survient alors que l’échantillon précédent n’a pas encore
  été traité).
• Alarme – Détection de dépassement en transmission UART
Le LED3 doit s’allumer et rester allumé si un dépassement est survenu au niveau de l’UART en
transmission (Si on doit transmettre un nouvel échantillon alors que la transmission précédente n’est
pas encore terminée).

Acquisition de données (20%)

E1 - Acquisition d’un signal analogique
  Le système doit être capable d’échantillonner du canal analogique, le capteur de son, à une fréquence
  de 1000 ou 2000 échantillons par seconde. La vitesse d’échantillonnage par défaut, au démarrage, est
  de 1000 éch/sec. Il est important de noter que le microcontrôleur, pour traiter ces données, nécessite
  une conversion de signal analogique à numérique via un convertisseur analogique-numérique (ADC).
E2 - Acquisition d’un signal numérique
  Le système doit être capable également d’envoyer les valeurs de la température provenant d’un
  capteur numérique à une fréquence constant de 1 mesure par seconde.
E3 - Changement de la vitesse d’acquisition
  La vitesse d’échantillonnage du signal analogique par défaut, au démarrage, est de 1000 éch/sec. Sur
  l’action de l’interrupteur (bouton), on passe à une vitesse de 2000 éch/sec. L’action successive de
  l’interrupteur permet de « toggler » entre les 2 vitesses.
E4 – Représentation des données d’échantillonnage
  L’échantillonnage du signal analogique de son et la mesure numérique du capteur de température
  doivent être des valeurs entières sur 32 bits.
E5 - Envoi des échantillons par le lien série
  Le système doit envoyer les échantillons à l’ordinateur maître par le lien série sans perdre ou réécrire
  aucun échantillon. Le format des échantillons doit suivre la spécification dans la section suivante de
  ce document. Il ne doit pas y avoir inversion de type des échantillons.
  Il est important de ne pas utiliser la fonction printf() pour envoyer les échantillons.
E6 - Réception des commandes du système maître
  Le système doit être capable de recevoir et de traiter rapidement les commandes transmises par
  l’ordinateur maître sur le lien série. La réception des caractères de commande doit utiliser la méthode
  des interruptions.
E8 - Minimisation de l’interrogation des périphériques
  On vous demande de privilégier l’utilisation des interruptions pour éviter d’interroger l’état d’un
  périphérique. Pour cela, Il est conseillé d’utiliser le programme principale ( main() ) de l’application
  pour initialiser uniquement les périphériques du microcontrôleur. Toutes les fonctionnalités devront
  être implémentées dans les routines d’interruption

Envois et reception des données via l'UART (20%)

  Le système transmet les valeurs des échantillons en utilisant 8 bits. Pour le cas de l'échantillon du son,
  il est demandé de codifier sa valeur initiale divisée en deux afin de minimiser le risque de débordement
  (à la réception, l’oscilloscope va le multiplier par 2). La valeur de l'échantillon de la température reste
  sans changement.
  Par la suite le bit 0 (LSB-Least Significant Bit) de l’octet à transmettre est utilisé pour identifier le canal
  de son (LSB=0) ou capteur de température (LSB=1). Voici quelques exemples d’illustration

Communication provenant de l’ordinateur maître
    Le système reçoit les commandes de l’ordinateur maître sous forme de caractères ASCII. Les
    commandes suivantes sont disponibles :
Caractère    Action
s            Démarrer l’acquisition
x            Arrêter l’acquisition 
  


Dans le rapport, vous devez inclure ce qui suit (20%):
● Une discussion sur toutes les implémentations d'interruptions utilisées (1-2 page).
o Justifiez les variables globales utilisées
o Expliquez et justifiez le travail fait dans la routine de l'interruption.
● Expliquer comment vous vous assurez que votre programme envoie toujours le bon nombre
d'échantillons (1/2 page).
● Discutez de vos principales difficultés (~1/2 page).
● Une discussion des limites de l’implémentation que vous avez réalisée (~1/2 page).
● Une identification claire de la contribution des membres de votre équipe.
● N'oubliez pas votre page de présentation








