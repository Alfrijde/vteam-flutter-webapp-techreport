# Flutter webb app och val av utvecklings port

Det här är en teknisk rapport för kursen Virtuellt team vid Blekinge tekniska högskola. 
Rapporten kommer gå igenom hur man kommer igång med Flutter som webb app och väljer port för utveckling av appen.

## Kort om Flutter

Flutter är ett UI Software development kit skapat av Google och släpptes 2018. Till skillnad måt andra UI ramverk 
tillhandahåller Flutter en egen renderings motor vilket gör att en app byggd med flutter kan enkelt användas på 
olika platformar utan ändringar i koden. En Flutter-app bygger på widgets, en widget bygger en komponent i UIn 
liknande komponenter i React.
Flutter-appar skrivs i Dart och har ett stort grundbibliotek för olika typer av widgets och funktioner för att kunna
bygga en snygg applikation på ett enkelt sätt.

### Cross platform

## Installation

Följ dessa [instruktioner från Flutter](https://docs.flutter.dev/get-started/install/linux/web), för att installera Flutter i din linuxmiljö. Välj alternativet för installation med VS Code.

### Innan du installerar

Skapa en mapp "development" i din hem-mapp för din användare i din linuxmiljö. Det underlättar senare steg i installeringsprocessen.

För att kunna köra utvecklingsmiljön behöver du ha Google Chrome installerat på din dator. Du behöver också installera tillägget "Dart Debug Extension" för att kunna köra din app i Chorme.

I VS Code installerar du exstentions för Flutter och Dart. 

## Starta ett Flutter-projekt

1. Starta VS Code via ubuntu/linuxterminal
2. Välj Commando palette eller tryck på ctrl+shift+p
3. Välj Flutter: New project
4. Du får flera olika appliaktioner att välja bland, jag rekommenderar "Application" eller "Empty Application". Application ger en hel app med testning och kommentarer, kommentarerna kan vara en bra hjälp på vägen. Vill du ha en mindre app och bara se att allt fungerr välj Empty Application.
5. Projektet startas i mappen du stod i när du öppnade VS Code.
6. Det kan ta en liten stund att starta projektet då det är många filer som ska skapas.
7. När allt är fördigt har du flera olika mappar och filer. Den viktigaste just nu är lib/main.dart. Där ligger all kod till din app.
8. Starta debug och välj Google Chrome bland Avaiable devices när du får frågan.
9. Debuggen tar också en stund att starta och flera portar kommer att öppnas. Du får ett meddelande om att din app hör öppnats i en autogenererad port via VS Code.
10. Öppna  ett fönster med rätt port och starta Dart Debug genom att trycka på iconen och välja "Open Devtools".
11. Nu ska du se en web app med en räknare som ökar i antal när du trycker på plus-knappen.
12. För att se att du kan uppdatera din app kan du prova byta färgtema i main.dart. Det som är speciellt med Flutter är att ändringarna i din app sker i realtid utan att du behöver ladda om sidan eller starta om debuggen. Prova byta färg några gånger och se hur appen byter utseende. 
13. Om det inte uppdateras som det ska kan du prova trycka på den lilla blixten, "Hot Reload", i debug menyn, då ska uppdateringen gå igenom.

## Välj port för utveckling

Varje gång flutter startar en debug session så används en ny autogenererad port. När man bara ska utveckla en ensam applikation är det inte något problem, men när kopplingar ska göras med backend eller andra system så är det bra att veta vilken port appen kommer öppnas på och att det är samma varje gång.

Det finns tre sätt att göra det här på som jag provade med olika resultat.

### Alt 1: Med en launch.json-fil

Det här alternativet fungerade inte för mig, men är bra att känna till om man vill kunna styra andra detaljer kring debugging eller hur appen startas. Mer information finns [här](https://dartcode.org/docs/launch-configuration/).

1. Under degugg-iconen i menyn längst till vänster finns en knapp "Create a launch.json-file".
2. Nu ska en ny mapp, ".vscode", dykt upp balnd dina filer, under den ligger "launch.json". Du kan se ett exempel i det här repot på hur det ser ut.
3. Under den första konfiguartionen lägger du till följande:
`"args": ["-d", "web-server", "--web-port", "8082" ]`
4. Det sista argumenet är den port du önskar att din app startar på och kan vara vilken port som helst som passar dig bäst.
5. Om du nu startar en debug session så ska appen starta på din valda port.

byt bild
![launchfilens utseende](/assets/launch-file.png)

### Alt 2: Inställning i VS Code

Den här inställningen fungerade för mig, men den gäller för alla flutter-appar som startas i VS Code. Så om du har flera flutter-projekt igång så kommer alla startas på samma port.

1. Gå in på "Inställningar/Settings" i VS Code.
2. Sök efter "Dart: Flutter Run Additional Args"
3. Skriv in `--web-port=8082` eller din önskade port i fältet.
4. Klicka på "Add item"
5. Starta en ny debugg session och appen startar på din valda port.
 
 ![Add item vyn](/assets/add-item.png)

 ### Alt 3: Kommando i terminalen

Du kan också starta en debug session i terminalen. Nackdelen är att du inte får upp debugkontrollpanelen där Hot reload-knappen finns utan måste köra alla kommandon fortsatt i terminalen. För att göra en Hot reload i terminalen används kommandot "r" eller "R". Fördelen är att du kan byta åprt när du vill utan att behöva göra några inställningar. Det här allternativet fungerar också bra om appen ska öppnas via ett script eller liknande. 

1. Öpnna en terminal och gå till mappen där ditt flutter-projekt finns. 
2. Skriv in förkjande kommand o med den port du vill använda 
`flutter run -d web-server --web-port 8082`
3. Nu startas en debug session på den port du angav.

För mig fungerade inte Hot reload som det skulle när jag staratde appen via terminalen utan jag var tvungen att ladda om möntsret där appen var. Det är något som Flutter har varnat för när man gör webapplikationer att just Hot relaod inte alltid funkar på det sätt som det gör mas andra typer av appar.

## Reflektioner

Flutter är främst utvecklat för att köras som native appar men har blivit bättre att även använda som webbapplikationer både för stor och liten skärm. Det var spännande att se att de olika lösningarna gav olika resulatat och hade olika för- och nackdelar. Jag kommer att använda alternativ 2 så länge och göra några till försök att få till launch-file. Det borde vara det bästa sättet när det väl funkar. 


 

## Källor

- [Flutter on the web](https://flutter.dev/multi-platform/web)
- [Launch configaration for Dart/Flutter](https://dartcode.org/docs/launch-configuration/)
- [Stackoverflow-post om att välja port för Flutter](https://stackoverflow.com/questions/58248277/how-to-specify-a-port-number-while-running-flutter-web)
- [Om Flutter på Wikipedia](https://en.wikipedia.org/wiki/Flutter_(software))
