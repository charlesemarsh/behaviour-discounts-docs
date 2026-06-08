---
layout: default
title: Aide aux marchands
nav_exclude: true
permalink: /fr/help/
---

[English](/help/) · [Deutsch](/de/help/) · **Français**

# Behaviour Discounts — Aide aux marchands

Behaviour Discounts verrouille les remises derrière des Magic Links et des déclencheurs comportementaux. En tant que marchand, vous contrôlez quand une remise s'applique, quel attribut de panier est défini et si les cadeaux gratuits sont ajoutés automatiquement.

## Premiers pas

- Installez l'app et acceptez les autorisations requises.  
- Dans Boutique en ligne → Intégrations d'apps, activez l'intégration de thème Behaviour Discounts.  
- Créez votre premier Magic Link (paramètre de campagne + valeur) et liez-le à une remise.  
- Optionnel : ajoutez un déclencheur comportemental (consultation de produit ou temps passé sur le site/la page) avec le contenu du popup.  
- Testez dans une prévisualisation de thème avant de passer en production.

## Comment ça marche

- L'intégration de thème injecte `magic-link-handler.js` dans la boutique.  
- Elle récupère les configurations actives via `/api/magic-links` et `/api/behaviour-triggers`.  
- Si l'URL actuelle correspond au paramètre/à la valeur d'un Magic Link, elle pose un cookie `magic_link_discount`, le duplique dans `sessionStorage` et écrit `magic_link_campaign` dans le panier avant le checkout.  
- Les déclencheurs comportementaux écrivent `behaviour_trigger_campaign` après acceptation du popup ; ils sont supprimés dès qu'un Magic Link est actif.  
- Quand une remise associée propose des produits gratuits, le handler ajoute automatiquement les variantes cadeau étiquetées `_gift_campaign` selon les paramètres de la remise.

## Configuration de l'intégration de thème (une fois par thème)

1) Dans l'admin Shopify, allez dans **Boutique en ligne → Thèmes → Personnaliser**.  
2) Ouvrez **Intégrations d'apps** et activez **Behaviour Discounts**.  
3) Enregistrez le thème. Le script se charge maintenant sur les pages de la boutique.

## Magic Links

- Définissez une paire de paramètres d'URL requise (par ex. `?campaign=spring15`) qui doit être présente.  
- Liez à une remise Shopify Function (Produit, Commande ou Livraison) dont les métadonnées contiennent le type d'avantage, les cadeaux et les paramètres.  
- Popup optionnel : recueillez une acceptation avant d'écrire l'attribut de panier.  
- Partagez l'URL complète de la campagne dans vos e-mails/publicités ; au clic, le Magic Link reste actif via cookie/session jusqu'à effacement ou expiration.

### Modifier ou désactiver

- Modifiez le paramètre/la valeur, la remise liée ou le contenu du popup directement dans l'app.  
- Désactivez une campagne pour arrêter les nouvelles activations ; les cookies existants expirent à leur échéance normale.

## Déclencheurs comportementaux

- Types de règles : consultation de produit, temps passé sur le site, temps passé sur une page.  
- Configurez le titre/le corps du popup et la remise liée.  
- L'acceptation écrit l'attribut de panier `behaviour_trigger_campaign` et, le cas échéant, ajoute les cadeaux configurés.  
- Si un Magic Link est actif, les déclencheurs restent supprimés pour éviter l'empilement.

## QR codes

