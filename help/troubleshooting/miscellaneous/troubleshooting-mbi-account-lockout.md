---
title: Problemen met vergrendeling van Adobe Commerce Intelligence-account oplossen
description: Dit artikel biedt oplossingen voor het vergrendelen van Adobe Commerce Intelligence-accounts. We zullen eerst moeten bepalen of dit een fout is, een tijdelijke glitch, of iets anders. Volg de onderstaande stappen om u zo snel mogelijk weer in uw account te krijgen.
exl-id: 85968257-ba4b-4cfb-a4fa-497b4c5b5aea
feature: Cache, Commerce Intelligence, Console
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%

---

# Problemen met vergrendeling van Adobe Commerce Intelligence-account oplossen

<!--
BOB: Is this in TOC?
-->

Dit artikel biedt oplossingen voor het vergrendelen van Commerce Intelligence-accounts. We zullen eerst moeten bepalen of dit een fout is, een tijdelijke glitch, of iets anders. Volg de onderstaande stappen om u zo snel mogelijk weer in uw account te krijgen.

## Verifieer uw e-mailadres correct is

Controleer uw e-mailadres om te controleren of het e-mailadres dat u wilt gebruiken om u aan te melden, aan een bestaande Commerce Intelligence-account is gekoppeld. Mogelijk moet u een accountbeheerder vragen om te bevestigen dat het e-mailadres geen typos bevat.

Zodra u hebt bevestigd dat het e-mailadres correct is, probeer opnieuw login gebruikend [ deze verbinding ](https://dashboard.rjmetrics.com/v2/session/create#/).

## Probeer het wachtwoord opnieuw in te stellen

Als u hebt geverifieerd dat u de juiste e-mail gebruikt, probeert u het wachtwoord opnieuw in te stellen. U kunt **gebruiken vergeten?** op de aanmeldingspagina van de vorige sectie om een e-mail voor het opnieuw instellen van wachtwoorden te activeren.

Als u het e-mailbericht in het begin niet ziet, moet u wel naar de map junk email kijken. Soms kunnen zelfs goedbedoelde e-mails worden verward met junk. **Merk op dat de tijdelijke toegangsverbindingen in deze e-mails slechts één keer goed zijn!**

Als u nog steeds vergrendeld bent, controleert u of uw e-mailadres juist is en gebruikt u de juiste koppeling in het e-mailbericht voor opnieuw instellen. Wij adviseren het proberen van het volgende **alvorens u om een andere terugstellen verzoekt en opnieuw probeert aan login:**

* De cache, cookies en opgeslagen wachtwoorden van uw browser wissen
* Schakel tijdelijk alle ad-blokkerende software uit

## Eventuele fouten documenteren en uitreiken voor ondersteuning

>[!NOTE]
>
>Deze stap wordt niet altijd vereist, maar proactief het voltooien van het kon de tijd verminderen die heen en weer aan een steunverzoek wordt doorgebracht.

Als u nog steeds geen toegang hebt tot uw account, raden we u aan te controleren op fouten en een ticket naar ons ondersteuningsteam te verzenden. Hoe kan je dit doen? Door de de ontwikkelaarshulpmiddelen van uw browser te openen en een het schermschot te nemen van om het even welke die fouten in de console, of venster van het plaatslogboek worden getoond. In het onderstaande GIF open ik de tools voor ontwikkelaars voor Google Chrome:

![ het Openen van Chrome ontwikkelaarshulpmiddelen.](assets/Opening_Chrome_dev_tools.gif)

In het bovenstaande voorbeeld, gebruikten wij de gemeenschappelijkste methode (**klik** met de rechtermuisknop aan > **Inspect**) om de console te openen. Als uw browser deze methode niet heeft of u hulp nodig hebt, gebruik de documentatiekoppelingen hieronder voor Webbrowser u gebruikt:

<table>
<tbody>
<tr>
<td><a href="https://www.technipages.com/mac-os-x-enable-web-inspector-in-safari">Safari</a></td>
<td><a href="https://developer.mozilla.org/en-US/docs/Tools/Web_Console/Opening_the_Web_Console">Firefox</a></td>
<td><a href="https://developers.google.com/web/tools/chrome-devtools/?hl=en">Chrome</a></td>
<td><a href="https://www.opera.com/dragonfly/documentation/">Opera</a></td>
<td><a href="https://msdn.microsoft.com/en-us/library/gg589512(v=vs.85).aspx#OpeningTools">Internet Explorer</a></td>
</tr>
</tbody>
</table>

In sommige browsers wordt de console mogelijk niet automatisch weergegeven wanneer u de ontwikkelaarsgereedschappen opent. Het is mogelijk dat de sitecode eerst wordt weergegeven. Als dit voor u gebeurt, klikt u op de optie Console in het ontwikkelaarsvenster en maakt u schermafbeeldingen van eventuele fouten die daar worden weergegeven.

Verzend een kaartje aan ons team van de Steun met **foutenscreenshots** en het e-mailadres van uw **Commerce Intelligence rekening**.

## Ziet u geen fouten of u bent gewoon verdwaald?

Maak je geen zorgen! Een nieuw ondersteuningsticket indienen (neem het e-mailadres van uw Commerce Intelligence-account op) en we halen je zo snel mogelijk terug in je account.

## Verwante onderwerpen in onze basis van steunkennis:

* [ Toevoegend een nieuwe gebruiker en plaatsend toestemmingen ](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/administrator/user-mgmt/user-management.html?lang=nl-NL)
* [ Hoe werk ik mijn e-mailadres of wachtwoord bij?](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/administrator/user-mgmt/create-user.html?lang=nl-NL)
* [ hoe ik mijn wachtwoord terugstel?](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/administrator/user-mgmt/reset-password.html?lang=nl-NL)
