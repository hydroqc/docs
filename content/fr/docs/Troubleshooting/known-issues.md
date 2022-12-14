---
title: Problèmes connus
linkTitle: Problèmes connus
weight: 52
description: >
  Problèmes dont nous sommes conscients et leurs solutions de contournement.
lastmod: 2022-09-21T18:41:22.563Z
---

## Hydroqc2mqtt (ou l'addon) redémarre souvent

Hydro-quebec a souvent une maintenance sur leurs systèmes qui se traduiront par des erreurs dans les clients Hydroqc.Si votre installation est généralement fonctionnelle, mais que le conteneur / addon redémarre de temps en temps, il n'est pas nécessaire de s'inquiéter.

Pour le addon Home-Assistant vous pouvez utiliser l'automatisme suivant pour redémarrer le addon:

```yaml
alias: AUTO restart HydroQC
description: Restart automatiquement l'addon à 4h00 AM si il est planté/arrêté
trigger:
  - platform: time
    at: "05:31:00"
condition:
  - condition: state
    entity_id: binary_sensor.hydroqc_add_on_running
    state: "off"
action:
  - service: hassio.addon_restart
    data:
      addon: 57e6a4ee_hydroqc
mode: single
```

## Entitées en double dans Home-Assistant

Parfois, si des problèmes sont rencontrés lors de la configuration initiale de Hydroqc2MQTT (ou de l'addon), il peut s'exécuter avec des valeurs non valides et créer des entités vides.

Vous pouvez résoudre ce problème en faisant ce qui suit

1. Arrêtez Hydroqc2MQTT ou l'addon

2. Laissez MQTT en cours d'exécution

3. Allez dans l'intégration MQTT dans Home-Assistant et ouvrez l'entité Hydroqc

4. Dans la case "Info de l'appareil", cliquez sur les trois points et cliquez sur "Supprimer"
  Cela supprimera toutes les entités Hydroqc Home-Assistant et dans MQTT.

5. Vous pouvez ensuite démarrer Hydroqc2MQTT ou l'addon et toutes les entités seront recréées sans les doublons.

## `binascii.Error: Incorrect padding` error

Nous avons eu un signalement de ce problème. Le problème provient du portail client Hydro-Québec renvoyant un JSON malformé lorsque le nom de la personne contient des caractères spéciaux (par exemple Benoît). La solution consiste à modifier le nom dans le portail client.

- Connectez-vous à votre portail client hydro-quebec

- Déplacez votre curseur sur votre nom en haut à droite

- Cliquez sur "Informations de connexion" (Données d'identification)

- Changez votre nom complet pour supprimer tous les caractères accentués

Essayez à nouveau le module.