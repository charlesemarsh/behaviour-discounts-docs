---
layout: default
title: Hilfe für Händler
nav_exclude: true
permalink: /de/help/
---

[English](/help/) · **Deutsch** · [Français](/fr/help/)

# Behaviour Discounts — Hilfe für Händler

Behaviour Discounts schaltet Rabatte hinter Magic Links und Verhaltensauslösern frei. Du als Händler:in steuerst, wann ein Rabatt greift, welches Cart-Attribut gesetzt wird und ob Gratisgeschenke automatisch hinzugefügt werden.

## Erste Schritte

- Die App installieren und die erforderlichen Berechtigungen akzeptieren.  
- Unter Online-Shop → App-Embeds das Theme-Embed von Behaviour Discounts aktivieren.  
- Den ersten Magic Link erstellen (Kampagnenparameter + Wert) und mit einem Rabatt verknüpfen.  
- Optional: Einen Verhaltensauslöser ergänzen (Produktansicht oder Verweildauer auf Seite/Website) inklusive Popup-Text.  
- In der Theme-Vorschau testen, bevor du live gehst.

## Wie es funktioniert

- Das Theme-App-Embed lädt `magic-link-handler.js` in deinem Storefront.  
- Es ruft aktive Konfigurationen von `/api/magic-links` und `/api/behaviour-triggers` ab.  
- Passt die aktuelle URL zum Parameter/Wert eines Magic Links, setzt es ein `magic_link_discount`-Cookie, spiegelt es in `sessionStorage` und schreibt `magic_link_campaign` vor dem Checkout in den Warenkorb.  
- Verhaltensauslöser setzen `behaviour_trigger_campaign` über die Popup-Bestätigung; sie werden unterdrückt, sobald ein Magic Link aktiv ist.  
- Enthält ein verknüpfter Rabatt Gratisprodukte, fügt der Handler die mit `_gift_campaign` getaggten Geschenkvarianten gemäß den Rabatteinstellungen automatisch hinzu.

## Theme-Embed einrichten (einmalig pro Theme)

1) Im Shopify-Admin zu **Online-Shop → Themes → Anpassen** gehen.  
2) **App-Embeds** öffnen und **Behaviour Discounts** aktivieren.  
3) Theme speichern. Das Skript lädt nun auf den Storefront-Seiten.

## Magic Links

- Lege ein erforderliches URL-Query-Paar fest (z. B. `?campaign=spring15`), das vorhanden sein muss.  
- Verknüpfe mit einem Shopify-Function-Rabatt (Produkt, Bestellung oder Versand), dessen Metadaten Vorteilstyp, Geschenke und Parameter enthalten.  
- Optionales Popup: Bestätigung der Kund:in einholen, bevor das Cart-Attribut gesetzt wird.  
- Teile die vollständige Kampagnen-URL in E-Mails/Anzeigen; beim Klick bleibt der Magic Link via Cookie/Session aktiv, bis er gelöscht wird oder abläuft.

### Bearbeiten oder deaktivieren

- Parameter/Wert, verknüpften Rabatt oder Popup-Text direkt in der App bearbeiten.  
- Eine Kampagne deaktivieren, um neue Aktivierungen zu stoppen; bestehende Cookies laufen nach ihrem normalen Plan ab.

## Verhaltensauslöser

- Regeltypen: Produktansicht, Verweildauer auf der Website, Verweildauer auf einer Seite.  
- Popup-Überschrift/-Text und den verknüpften Rabatt konfigurieren.  
- Die Bestätigung schreibt das `behaviour_trigger_campaign`-Cart-Attribut und fügt ggf. konfigurierte Geschenke hinzu.  
- Wenn ein Magic Link aktiv ist, bleiben Auslöser unterdrückt, um Stacking zu vermeiden.

## QR-Codes

