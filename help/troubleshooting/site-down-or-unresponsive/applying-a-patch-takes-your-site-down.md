---
title: Als u een patch toepast, wordt uw site uitgeschakeld
description: In dit artikel wordt gesproken over het probleem waarbij een patch die u zojuist hebt aangebracht, uw site neerzet. U kunt de pleister verwijderen om deze op te lossen.
exl-id: dc765bcd-0761-4efd-a345-46a908d61272
feature: Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# Als u een patch toepast, wordt uw site uitgeschakeld

In dit artikel wordt gesproken over het probleem waarbij een patch die u zojuist hebt aangebracht, uw site neerzet. U kunt de pleister verwijderen om deze op te lossen.

## Betrokken producten en versies

* Adobe Commerce (alle implementatiemethoden), alle ondersteunde versies
* Magento Open Source, alle versies

## Probleem

Nadat u een patch hebt toegepast, gaat uw site omlaag.

## Oorzaak

Dit probleem kan ontstaan door een incompatibiliteit van de versie tussen de patch die u zojuist op uw website hebt toegepast, uw aanpassingen, andere patches die u in het verleden hebt toegepast of een andere fout.

## Oplossing

Verwijder de pleister. De methode voor het verwijderen van patches is anders voor Adobe Commerce op cloudinfrastructuur dan voor Adobe Commerce op locatie en Magento Open Source.

### Magento Open Source, alle 1.X versies

Voor Magento Open Source 1.X-versies:

* Voer de volgende SSH-opdracht uit: `h SUPEE_patch --revert `

### Adobe Commerce op locatie, Magento Open Source, alle 2.x-versies

Voor Adobe Commerce on-premisse en Magento Open Source 2.x versies,

1. Voer de volgende SSH-opdracht uit:

   ```
   patch -p1 -R %patch_name%.composer.patch
   ```

   (Als de bovenstaande opdracht niet werkt, probeert u `-p2` in plaats van `-p1` te gebruiken)

1. Voor de veranderingen die moeten worden weerspiegeld, vernieuw het geheime voorgeheugen in Admin onder **Systeem** > **het Beheer van het Geheime voorgeheugen**.

### Adobe Commerce op cloud-infrastructuur, alle versies

Voor Adobe Commerce op cloud-infrastructuur, alle versies,

1. Verwijder de `%patch_name%.composer.patch` bestanden uit de map `m2-hotfixes` .
1. Leg de wijzigingen in de code vast en duw erop:

   ```
   git commit -m "Remove %patch_name%.composer.patch patch" && git push origin
   ```

## Gerelateerde lezing

* [&#x200B; hoe te om een componentenflard toe te passen dat door Adobe &#x200B;](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze steunkennisbasis wordt verstrekt.
