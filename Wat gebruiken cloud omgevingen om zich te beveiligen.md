# Welke methodes gebruiken Cloud omgevingen om zich te beveiligen?

## inleiding
Cloud omgevingen worden door veel consumenten en bedrijven gebruikt, deze omgevingen bevatten veel gevoelige data en gegevens van de klanten. Omdat er gevoelige data is zullen er altijd hackers op de loer liggen die de data willen stelen, veranderen of verwijderen. Hoe gaan Cloud omgevingen hier mee om en wat voor methodes gebruiken Cloud omgevingen om zich te beschermen tegen hackers?

## Inhoudsopgave
- Toegangsbeheer
- Versleuteling
- Netwerkbeveiliging
- Monitoring
- Fysieke beveiliging
- Back-ups en herstel

## Toegangsbeheer
Cloud providers proberen de klanten het zo moeilijk mogelijk te maken om eenvoudige inloggegevens te gebruiken, zo sporen ze aan sterke wachtwoorden te gebruiken. Ook wordt er gebruik gemaakt van 2-factor authentication, 2-factor authentication (2FA) is een beveiligingsmethode die extra bescherming biedt voor online accounts.  
<img src="https://github.com/BrucevandeVen/Cloud-Exploits/assets/58031089/ea9d793f-b233-43b0-b5dd-90f20a9c7cbc" width="600" alt="Image 3">  
Het vereist dat de gebruiker, naast het wachtwoord, een tweede vorm van verificatie gebruikt om toegang te krijgen tot je account. In plaats van alleen je wachtwoord in te voeren, ontvang je bijvoorbeeld een unieke code via een sms-bericht of een authenticatie-app op je telefoon. Deze code moet je vervolgens invoeren om te bewijzen dat je de eigenaar van het account bent. Door deze extra stap wordt het moeilijker voor hackers om toegang te krijgen tot je account, zelfs als ze je wachtwoord hebben bemachtigd. Het voegt een extra laag beveiliging toe door iets wat je weet (wachtwoord) te combineren met iets wat je hebt (bijvoorbeeld je telefoon) om je identiteit te verifiëren.  
Er zijn verschillende bedrijven die 2-factor authenticatie aanbieden, hieronder Microsoft en Google:  
<img src="https://github.com/BrucevandeVen/Cloud-Exploits/assets/58031089/8d67885c-a3f7-49a9-9a8c-1bae1361ba20" width="200" alt="Image 1">
<img src="https://github.com/BrucevandeVen/Cloud-Exploits/assets/58031089/f38ce718-4e7a-4f4b-9e8f-acb5ce41a1a4" width="200" alt="Image 2">

## Versleuteling
Cloud providers maken gebruik van data encryptie tijdens de transit of opslag er van. Tijdens de transit wordt er gebruik gemaakt van SSL/TLS protocollen om de data verborgen te houden voor onbevoegde lezers. In de [Microsoft Documentatie](https://learn.microsoft.com/en-us/azure/security/fundamentals/data-encryption-best-practices) wordt aangegeven dat de data in de Azure Storage automatisch geëncrypt wordt en het is mogelijk de Azure Key Vault te gebruiken om je sleutels te beheren die bij de geëncryptte data kunnen.

## Netwerkbeveiliging
Cloud providers maken gebruik van firewalls, netwerksegmentatie en VPN's om het verkeer te controleren en te beveiligen tussen verschillende services en gebruikers.  
![image](https://github.com/BrucevandeVen/Cloud-Exploits/assets/58031089/43381e89-ad8f-4ee1-97b4-79c210fed9c4)  
In de afbeelding is een voorbeeld architectuur van een Cloud omgeving gemaakt in Azure te zien die gebruik maakt van firewalls, netwerksegmentatie en VPN's.

## Monitoring
Het is mogelijk om de cloud omgeving te monitoren en dit doen de cloud providers ook bij hun eigen servers. Alle eerder genoemde beveiligingen zorgen er voor dat er anomaliteiten op kunnen treden die een indicatie kunnen geven of er door een hacker of een normale gebruiker in de cloud omgeving wordt gewerkt.  
Cloud omgevingen kunnen ook gebruikmaken van intrusion detection/prevention-systemen (IDS/IPS) en logboekregistratie voor het vastleggen van beveiligingsgebeurtenissen.

## Fysieke beveiliging
De servers van de Cloud omgevingen zijn goed beveiligd en garanderen een 99.99% up time garantie tegen betalinig (in ieder geval bij Azure). Volgens de [Microsoft Documentatie](https://learn.microsoft.com/en-us/compliance/assurance/assurance-datacenter-security) worden de servers goed beveiligd en er staan een aantal certificaten op die aan tonen dat de fysieke datacenters goed beveiligd zijn.  
Amazon heeft ongeveer dezelfde certificaten om aan te tonen dat de datacenters goed beveiligd zijn [AWS Security](https://aws.amazon.com/compliance/data-center/controls/)

## Back-Up & Herstel
Cloud providers bieden vaak mogelijkheden voor gegevensback-ups en herstel om te beschermen tegen gegevensverlies door onvoorziene omstandigheden, zoals hardwarestoringen of menselijke fouten. Hier hangt een prijskaartje aan. Er is meestal een optie om te kiezen voor "Global redundancy" of "Local redundancy", dit betekend dat het mogelijk is op meerdere datacenters over de hele wereld je data te dupliceren en daarna te herstellen of alleen in een lokaal datacenter. Global Redundancy geeft natuurlijk meer zekerheid op het niet verliezen van data omdat dit minder kwetsbaar is. 





