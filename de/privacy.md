---
layout: default
title: Datenschutz & Datennutzung
nav_exclude: true
permalink: /de/privacy/
---

[English](/privacy/) · **Deutsch**

# Datenschutz & Datennutzung

So geht Behaviour Discounts mit Daten von Händler:innen und Käufer:innen um. Passe diesen Text an deine eigenen Richtlinien und die rechtlichen Anforderungen deines Standorts an.

## Daten, die wir speichern (App-Backend)

- **Magic Links:** Parameter-/Wert-Paare, verknüpfter Rabatt, Popup-Einstellungen und Kampagnen-Metadaten (gespeichert über Prisma).  
- **Verhaltensauslöser:** Regeltyp (Produktansicht, Verweildauer auf Website/Seite), Schwellenwerte, Popup-Text, verknüpfter Rabatt und Status.  
- **Rabatt-Metadaten:** Vorteilstyp, Geschenke, Parameter/Wert und Optionen, gespeichert im Konfigurations-Metafeld einer Shopify Function.  
- **Abrechnung:** Tarifauswahl (Free, Starter, Business, Enterprise) und Shopify-Abrechnungs-IDs.  
- **Betriebs-Logs:** Service- und Fehler-Logs zur Fehlerbehebung; kein Verkauf von Daten.

## Daten, die clientseitig gelesen/geschrieben werden

- **Cookies/Session:** Das `magic_link_discount`-Cookie plus eine sessionStorage-Spiegelung, damit die aktive Kampagne erhalten bleibt.  
- **Cart-Attribute:** `magic_link_campaign` oder `behaviour_trigger_campaign` werden vor dem Checkout geschrieben, damit die Function weiß, welcher Rabatt greifen soll.  
- **Gratisgeschenke:** Geschenkvarianten, die mit `_gift_campaign` getaggt sind, können je nach Konfiguration automatisch in den Warenkorb gelegt werden.

## Shopper-Telemetrie

- URL-Query-Parameter zur Erkennung einer Magic-Link-Aktivierung.  
- Produktansicht-Ereignisse (um Popups auszulösen) und Verweildauer-Schwellen auf Website/Seite.  
- Popup-Bestätigungen/-Ablehnungen, verknüpft mit Kampagnen (ausschließlich zur Aktivierung; Impressions-/Bestätigungs-Metriken sind geplant, aber noch nicht implementiert).

## API-Tokens und Zugriff

- Es wird ein Offline-Admin-API-Token verwendet, um Rabatte zu hydrieren und Metafelder zu lesen/schreiben.  
- Der Zugriff ist auf die bei der Installation gewährten Scopes beschränkt; die Rotation folgt den Best Practices für Shopify-Apps.

## Datenweitergabe und Verarbeiter

- Shopify fungiert als primärer Datenverarbeiter; weitere Unterauftragsverarbeiter beschränken sich auf Infrastruktur-/Monitoring-Anbieter.  
- Es werden keine Daten verkauft oder vermietet. Der Produktivzugriff ist auf autorisiertes Personal für Support und Betrieb beschränkt.

## Aufbewahrung und Löschung

- Konfigurationen und Metafelder werden so lange aufbewahrt, wie die App installiert ist.  
- Logs werden aus betrieblichen Gründen aufbewahrt und nach einem üblichen Plan rotiert.  
- Bei Deinstallation oder auf Anfrage können gespeicherte Konfigurationen und zugehörige Metafelder entfernt werden; Löschanfragen bitte über den Support stellen.

## Deine Pflichten (Händler:innen)

- Stelle sicher, dass du eine Rechtsgrundlage für die Verarbeitung personenbezogener Daten hast (z. B. Einwilligung, Vertrag, berechtigtes Interesse).  
- Vermeide, sensible personenbezogene Daten über Kampagnenparameter oder Auslöser zu senden.  
- Aktualisiere diese Erklärung so, dass sie deine eigenen Datenflüsse, Anbieter und geltenden Vorschriften widerspiegelt (DSGVO, CCPA).

## Rechte

- Wir unterstützen bei Auskunfts-, Berichtigungs- und Löschanfragen für die von uns kontrollierten Daten — vorbehaltlich Verifizierung.  
- Käufer:innen wenden sich zuerst an die Händler:in; Händler:innen können Anfragen an uns weiterleiten.

## Sicherheit

- Verschlüsselung bei der Übertragung (HTTPS/TLS) ist für Admin- und Storefront-Aufrufe erforderlich.  
- Prinzip der geringsten Rechte für Betreiberzugriffe; Zugriffe und Rabattänderungen werden regelmäßig auditiert.

## Brauchst du Hilfe?

Fragen zu Datenschutz oder Daten? Schreibe eine E-Mail an `support@example.com` mit deiner Shop-Domain und der betreffenden Kampagne/dem Auslöser.
