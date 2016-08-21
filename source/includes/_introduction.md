# Introduction

<aside class="warning">
TODO LIST - BEGIN
</aside>

1. al posto dei codici numerici usare etichette come ruolo utente (e.g. 0 diventa "administrator") e tipo di pipeline (e.g. 0 è "money") e tipo di stadio (e.g. 1 è "won")
2. i "products" sono in realtà i "margins" sia per esser congruenti con l'uso lato app sia perché i products se li introdurremmo in futuro sono una altra cosa
3. andrebbero rinominati i "contacts" in "people" perché propriamente i contatti sono sia persone che aziende (e infatti anche nelle app si chiamano cosi)
4. vanno passati al setaccio sia tutti gli attributi elencati in tabella, sia tutti i query params sia tutti gli esempi json di responses per vedere se sono congruenti con le apis
5. la get della lista degli stadi ritorna tutti gli stadi di tutte le pipelines? non vengono filtrati per pipeline? forse è meglio fare una call del tipo pipeline/:id/stages
6. sistemare wp negli stadi. per i won/lost/abandoned che wp mettiamo adesso? n/a?
7. nella creazione di deal e contatti o nella get, va specificato lo user id? e l'id dell'area?
8. controllare i query params della get di deal e contatti (serve il suid?)
9. completare documentazione delle aziende

<aside class="warning">
TODO LIST - END
</aside>

Welcome to the Sellf API! You can use our API to access Sellf API endpoints, which can get information on [contacts](#contacts) and [deals](#deals) in our database.


```ruby
# To have a response in JSON
Accept: application/json
```


```ruby
# To send a JSON request
Content-Type: application/json
```

We have language bindings in Shell ([cURL](https://en.wikipedia.org/wiki/CURL)). You can view code examples in the dark area to the right.

The API is organized around [REST](http://en.wikipedia.org/wiki/Representational_State_Transfer). All requests should be made over SSL. All request and response bodies, including errors, are encoded in [JSON](https://en.wikipedia.org/wiki/JSON). Please specify the `Accept` and `Content-Type` header as `application/json`.

The API dates are represented in UTC following the [ISO 8601](https://it.wikipedia.org/wiki/ISO_8601) industry-adopted standard.
Each entity has a unique integer ID.

<aside class="notice">
All API calls must be made to `https://api.sellf.io/v1`, where `v1` is the (current) version of the APIs.
</aside>

Please report any issues to <a href="mailto:support@sellfapp.com">support@sellfapp.com</a> or leave any feedback [here](https://sellf.uservoice.com).