- Créez des QR codes à votre image qui déclenchent une remise lorsqu'ils sont scannés depuis des emballages, des flyers, des présentoirs en magasin ou des supports événementiels.
- Chaque QR code est lié à une remise Shopify Function (mêmes types que les Magic Links : Produit, Commande ou Livraison).
- Choisissez une page de destination (page d'accueil, produit, collection, panier ou chemin personnalisé). Le paramètre `qr` est ajouté automatiquement.
- Personnalisez l'apparence du QR code : couleurs de premier plan/arrière-plan, style des coins (carré ou arrondi), logo au centre, et un cadre optionnel avec un libellé d'appel à l'action.
- Popup optionnel : affichez un message à votre image quand le client arrive dans votre boutique après le scan.
- URL courte optionnelle : créez une redirection (par ex. `/go/scan`) pour que le lien puisse être imprimé ou partagé à côté du QR code.
- Les QR codes ont la même priorité que les Magic Links — quand l'un est actif, les déclencheurs comportementaux sont supprimés.

### Modifier ou désactiver

- Modifiez la destination, la remise, le popup, le design du QR code ou l'URL courte directement dans l'app.
- Mettez une campagne en pause pour arrêter les nouvelles activations tout en conservant vos statistiques. La suppression retire le QR code, la remise Shopify et l'éventuelle redirection d'URL.

## Cadeaux gratuits / produits gratuits

- Les remises peuvent inclure des variantes cadeau étiquetées `_gift_campaign`.  
- Modes : **auto** (cadeau ajouté automatiquement), **manual** (le client ajoute lui-même) ou **manualPopup** (ajouté après acceptation du popup).  
- `autoAddGiftCount` contrôle le nombre de cadeaux ajoutés par campagne.

## Priorité

- Les Magic Links et les QR codes partagent la même priorité : quand l'un est actif, les popups et actions des déclencheurs comportementaux sont supprimés afin que seule la remise du Magic Link ou du QR code s'applique.

## Checklist de test

- Dans une prévisualisation de thème, chargez une URL de campagne avec le paramètre/la valeur attendue et confirmez le popup (si activé) et l'état de la remise.
- Vérifiez le stockage du navigateur : le cookie `magic_link_discount` et son miroir sessionStorage sont présents.
- Ajoutez des articles au panier ; vérifiez que l'attribut de panier (`magic_link_campaign` ou `behaviour_trigger_campaign`) est écrit avant le checkout.
- Pour les cadeaux gratuits, confirmez que les bonnes variantes sont ajoutées automatiquement et retirées si la remise est désactivée.
- Déclenchez une règle comportementale (consultation de produit ou seuil de temps) sans Magic Link ; confirmez le popup et l'attribut de panier.
- Assurez-vous que les déclencheurs restent supprimés quand un Magic Link ou un QR code est actif.
- Pour les QR codes, scannez le code généré avec un téléphone et confirmez qu'il redirige vers la bonne destination avec la remise appliquée.
- Si une URL courte est configurée, visitez-la dans un navigateur et confirmez qu'elle redirige correctement.
- Utilisez le bouton **Prévisualisation pour tests** sur les QR codes et Magic Links pour forcer l'affichage du popup sans que la campagne soit active.
- Réalisez un checkout test et vérifiez que la bonne remise/le bon cadeau apparaît.

## Dépannage

- **Pas de popup ni de remise :** vérifiez que l'intégration de thème est activée et publiée.
- **Le paramètre ne correspond pas :** assurez-vous que l'URL partagée contient la paire exacte et que le Magic Link est actif.
- **Le QR code ne fonctionne pas :** vérifiez que le statut du QR code est Actif, pas Brouillon ni En pause. Scannez le code et vérifiez que l'URL de destination contient le paramètre `?qr=`.
- **L'URL courte ne redirige pas :** confirmez que la redirection a été créée correctement (vérifiez les avertissements à l'enregistrement). Vous pouvez aussi vérifier dans l'admin Shopify sous Paramètres → Navigation.
- **Chemin d'URL courte déjà pris :** chaque chemin doit être unique dans votre boutique. Choisissez un autre chemin ou supprimez la redirection existante sous Paramètres → Navigation.
- **Les cadeaux ne s'ajoutent pas :** confirmez que la variante cadeau est étiquetée `_gift_campaign` et que l'avantage de la remise est défini sur Produits gratuits avec le bon `autoAddGiftCount`.
- **Attribut de panier manquant :** vérifiez que le client a accepté le popup (si requis) et que le panier n'est pas bloqué par d'autres scripts.
- **Les déclencheurs se déclenchent toujours :** assurez-vous qu'aucun Magic Link ou QR code n'est actif depuis une session précédente ; effacez les cookies/la session ou utilisez une fenêtre privée.

## FAQ

- **Quels types de remises sont pris en charge ?** Produit (pourcentage/montant fixe/cadeau), Commande (pourcentage/montant fixe avec sous-total/quantité minimum optionnels) et Livraison (pourcentage/montant fixe/gratuit), tous propulsés par Shopify Functions.
- **Puis-je empêcher l'empilement ?** Oui. Les Magic Links et les QR codes suppriment les déclencheurs comportementaux ; au sein d'une remise, les règles d'empilement sont appliquées par la configuration de la Function.
- **Où je modifie le contenu du popup ?** Dans les paramètres du Magic Link, du QR code ou du déclencheur comportemental, pour chaque campagne.
- **Comment les remises sont-elles configurées ?** Les métadonnées (type d'avantage, cadeaux, paramètre/valeur) sont stockées dans le métachamp de configuration de la Function et lues à l'exécution.
- **Quelle est la différence entre un Magic Link et un QR code ?** Les Magic Links utilisent un paramètre d'URL personnalisable (par ex. `?ref=summer`) et sont pensés pour un partage numérique. Les QR codes utilisent toujours le paramètre `qr` avec une valeur auto-générée et incluent une image QR scannable pour l'impression et les supports physiques. Les deux prennent en charge les mêmes types de remises, popups et URL courtes.
- **Puis-je utiliser le même chemin d'URL courte pour un Magic Link et un QR code ?** Non. Les chemins d'URL courte doivent être uniques dans toute votre boutique, qu'ils appartiennent à un Magic Link ou à un QR code.
- **Puis-je utiliser « qr » comme nom de paramètre Magic Link ?** Non. Le nom de paramètre `qr` est réservé aux QR codes. Choisissez un autre nom pour vos Magic Links (par ex. `ref`, `promo`, `campaign`).
- **Que se passe-t-il si je supprime un QR code ou un Magic Link avec une URL courte ?** La redirection d'URL Shopify est automatiquement supprimée avec la campagne et la remise associée.
- **Puis-je mettre un QR code en pause sans le supprimer ?** Oui. La pause arrête l'application de la remise mais conserve vos statistiques et votre configuration. Vous pouvez le réactiver plus tard.

## Besoin d'aide ?

Envoyez un e-mail à `support@example.com` avec le domaine de votre boutique, l'URL de la campagne et une brève description de ce que vous attendiez vs ce que vous avez vu.
