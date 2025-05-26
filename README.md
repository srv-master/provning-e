# Prövning för E i webbserver

Du behöver visa att du kan

- Grunderna i programmering
- Lösa enkla problem med webbserverprogrammering
- Skapa en enkel webbserver som svara på förfrågningar
- Förstår hur en webbserver i MEPN-stacken är uppbyggd

## Uppgifter

1. Skapa en server och lyssna på port 3000

- Logga "Server uppe på :3000" när den startar

2. Hello

- Skapa rutt för /
- Logga "Hello på /" till konsolen
- Visa "Hello" i webbläsaren

3. Dudes

- Skapa rutt för /dudes
- Skapa en array med 3 namn.
- Skicka tillbaka alla namnen.
- Använd helst json.

4. Cheater

- Skapa rutt för /secret-level
- Logga "Cheater" i konsolen
- Skicka tillbaka till /

5. Target

- Skapa rutt för /target/name
- Använd ruttparameter för name så att det kan läsas
- Logga namnet till konsolen
- Visa "Target: Johan" i webbläsaren om /target/Johan

6. Count Me In

- Skapa en rutt för /sum/max
- Använd ruttparameter för max så att det kan användas
- Skapa en loop som räknar samman summan av alla tal fram till och med talet, ex /sum/4 skulle då vara 1+2+3+4
- Visa summan i webbläsaren

7. Pug Me Baby One More Time

- Skapa rutt för /stylish
- Aktivera stöd för Pug (på de sätt det krävs)
- Skapa vy stylish.pug
- Skapa en rubrik "Stylish" och en ordnad lista med länkar till respektive uppgift
- Se till att besökaren ser vyn

8. Kattunge!

- Lägg till det som behövs för att kunna visa statiska filer
- Testa genom att surfa till /kitten.webp så att bilden visas (alltså inte någon rutt)

9. Monsterdata

- Skapa rutten /api/monsters
- Skapa en array med monster
- Varje monster är ett objekt med egenskaperna name, size, damage och hp
- Lägg in tre monster med valfritt namn, antal hp, damage och size
- Skicka tillbaka till användaren som json

10. Monstersamlingen

- Skapa rutten /monsters
- Skapa en css-fil och skapa en klass för röd text, ex .red
- Återanvänd eller skapa en ny array med monster där varje monster är ett objekt med egenskaperna name, level, damage och hp och lägg in tre monster med valfritt namn, antal hp, damage och level
- Skapa en vy med en h1 "Monster!"
- Använd monsters-arrayen i vyn och loopa igenom den så att
  - name är en h2
  - name får klassen .red ifall level är 2 eller över (testa med ett av monstren)
  - level, damage och hp är punkter i en oordnad lista

## Cheat Sheet Webbserverprogrammering

### node

```javascript
npm init -y
npm install express pug morgan mongoose
npm install nodemon -g
```

### express

Middleware som du typ alltid vill använda

```javascript
app.use(express.urlencoded({ extended: false }));
app.use(morgan("dev"));
app.use(express.static("public")));
```

### Pug

Ställ in som renderingsmotor i Express

```javascript
app.set("view engine", "pug");
app.set("views", "./views");
```

Placering av vy-filer

```
/views/demo.pug
/views/notes/all.pug
/views/notes/new.pug
```

Rendera vy

```javascript
app.get("/", (req, res) => {
  res.render("demo", { namn: "Johan" });
});

app.get("/notes/new", (req, res) => {
  // kod för att hämta data till variabeln notes
  res.render("notes/new", { title: "Demo", notes: notes, numbers: [1, 2, 3] });
});
```

Taggar och attribut

```javascript
form(action="/demo", method="POST")
	label(for="name") Vad heter du?
input(type="text", id="name", name="name")

.parent
.child
p Lorem...
p Color...
.child
p Dolores ...
```

Utskrift av variabel som skickats in

```javascript
h1 Du heter #{name}!
h1= name
```

Tagg inline i text

```javascript
p Surfa till #[a(href="/cars/") alla bilar] och börja om.
p Surfa till #[a(href="https://www.expressen.se") Expressen] och läs något.
```

Loopar

```javascript
each number in numbers
p #{number}
```

Villkor

```javascript
if namn
	h1 Hej #{name}!
else
	h1 Vad heter du?
```
