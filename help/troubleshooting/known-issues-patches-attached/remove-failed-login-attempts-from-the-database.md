---
title: Mislukte aanmeldingspogingen verwijderen uit de database
description: In dit artikel wordt uitgelegd hoe u bestaande aanmeldingsgegevens voor mislukte pogingen verwijdert uit de Adobe Commerce-database op locatie en Adobe Commerce in de cloud-infrastructuurdatabase. Voor versies 2.2.10+ en 2.3.3+, moet u slechts het manuscript in bijlage in werking stellen. Voor oudere versies 2.3.0-2.3.2-p2, moet u een flard toepassen om het registreren tegen te houden en het manuscript in werking te stellen in bijlage om reeds bestaande ontbroken login geloofsbrieven te verwijderen.
exl-id: 0d7e3674-3563-414f-86a2-297eb8104099
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 0%

---

# Mislukte aanmeldingspogingen verwijderen uit de database

>[!NOTE]
>
>Dit artikel is bijgewerkt op 13 april 2020 met een nieuw script met de naam DB\_CLEANUP\_SCRIPT\_v2. Gebruik het bijgevoegde DB\_CLEANUP\_SCRIPT\_v2-script om bestaande mislukte aanmeldgegevens in extra tabellen te wissen. U moet DB\_CLEANUP\_SCRIPT\_v2 gebruiken, zelfs als u eerder DB\_CLEANUP\_SCRIPT\_v1 in werking hebt gesteld om extra lijsten te helpen schoonmaken.

In dit artikel wordt uitgelegd hoe u bestaande aanmeldingsgegevens voor mislukte pogingen verwijdert uit de Adobe Commerce-database op locatie en Adobe Commerce in de cloud-infrastructuurdatabase. Voor versies 2.2.10+ en 2.3.3+, moet u slechts het manuscript in bijlage in werking stellen. Voor oudere versies 2.3.0-2.3.2-p2, moet u een flard toepassen om het registreren tegen te houden en het manuscript in werking te stellen in bijlage om reeds bestaande ontbroken login geloofsbrieven te verwijderen.

## **Betrokken producten en versies**

* Dit probleem betreft Magento Open Source, Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.2.x, 2.3.x en eerdere versies.
* Adobe Commerce 1.x-implementaties worden niet beïnvloed.

## Probleem

In 2019 werd een fout gemeld aan Adobe Commerce die mislukte aanmeldingspogingen toestond om te worden aangemeld bij een database in Adobe Commerce 2.3.x en 2.2.x. Adobe Commerce heeft in reactie hierop een oplossing voor dit probleem opgenomen in Adobe Commerce 2.3.3 en 2.2.10 (gepubliceerd in oktober 2019). Terwijl de moeilijke situatie voor die insect het registreren van ontbroken login pogingen ophield, kan de informatie die voorafgaand aan het bijwerken aan deze huidige versies wordt verzameld nog bestaan. Deze meest recente moeilijke situatie ontruimt de login pogingen informatie die eerder werd geregistreerd, als om het even welk.   CVE-2019-8118 wordt beschreven en bijgehouden in [Algemene kwetsbaarheden en blootstellingen](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-8118).

## Oplossing

Of u het bijgevoegde script en de patch moet gebruiken, of alleen het script, is afhankelijk van uw versie van Adobe Commerce:

**Adobe Commerce en Magento Open Source versies 2.3.0-2.3.2-p2**

Voor deze versies moet u het flard toepassen en het in bijlage gegevensbestand schoonmaakmanuscript in werking stellen om het verdere registreren te beëindigen en logboeken te elimineren.

1. Voer de componentpatch uit om het loggen te stoppen. Deze patch is gekoppeld aan het artikel. Als u het bestand wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op de volgende koppeling [CLEANUP\_PATCH\_COMPOSER\_2.3.2.patch](assets/CLEANUP_PATCH_COMPOSER_2.3.2.patch.zip). Voor instructies over het aanbrengen van de pleister, zie [Een door Adobe Commerce geleverde componentpatch toepassen](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze kennisbasis voor ondersteuning.

1. Voer nu het script uit om de database van de reeds bestaande mislukte aanmeldingspogingen op te schonen. Dit script is aan het artikel gekoppeld. Als u het bestand wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op de volgende koppeling [DB\_CLEANUP\_SCRIPT\_v2.php](assets/DB_CLEANUP_SCRIPT_v2.php.zip).

Raadpleeg de [**Het script uitvoeren**](/help/troubleshooting/known-issues-patches-attached/remove-failed-login-attempts-from-the-database.md#run_script) voor instructies.

**Adobe Commerce en Magento Open Source versie 2.3.3 en hoger/2.2.10 en hoger**<br>
Alleen voor deze versies: voer het onderstaande script uit om oude logbestanden te wissen (het logbestand werd eerder beëindigd voor deze versies via een correctie die in oktober 2019 werd uitgebracht). Dit script is aan het artikel gekoppeld. Als u het bestand wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op de volgende koppeling [DB\_CLEANUP\_SCRIPT\_v2.php](assets/DB_CLEANUP_SCRIPT_v2.php.zip).

Raadpleeg de [**Het script uitvoeren**](/help/troubleshooting/known-issues-patches-attached/remove-failed-login-attempts-from-the-database.md#run_script) voor instructies in onze kennisbasis voor ondersteuning.

**Het script uitvoeren**

Volg de onderstaande instructies om het script uit te voeren:

1. Put `DB_CLEANUP_SCRIPT_v2.php` in de hoofdmap van de installatie van Adobe Commerce of Magento Open Source (in dezelfde map als de toepassing die `app/bootstrap.php`).
1. Voer dit bevel in de terminal uit: `php DB_CLEANUP_SCRIPT_v2.php` en het zal beginnen het gegevensbestand schoonmaakproces.

Als er problemen optreden tijdens het uitvoeren van het script, [een ondersteuningsticket indienen](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) of stuur ons een e-mail naar [security@magento.com](mailto:security@magento.com).

**Bijgevoegde bestanden**

[CLEANUP\_PATCH\_COMPOSER\_2.3.2.patch](assets/CLEANUP_PATCH_COMPOSER_2.3.2.patch.zip)

[DB\_CLEANUP\_SCRIPT\_v2.php](assets/DB_CLEANUP_SCRIPT_v2.php.zip)