- Erstelle gebrandete QR-Codes, die beim Scannen von Verpackungen, Flyern, In-Store-Displays oder Eventmaterialien einen Rabatt auslösen.
- Jeder QR-Code verlinkt mit einem Shopify-Function-Rabatt (gleiche Typen wie Magic Links: Produkt, Bestellung oder Versand).
- Wähle eine Zielseite (Startseite, Produkt, Kollektion, Warenkorb oder ein benutzerdefinierter Pfad). Der `qr`-Parameter wird automatisch angehängt.
- Passe das Erscheinungsbild des QR-Codes an: Vorder-/Hintergrundfarbe, Eckenstil (eckig oder abgerundet), zentrales Logo sowie optional ein Rahmen mit Call-to-Action-Label.
- Optionales Popup: Eine gebrandete Nachricht anzeigen, wenn die Kundin oder der Kunde nach dem Scannen in deinem Shop landet.
- Optionale Kurz-URL: Erstelle eine Vanity-Weiterleitung (z. B. `/go/scan`), damit der Link gedruckt oder neben dem QR-Code geteilt werden kann.
- QR-Codes haben dieselbe Priorität wie Magic Links — ist einer aktiv, werden Verhaltensauslöser unterdrückt.

### Bearbeiten oder deaktivieren

- Ziel, Rabatt, Popup, QR-Design oder Kurz-URL direkt in der App bearbeiten.
- Eine Kampagne pausieren, um neue Aktivierungen zu stoppen und Statistiken zu behalten. Beim Löschen werden QR-Code, Shopify-Rabatt und ggf. die URL-Weiterleitung entfernt.

## Gratisgeschenke / Gratisprodukte

- Rabatte können Geschenkvarianten enthalten, die mit `_gift_campaign` getaggt sind.  
- Modi: **auto** (Geschenk wird automatisch hinzugefügt), **manual** (Kund:in fügt selbst hinzu) oder **manualPopup** (Hinzufügen nach Popup-Bestätigung).  
- `autoAddGiftCount` steuert, wie viele Geschenke pro Kampagne hinzugefügt werden.

## Priorität

- Magic Links und QR-Codes haben dieselbe Priorität: Ist eine der beiden aktiv, werden Popups und Aktionen von Verhaltensauslösern unterdrückt, sodass nur der Magic-Link- oder QR-Code-Rabatt greift.

## Test-Checkliste

- In einer Theme-Vorschau eine Kampagnen-URL mit dem erwarteten Query-Parameter/Wert laden und das Popup (falls aktiviert) sowie den Rabattstatus prüfen.
- Browser-Storage prüfen: `magic_link_discount`-Cookie und die sessionStorage-Spiegelung sind vorhanden.
- Artikel in den Warenkorb legen; sicherstellen, dass das Cart-Attribut (`magic_link_campaign` oder `behaviour_trigger_campaign`) vor dem Checkout geschrieben wird.
- Bei Gratisgeschenken: bestätigen, dass die richtigen Varianten automatisch hinzugefügt und wieder entfernt werden, wenn der Rabatt deaktiviert wird.
- Eine Verhaltensregel auslösen (Produktansicht oder Zeitschwelle) ohne Magic Link; Popup und Cart-Attribut bestätigen.
- Sicherstellen, dass Auslöser unterdrückt bleiben, wenn ein Magic Link oder QR-Code aktiv ist.
- Bei QR-Codes: den generierten Code mit einem Handy scannen und bestätigen, dass er zum richtigen Ziel mit angewendetem Rabatt weiterleitet.
- Falls eine Kurz-URL konfiguriert ist, im Browser besuchen und bestätigen, dass sie korrekt weiterleitet.
- Den **Vorschau-Button für Tests** bei QR-Codes und Magic Links nutzen, um das Popup zu erzwingen, ohne dass die Kampagne aktiv sein muss.
- Einen Test-Checkout abschließen und prüfen, dass der richtige Rabatt bzw. das richtige Geschenk erscheint.

## Fehlerbehebung

