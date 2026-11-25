# Livrable 1 – Choix de projet et plan de projet

Station météorologique intelligente \| 420-314 – Automne 2026

Membres de l’équipe : Ayoub Mazari et Hamza

## 1. Description du problème et fonction du prototype

Notre projet consiste à créer une station météorologique intérieure permettant de surveiller les conditions ambiantes d’une pièce.

Le LCD affichera la température, l’humidité et la date. Le capteur de son mesurera le bruit ambiant : la LED bleue sera éteinte si le bruit est faible, à 50 % s’il est modéré et à 100 % s’il est élevé. Le buzzer sonnera à partir de 28 °C ou au-dessus de 65 % d’humidité.

Un bouton-poussoir permettra de basculer entre deux modes de fonctionnement :

- Mode normal : affichage, LED adaptée au bruit et alerte sonore.

- Mode silencieux : mêmes fonctions, sans alerte sonore.

Le bruit sera évalué sur plusieurs mesures, avec des seuils calibrés. Les mesures sonores seront suspendues pendant les alertes du buzzer. En cas d’erreur, le LCD affichera un message et le système réessaiera automatiquement.

```text
DATE : 24/11/2026
TEMP : 23 C
HUM : 45%
MODE : NORMAL
```

Exemple d’affichage a changer si non concenable a l’écran LCD

## 2. Diagramme fonctionnel du système

![Diagramme fonctionnel du système](diagramme_fonctionnel.png)

## 3. Liste préliminaire des composants

| **Composant**                         | **Quantité** | **Fonction**                   |
|---------------------------------------|--------------|--------------------------------|
| DHT11 Temperature and Humidity Sensor | 1            | Capteur numérique              |
| Analog Sounds Sensor                  | 1            | Capteur analogique             |
| LCD Module                            | 1            | Affichage et composant nouveau |
| LED RGB Keyestudio (bleu)             | 1            | Sortie PWM                     |
| Buzzer Active                         | 1            | Sortie numérique               |
| Push Button                           | 1            | Changement de mode             |
| Plus de files                         | ?            | Matériel de montage            |

## 4. Attribution préliminaire des broches

| **Composant**             | **Broche Arduino** | **GPIO** | **Type**   |
|---------------------------|--------------------|----------|------------|
| DHT11                     | D2                 | 5        | Numérique  |
| Analog Sounds Sensor      | A0                 | 1        | Analogique |
| Push Button               | D3                 | 6        | Numérique  |
| LED RGB Keyestudio (bleu) | D5                 | 8        | PWM        |
| Buzzer Active             | D6                 | 9        | Numérique  |
| LCD – SDA                 | A4                 | 11       | I2C        |
| LCD – SCL                 | A5                 | 12       | I2C        |

Brochage préliminaire : vérifier la compatibilité 3,3 V des modules, les résistances de la LED et le modèle I2C du LCD. Confirmer que le LCD est nouveau en classe.

La date sera gérée par l’horloge interne de l’ESP32, synchronisée au démarrage via Wi-Fi (NTP). Elle pourrait devoir être réglée de nouveau après une coupure d’alimentation.

## 5. Répartition initiale du travail

| **Membre 1**                               | **Membre 2**                         |
|--------------------------------------------|--------------------------------------|
| Branchement des capteurs                   | Branchement de l’écran LCD           |
| Lecture de la température et de l’humidité | Programmation de l’affichage         |
| Lecture et traitement de la niveau sonore  | Programmation du buzzer              |
| Commande PWM de la LED RGB                 | Programmation du bouton et des modes |

Les deux membres participeront à l’intégration, à la gestion des erreurs, aux tests et à la réalisation du boîtier.
