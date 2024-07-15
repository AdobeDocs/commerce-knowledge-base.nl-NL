---
title: Hoe een door Adobe geleverde componentpleister aanbrengen
description: In dit artikel wordt uitgelegd hoe u een composer-patch kunt toepassen voor Adobe Commerce op locatie, Adobe Commerce op cloudinfrastructuur en Magento Open Source.
exl-id: a9301ad8-1d4b-49f5-b679-758624928219
feature: Cache
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# Hoe een door Adobe geleverde componentpleister aanbrengen

In dit artikel wordt uitgelegd hoe u een composer-patch kunt toepassen voor Adobe Commerce op locatie, Adobe Commerce op cloudinfrastructuur en Magento Open Source.

>[!WARNING]
>
>We raden u ten zeerste aan de patch toe te passen en te testen in de omgeving Staging/Integration voordat deze op Production wordt toegepast. We raden u ook aan een recente back-up te maken voordat u wijzigingen aanbrengt.

## Een componentpatch voor Adobe Commerce toepassen op cloudinfrastructuur {#cloud}

1. Als u geen map hebt met de naam `m2-hotfixes` in de hoofdmap van het project, maakt u een map.
1. Kopieer het bestand of de bestanden `%patch_name%.composer.patch` naar de map `m2-hotfixes` .
1. De wijzigingen in de code toevoegen, doorvoeren en doorvoeren:

   ```git
   git add -A
   ```

   ```git
   git commit -m "Apply %patch_name%.composer.patch patch"
   ```

   ```git
   git push origin
   ```

Voor extra informatie over het toepassen van flarden op de projecten van de Wolk, zie [ flarden ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toepassen.

### Een componentpatch voor Adobe Commerce op locatie en Magento Open Source toepassen {#commerce}

1. Upload de patch naar uw Adobe Commerce-hoofdmap op locatie of in de hoofdmap van de Magento Open Source.
1. Voer de volgende SSH-opdracht uit:

   ```bash
   patch -p1 < %patch_name%.composer.patch
   ```

   (Gebruik `-p2` in plaats van `-p1` als de bovenstaande opdracht niet werkt.)

1. Voor de veranderingen die moeten worden weerspiegeld, vernieuw het geheime voorgeheugen in Admin onder **Systeem** > **het Beheer van het Geheime voorgeheugen**.
