---
title: Adobe Commerce Recommendations for PHP Vulnerabilities
description: Op 3 september heeft het Multi-State Information Sharing and Analysis Center (MS-ISAC) een waarschuwing gepubliceerd met betrekking tot meerdere kwetsbaarheden die het uitvoeren van willekeurige code mogelijk maken, en een aanbeveling dat alle sites die PHP gebruiken moeten bijwerken naar de nieuwste PHP versie ASAP ([hier is volledige waarschuwing beschikbaar](https://www.cisecurity.org/advisory/multiple-vulnerabilities-in-php-could-allow-for-arbitrary-code-execution_2019-087/)).
exl-id: 0bc7caab-0b89-463a-a7f2-a7c92df9f84e
feature: Compliance, Recommendations
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 0%

---

# Adobe Commerce Recommendations for PHP Vulnerabilities

Op 3 September, heeft het Meerstatelijke Informatie Delend en Centrum van de Analyse (MS-ISAC) een alarm met betrekking tot veelvoudige kwetsbaarheid uitgegeven die voor willekeurige codeuitvoering en een aanbeveling kon toestaan dat alle plaatsen die PHP gebruiken aan de recentste PHP versie ASAP zouden moeten bijwerken ([ volledig alarm is hier beschikbaar ](https://www.cisecurity.org/advisory/multiple-vulnerabilities-in-php-could-allow-for-arbitrary-code-execution_2019-087/)).

>[!WARNING]
>
>Op Adobe Commerce over cloudinfrastructuur dient u te weten dat serviceupgrades niet naar de productieomgeving kunnen worden doorgevoerd zonder dat ons infrastructuurteam hiervan 48 uur op de hoogte wordt gesteld. Dit is nodig omdat wij ervoor moeten zorgen dat wij een ingenieur van de infrastructuursteun beschikbaar hebben om uw configuratie binnen een gewenst tijdsbestek met minimale onderbreking aan uw productiemilieu bij te werken. Zo 48 uren voorafgaand aan wanneer uw veranderingen op productie moeten zijn [ een steunkaartje ](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) voorleggen detailend uw vereiste de dienstverbetering en het verklaren van de tijd wanneer u het verbeteringsproces wilt beginnen.

Lees verder voor effecten en stappen voor Adobe Commerce-sites:

**Adobe Commerce die op ons product van de Wolk wordt ontvangen**

Als u Adobe Commerce gebruikt voor cloudinfrastructuur, werkt u samen met uw technologieteam om Adobe Commerce op elk gewenst moment opnieuw te implementeren\* om te profiteren van de update. Wij adviseren dat Merchants deze herplaatsing tegen 30 september voltooien om PCI nalevingskwesties te vermijden die als gevolg van deze kwetsbaarheid aan het eind van de maand van kracht kunnen worden.

Aanvullende opmerkingen over het opnieuw implementeren van uw Cloud-site voor deze update:

* Als uw site nog steeds PHP versie 7.0 gebruikt, moet u eerst een upgrade uitvoeren naar een ondersteunde PHP versie voordat u de site opnieuw implementeert om te kunnen profiteren van deze beveiligingsupdates.
* Voor 2.1.x/2.2.x, kan meer informatie over bevordering PHP [ hier ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html?lang=nl-NL) worden gevonden.

\* *Vorige versies van dit artikel en ons overseinen verklaarde 19 September, maar onze teams hebben hun werk voorafgaand aan programma gebeëindigd.*

**Adobe Commerce op alle andere het ontvangen oplossingen**

Aangezien Adobe Commerce afhankelijk is van PHP, raden we aan dat alle verkopers die Adobe Commerce gebruiken de benodigde updates voor PHP doornemen met hun hostingprovider. Wij adviseren ook dat de verkopers deze controle en om het even welke updates tegen 30 september voltooien om PCI nalevingskwesties te vermijden die als resultaat van deze kwetsbaarheid aan het eind van de maand van kracht kunnen worden.

Houd rekening met enkele aanvullende gegevens voor Adobe Commerce over andere hostingoplossingen:

* Adobe Commerce versies 2.0 of 1.x die PHP versies gebruiken ouder dan 7.1 of hoger hebben geen officiële PHP patch beschikbaar. Het aanbevolen pad is om PHP bij te werken naar een ondersteunde PHP versie.

Tot de aanbevolen patches voor deze kwetsbaarheid behoren:

* PHP 7.1: [ https://www.php.net/ChangeLog-7.php\#7.1.32 ](https://www.php.net/ChangeLog-7.php#7.1.32)
* PHP 7.2: [ https://www.php.net/ChangeLog-7.php\#7.2.22 ](https://www.php.net/ChangeLog-7.php#7.2.22)
* PHP 7.3: [ https://www.php.net/ChangeLog-7.php\#7.3.9 ](https://www.php.net/ChangeLog-7.php#7.3.9)

Als u meer informatie over PHP en recente versies zou willen, kunt u [ PHP plaats ](https://www.php.net/) bezoeken. En als u vragen hebt of meer informatie over beste praktijken voor veiligheid zou willen, gelieve onze [ Gids van de Beste praktijken van de Veiligheid te controleren ](https://www.adobe.com/content/dam/cc/en/security/pdfs/Adobe-Magento-Commerce-Best-Practices-Guide.pdf).
