# Coding tracker!

I denna övningen kommer du att bygga en `tracker` som kan hjälpa dig hålla koll på dina kodvanor, till exempel om du vill hålla reda på vad du spenderar tid på eller hur mycket du kodat under en viss period. Du kommer bygga ett API som har ett antal routes och funktionalitet.

Testa att bygga denna med Express, MVC-modellen och en SQL-databas - förslagsvis `sqlite3` (kanske i kombination med ett ORM som `knex`?).

Paket: `express`, `cors` och om du väljer att använda en databas `sqlite3` / `knex`.

Du kan testa dessa med hjälp av Insomnia, Postman eller annan HTTP REST-klient.

## Krav

- `POST /users` för att skapa en ny användare => Ska returnera `username` och `id`
- `GET /users` för att hämta en lista på användare => Ska returnera en array med objekt som innehåller `username` och `id`.
- `POST /users/:id/activity` skapar en ny aktivitet, med titel, tid och datum. (Skickas inget datum med ska den använda nuvarande datumet) => Ska returnera användar-objektet med alla dess aktiviteter.
- `GET /users/:id/logs` hämtar historiken på användarens aktiviteter => Ska returnera en array med objekt som innehåller `title`, `duration` och `date`.
- Lägg till from, to och limit-parametrar i query-stringen för att hämta bara en del av användarens log

Aktivitetens `title` ska vara en `sträng`, `duration` en int (i minuter) och `date` ett datum.
```js
// Aktivitet
{
  title: "Learned how to use express session",
  time: 60,
  date: "Wed Feb 23 1970", // eller liknande,
  id: "8h8h2tj0k?KFjg"
}
```

Användarens `username` ska vara en sträng.
```js
// Användare
{
  username: "potatoman",
  id: "98h2t190j+k1+0d"
}
```

En "logg" ska innehålla följande värden:
```js
// Log
{
  username: "potatoman",
  count: 1,
  id: "98h2t190j+k1+0d",
  activity_log: [
    {
      title: "Learned how to use express session",
      time: 60,
      date: "Wed Feb 23 1970", // eller liknande,
      id: "8h8h2tj0k?KFjg"
    }
  ]
}
```

## (optional) Frontend

Trots att det är en "backend"-kurs, så vill jag uppmuntra dig att skapa en tillhörande Frontend!

Jag har inkluderat en `frontend`-mapp med ett nytt Vite/React-projekt. Skapa en React-app som gör det möjligt för användaren att lägga till

## Extra

Vill du passa på att öva på querystrings bland annat? Testa att implementera följande funktionalitet:

### Querystrings

`GET /users/:id/logs?from=<date>&to=<date>&limit=<antal>`

- `from` hämtar användarens aktiviteter i en logg från det datumet du anger och framåt
- `to` hämtar användarens aktiviteter i en logg fram till datumet du angett
- `limit` är ett maxantal på hur många aktiviteter som ska skickas tillbaka

För att klara `from` och `to` behöver du hantera datum (lite klurigt, du kan ta hjälp av ex. `dayjs` för att lösa det). `limit` behöver du bara begränsa antalet resultat som skickas tillbaka i `activity_log`.

### Ta bort/ångra ett inlägg

Ifall användaren skulle mata in ett felaktigt värde och ångra sig, så är det bra ifall man har möjlighet att ta bort en `aktivitet`. Lägg till en route med funktionalitet som låter användaren ta bort en `aktivitet`.
