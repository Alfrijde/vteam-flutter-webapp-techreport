# Teknisk rapport

Det här är en teknisk rapport för kursen Virtuell team vid Blekinge tekniska högskola. 
Rapporten kommer gå igenom hur man kommer igång med Flutter som webb app och väljer port för utveckling av appen.

## Kort om Flutter

Flutter är ett Ui Software development kit skapat av Google och släpptes 2018. Till skillnad måt andra UI ramverk 
tillhandahåller Flutter en egen renderings motor vilket gör att en app byggd med flutter kan enkelt användas på 
olika platformar untan ändringar i koden. En Flutter-app bygger på widgets, en widget bygger en komponent i UIn 
liknande komponenter i React.
Flutter-appar skrivs i Dart och har ett stort grundbibliotek för olika typer av widgets och funktioner för att kunna
bygga en snygg applikation på ett enkelt sätt.

## Installation

Följ dessa [instruktioner från Flutter](https://docs.flutter.dev/get-started/install/linux/web), för att installera Flutter i din linuxmiljö. Välj alternativet för installation med VS Code.

### Innan du installerar

Skapa en mapp "development" i din hem-mapp för din användare i din linuxmiljö. Det underlättar senare steg i installeringsprocessen.

För att kunna köra utvecklingsmiljön behöver du ha Google Chrome installerat på din dator. Du behöver också installera tillägget Dart Debug Extension för att kunna köra din app i Chorme.
I VS Code installerar du exstentions för Flutter och Dart. 

## Starta ett Flutter-projekt

- Starta VS Code via ubuntu/linuxterminal
- Välj Commando palette eller tryck på ctrl+shift+p
- Välj Flutter: New project
- Du får flera olika appliaktioner att välja bland, jag rekommenderar "Application" eller "Empty Application". Application ger en hel app med testning och kommentarer, kommentarerna kan vara en bra hjälp på vägen. Vill du ha en mindre app och bara se att allt fungerr välj Empty Application.
- Projektet startas i mappen du stod i när du öppnade VS Code.
- Det kan ta en liten stund att starta projektet då det är många filer som ska skapas.
- När allt är fördigt har du flera olika mappar och filer. Den viktigaste just nu är lib/main.dart. Där ligger all kod till din app.
- Starta debug och välj Google Chrome bland Avaiable devices när du får frågan.
- Debuggen tar också en stund att starta och flera portar kommer att öppnas. Du får ett meddelande om att din app hör öppnats i en autogenererad port via VS Code.
- Öppna  ett fönster med rätt port och starta Dart Debug genom att trycka på iconen och välja "Open Devtools".
- Nu ska du se en web app med en räknare som ökar i antal när du trycker på plus-knappen.
- För att se att du kan uppdatera din app kan du prova byta färgtema i main.dart. Det som är speciellt med Flutter är att ändringarna i din app sker i realtid utan att du behöver ladda om sidan eller starta om debuggen. Prova byta färg några gånger och se hur appen byter utseende. 
- Om det inte uppdateras som det ska kan du prova trycka på den lilla blixten, "Hot Reload", i debug menyn, då ska uppdateringen gå igenom.

## Välj port för utveckling

Varje gång flutter startar en debug session så används en ny autogenererad port. När man bara ska utveckla en ensam applikation är det inte något problem, men när kopplingar ska göras med backend eller andra system så är det bra att veta vilken port appen kommer öppnas på och att det är samma varje gång.

Det finns två sätt att göra det här på som jag provade, varav ett fungerade för mig.

### Alt 1: Med en launch.json-fil

Det här alternativet fungerade inte för mig, men är bra att känna till om man vill kunna styra andra detaljer kring debugging eller hur appen startas. Mer information finns [här](https://dartcode.org/docs/launch-configuration/).

- Under degugg-iconen i menyn längst till vänster finns en knapp "Create a launch.json-file".
- Nu ska en ny mapp, ".vscode", dykt upp balnd dina filer, under den ligger "launch.json". Du kan se ett exempel i det här repot på hur det ser ut.
- Under den första konfiguartionen lägger du till följande:
`"args": ["-d", "chrome", "--web-port", "8082" ]`
- Det sista argumenet är den port du önskar att din app startar på och kan vara vilken port som helst som passar dig bäst.
- Om du nu startar en debug session så ska appen starta på din valda port.

### Alt 2: Inställning i VS Code

Den här inställningen fungerade för mig, men den gäller för alla flutter-appar som startas i VS Code. Så om du har flera flutter-projekt igång så kommer alla startas på samma port.

- Gå in på "Inställningar/Settings" i VS Code.
- Sök efter "Dart: Flutter Run Additional Args"
- Skriv in `--web-port=8082` eller din ösnkade port i fältet.
- Klicka på "Add item"
- Starat en ny debugg session och appen startar på din valda port


## Källor

- [Flutter on the web](https://flutter.dev/multi-platform/web)
- [Launch configaration for Dart/Flutter](https://dartcode.org/docs/launch-configuration/)
- [Stackoverflow-post om att välja port för Flutter](https://stackoverflow.com/questions/58248277/how-to-specify-a-port-number-while-running-flutter-web)
- [Om Flutter på Wikipedia](https://en.wikipedia.org/wiki/Flutter_(software))
