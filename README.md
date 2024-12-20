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

Api´et kører lokalt på _localhost:8081_

**GUIDE TIL API I POSTMAN**
[<img src="https://run.pstmn.io/button.svg" alt="Run In Postman" style="width: 128px; height: 32px;">](https://app.getpostman.com/run-collection/31531123-53cdd16d-0945-4ee1-912a-c9f0495d8517?action=collection%2Ffork&source=rip_markdown&collection-url=entityId%3D31531123-53cdd16d-0945-4ee1-912a-c9f0495d8517%26entityType%3Dcollection%26workspaceId%3D9d7edd33-c0f5-4323-9ce8-65e8c71cebd3)

**AUTHORIZATION**
Alle Routes der har med oprettelse af tickets/events at gøre er beskyttet bag en token.
For at bruge denne token skal du sende den med i din header

```
"Authorization": "Bearer <TOKEN>"
```

## ROUTES

Api´et har følgende routes

#### USER MANAGEMENT

```
   POST - /sign-up (params: name, email, password, phone )
   POST - /sign-in (params: email, password )
   GET - /profile (params: none)
```

#### TICKET MANAGEMENT - Er alle protected routes. Dvs. du skal være logget ind

```
   POST - /create (params: title, date, location, time, image, description)
   PUT - /update/:id (params: title, date, location, time, image, description)
   GET - /getAll (params: none)
   GET - /getOne/:id (params: none)
   DELETE - /deleteAll (params: none)
   DELETE - /delete/:id (params: none)
```
