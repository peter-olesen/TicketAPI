# TicketAPI

Ticket API er et api med brugerstyring og mulighed for at oprette, slette og ændre billetter som er bundet op til en bestemt bruger.
Dette API er lavet så du blot skal downloade det og sætte det op.

## Guide til installation

1. Start med at hente projektet ned. Herefter skal du navigere til roden og køre
   `npm install`

2. Opret en ny fil .env i roden og indsæt følgende:
   Bemærk at JWTSECRET er en unik kode du selv skal lave - indtast blot 64 tal og bogstaver eller brug en online JWT Secret generator.

   _Husk at indsætte USER, PASSWORD og DB, som kommer fra din database_

   _Bruger du en anden DB end MySQL skal DIALECT også tilrettes_

```
PORT=8081
JWT_REFRESH_EXPIRATION=30000000
JWT_EXPIRATION=1400000
JWT_SECRET=64_CIFRE_LANG_KODE_HER
HOST=localhost
USER=root
PASSWORD=DIT_ROOT_PASSWORD
DIALECT=mysql
DB=tickets
```

3. Åben dit foretrukne program til at styre din database og opret en ny database ved navn tickets

4. Nu skulle du kunne starte serveren ved at skrive i terminalen:
   `node server.js`

## Guide til API

Api´et har følgende routes
Alle Routes der har med oprettelse af tickets/events at gøre er beskyttet bag en token.
For at bruge denne token skal du sende den med i din header

```
"Authorization": "Bearer <TOKEN>"
```

#### USER MANAGEMENT

```
    - /sign-up (params: name, email, password, phone )
    - /sign-in (params: email, password )
    - /profile (params: none)
```

#### TICKET MANAGEMENT - Er alle protected routes. Dvs. du skal være logget ind

```
    - /create (params: title, date, location, time, image, description)
    - /update/:id (params: title, date, location, time, image, description)
    - /getAll (params: none)
    - /getOne/:id (params: none)
    - /deleteAll (params: none)
    - /delete/:id (params: none)
```
