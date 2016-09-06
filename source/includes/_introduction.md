# Introduction

<aside class="warning">
TODO LIST - BEGIN
</aside>

4. vanno passati al setaccio sia tutti gli attributi elencati in tabella, sia tutti i query params sia tutti gli esempi json di responses per vedere se sono congruenti con le apis
5. la get della lista degli stadi ritorna tutti gli stadi di tutte le pipelines se non viene specificato il query param pipeline_id.
6. sistemare wp negli stadi (valori di default). per i won/lost/abandoned mettiamo wp 100
7. nella creazione di deal e contatti o nella get. lo user id va specificato, quello dell'area no
8. controllare i query params della get di deal e contatti (non serve specificare lo user_id altrimenti ritorna tutti quelli che puoi vedere a seconda delle permission)
9. completare documentazione delle aziende

NOTE DI GIOVANNI:

ho visto che hai segnato un po’ di robe per la documentazione delle api
riguardo i query params, ti segnalo quelli che sono già implementati
https://github.com/Sellf/sellf-moon/blob/master/sellf/apis/public/v1/common/contacts.py#L15
per contatti e compagnie, ‘user_id’ e ‘name'
https://github.com/Sellf/sellf-moon/blob/master/sellf/apis/public/v1/common/deals.py#L29
pipeline ‘type' (monetaria o quantitativa)
https://github.com/Sellf/sellf-moon/blob/master/sellf/apis/public/v1/common/deals.py#L44
stadi ‘pipeline_id’ e ‘type' (il type è lo stage number)
https://github.com/Sellf/sellf-moon/blob/master/sellf/apis/public/v1/common/deals.py#L103
deals ‘user_id’, ‘stage_id’, ‘contact_id’, ‘company_id’, ‘source_id’, ‘product_id'
praticamente ogni sezione di un controllore in cui vedi una chiamata a request.query_params o cast_qparam (che lo casta direttamente a intero)
quindi per prendere gli stadi di una pipeline basta chiamare v1/stages?pipeline_id=123
per il sort invece come ti ho detto ieri vedi in cima ai controllori una serie di variabili allowed_sorts
https://github.com/Sellf/sellf-moon/blob/master/sellf/apis/public/v1/common/deals.py#L12
occhio che alcuni sono rimappati: per ordinare per estimated_value, che nelle api pubbliche non esiste, va fatto sort_by=-value
i campi serializzati sono tutti nei serializer: https://github.com/Sellf/sellf-moon/tree/master/sellf/apis/public/v1/serializers
quelli accettati sono tutti nei filters: https://github.com/Sellf/sellf-moon/tree/master/sellf/apis/public/v1/filters

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