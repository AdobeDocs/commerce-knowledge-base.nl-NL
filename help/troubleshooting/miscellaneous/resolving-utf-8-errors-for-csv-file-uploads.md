---
title: UTF-8-fouten oplossen voor het uploaden van CSV-bestanden
description: Dit artikel bevat een oplossing voor het foutbericht "CSV-bestanden moeten UTF-8-codering gebruiken". Dit foutbericht betekent dat het bestand dat u wilt uploaden ongeldige tekens bevat, of tekens die niet zijn toegestaan. Hoewel UTF-8-codering [de meeste tekens] (https://www.fileformat.info/info/charset/UTF-8/list.htm) toestaat, zijn sommige niet compatibel met Magento BI.
exl-id: 88d8e0b8-152e-4a6d-bc44-3b285e0eb0c3
feature: Data Import/Export
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# UTF-8-fouten oplossen voor het uploaden van CSV-bestanden

Dit artikel bevat een oplossing voor het foutbericht &quot;CSV-bestanden moeten UTF-8-codering gebruiken&quot;. Dit foutbericht betekent dat het bestand dat u wilt uploaden ongeldige tekens bevat, of tekens die niet zijn toegestaan. Terwijl UTF-8 het coderen voor [ de meerderheid van karakters ](https://www.fileformat.info/info/charset/UTF-8/list.htm) toestaat, zijn sommige niet compatibel met Magento BI.

U moet de codering van het bestand wijzigen om het probleem op te lossen. Wanneer u het bestand opnieuw opslaat met de juiste codering, wordt het probleem meestal opgelost, maar u moet er rekening mee houden dat u tijdens het uitvoeren van dit proces mogelijk bepaalde gegevens kwijtraakt (de ongeldige tekens worden bijvoorbeeld verwijderd).

Wij adviseren gebruikend [ Sublime Tekst ](https://www.sublimetext.com/2) om het dossier te bewaren en te coderen.

1. Open het bestand in Microsoft Excel, Google Docs, Apple Numbers of uw programma.
1. Klik &#x200B; **Dossier** > **sparen als** &#x200B; &#x200B; en kies de &#x200B; &#x200B; **komma gescheiden waarden (.csv)** formaat om het dossier te bewaren.
1. Open het CSV-bestand in Sublime Text.
1. In Sublime Tekst, navigeer aan &#x200B; **Dossier** > **sparen met het Coderen** > **UTF-8 \* &#x200B;**. Hiermee slaat u het CSV-bestand op met UTF-8-codering.    ![ csv_file_UTF-8_sublime_3.2.2_magento_BI.png ](assets/csv_file_UTF-8_sublime_3.2.2_magento_BI.png)
1. [ upload de gegevens ](https://experienceleague.adobe.com/en/docs/commerce-business-intelligence/mbi/analyze/connecting/using-file-uploader) (in onze gebruikersgids) aan een nieuwe lijst in Magento BI.