- **Kein Popup oder Rabatt:** Prüfen, ob das Theme-Embed aktiviert und veröffentlicht ist.
- **Parameter passt nicht:** Sicherstellen, dass die geteilte URL das exakte Query-Paar enthält und der Magic Link aktiv ist.
- **QR-Code funktioniert nicht:** Status des QR-Codes prüfen — muss „Aktiv" sein, nicht „Entwurf" oder „Pausiert". Code scannen und prüfen, ob die Ziel-URL den `?qr=`-Parameter enthält.
- **Kurz-URL leitet nicht weiter:** Bestätigen, dass die Weiterleitung erfolgreich erstellt wurde (auf Warnungen beim Speichern achten). Kann auch im Shopify-Admin unter Einstellungen → Navigation überprüft werden.
- **Kurz-URL-Pfad bereits vergeben:** Jeder Pfad muss im gesamten Shop eindeutig sein. Wähle einen anderen Pfad oder entferne die bestehende Weiterleitung unter Einstellungen → Navigation.
- **Geschenke werden nicht hinzugefügt:** Bestätigen, dass die Geschenkvariante mit `_gift_campaign` getaggt ist und der Rabatt-Vorteil auf „Gratisprodukte" mit dem richtigen `autoAddGiftCount` gesetzt ist.
- **Cart-Attribut fehlt:** Prüfen, ob die Kund:in das Popup (falls erforderlich) bestätigt hat und ob der Warenkorb nicht von anderen Skripten blockiert wird.
- **Auslöser feuern immer:** Sicherstellen, dass kein Magic Link oder QR-Code aus einer vorherigen Sitzung aktiv ist; Cookies/Session löschen oder ein Inkognito-Fenster verwenden.

## FAQ

- **Welche Rabatttypen werden unterstützt?** Produkt (Prozent/Festbetrag/Geschenk), Bestellung (Prozent/Festbetrag mit optionalem Mindestbestellwert/-menge) und Versand (Prozent/Festbetrag/Gratis) — alle betrieben durch Shopify Functions.
- **Kann ich Stacking verhindern?** Ja. Magic Links und QR-Codes unterdrücken Verhaltensauslöser; innerhalb des Rabatts werden Stacking-Regeln durch die Function-Konfiguration durchgesetzt.
- **Wo bearbeite ich den Popup-Text?** In den Einstellungen des Magic Links, QR-Codes oder Verhaltensauslösers für jede Kampagne.
- **Wie werden Rabatte konfiguriert?** Metadaten (Vorteilstyp, Geschenke, Parameter/Wert) werden im Function-Konfigurations-Metafeld gespeichert und zur Laufzeit gelesen.
- **Was ist der Unterschied zwischen einem Magic Link und einem QR-Code?** Magic Links verwenden einen anpassbaren Query-Parameter (z. B. `?ref=summer`) und sind für digitales Teilen gedacht. QR-Codes verwenden immer den `qr`-Parameter mit einem automatisch generierten Wert und enthalten ein scanbares QR-Bild für Druck und physische Medien. Beide unterstützen dieselben Rabatttypen, Popups und Kurz-URLs.
- **Kann ich denselben Kurz-URL-Pfad für einen Magic Link und einen QR-Code verwenden?** Nein. Kurz-URL-Pfade müssen im gesamten Shop eindeutig sein — unabhängig davon, ob sie zu einem Magic Link oder QR-Code gehören.
- **Kann ich „qr" als Parameter-Namen für einen Magic Link verwenden?** Nein. Der Parametername `qr` ist für QR-Codes reserviert. Wähle einen anderen Namen für deine Magic Links (z. B. `ref`, `promo`, `campaign`).
- **Was passiert, wenn ich einen QR-Code oder Magic Link mit einer Kurz-URL lösche?** Die Shopify-URL-Weiterleitung wird automatisch zusammen mit der Kampagne und dem zugehörigen Rabatt gelöscht.
- **Kann ich einen QR-Code pausieren, ohne ihn zu löschen?** Ja. Beim Pausieren stoppt die Rabattgewährung — deine Statistiken und die Konfiguration bleiben erhalten. Du kannst ihn später wieder aktivieren.

## Brauchst du Hilfe?

Schreibe eine E-Mail an `support@example.com` mit deiner Shop-Domain, der Kampagnen-URL und einer kurzen Beschreibung, was du erwartet vs. gesehen hast.
