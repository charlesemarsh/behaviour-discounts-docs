---
layout: default
title: Confidentialité et utilisation des données
nav_exclude: true
permalink: /fr/privacy/
---

[English](/privacy/) · [Deutsch](/de/privacy/) · **Français**

# Confidentialité et utilisation des données

Comment Behaviour Discounts traite les données des marchands et des acheteurs. Adaptez ce texte à vos propres politiques et aux exigences juridiques applicables.

## Données que nous stockons (backend de l'app)

- **Magic Links :** paires paramètre/valeur, remise liée, paramètres de popup et métadonnées de campagne (stockés via Prisma).  
- **Déclencheurs comportementaux :** type de règle (consultation de produit, temps passé sur le site/la page), seuils, contenu du popup, remise liée et état.  
- **Métadonnées de remise :** type d'avantage, cadeaux, paramètre/valeur et options stockés dans le métachamp de configuration d'une Shopify Function.  
- **Facturation :** sélection du forfait (Free, Starter, Business, Enterprise) et identifiants de facturation Shopify.  
- **Logs opérationnels :** logs de service et d'erreurs pour le débogage ; aucune vente de données.

## Données lues/écrites côté client

- **Cookies/session :** cookie `magic_link_discount` plus un miroir dans sessionStorage pour conserver la campagne active.  
- **Attributs de panier :** `magic_link_campaign` ou `behaviour_trigger_campaign` écrits avant le checkout pour indiquer à la Function quelle remise appliquer.  
- **Cadeaux gratuits :** des variantes cadeau étiquetées `_gift_campaign` peuvent être ajoutées automatiquement au panier selon la configuration.

## Télémétrie côté acheteur

- Paramètres d'URL pour détecter l'activation d'un Magic Link.  
- Événements de consultation de produit (pour déclencher les popups) et seuils de temps passé sur le site/la page.  
- Acceptations/rejets de popups liés aux campagnes (uniquement pour l'activation ; les métriques d'impression/d'acceptation sont prévues mais pas encore implémentées).

## Jetons d'API et accès

- Utilisation d'un jeton Admin API hors ligne pour hydrater les remises et lire/écrire les métachamps.  
- L'accès est limité aux scopes accordés à l'installation ; la rotation suit les bonnes pratiques des apps Shopify.

## Partage de données et sous-traitants

- Shopify agit comme sous-traitant principal des données ; les sous-traitants supplémentaires se limitent aux fournisseurs d'infrastructure/de monitoring.  
- Aucune donnée n'est vendue ou louée. L'accès en production est restreint au personnel autorisé pour le support et l'exploitation.

## Conservation et suppression

- Les configurations et les métachamps sont conservés tant que l'app est installée.  
- Les logs sont conservés pour des besoins opérationnels et tournés selon un calendrier standard.  
- En cas de désinstallation ou sur demande, les configurations stockées et les métachamps associés peuvent être supprimés ; envoyez les demandes de suppression via le support.

## Vos obligations (marchands)

- Assurez-vous d'avoir une base légale pour traiter les données personnelles (par ex. consentement, contrat, intérêt légitime).  
- Évitez d'envoyer des données personnelles sensibles via les paramètres de campagne ou les déclencheurs.  
- Mettez à jour cette notice pour refléter vos propres flux de données, vos prestataires et la réglementation applicable (RGPD, CCPA).

## Droits

- Nous aiderons aux demandes d'accès, de rectification ou de suppression pour les données que nous contrôlons, sous réserve de vérification.  
- Les acheteurs doivent contacter le marchand en premier ; les marchands peuvent nous relayer les demandes.

## Sécurité

- Le chiffrement en transit (HTTPS/TLS) est requis pour les appels admin et boutique.  
- Principe du moindre privilège pour les accès opérateurs ; les accès et les modifications de remises sont audités régulièrement.

## Besoin d'aide ?

Questions sur la confidentialité ou les données ? Envoyez un e-mail à `support@example.com` avec le domaine de votre boutique et la campagne/le déclencheur concerné.
