# RESTful

> RESTful vs RPC == Resources vs Operations == CRUD auf Resourcen (Entities) vs Methoden/Processes calls

## Methods
**POST** (Create)
* Execute once
* Wird auch für Commands verwendet oder GETS die einen Body mitschicken müssen (z.b.: eine Liste von Ids die zu lange für die URL werden kann)
* Hat Body
* Response
    * 201 => Created (mit Location Attribute)

**GET** (Read)
* Response
    * 200 => OK mit Body

**PUT**
* Update (idempotent => execute multiple times)
* Hat Body
* Response
    * 204 => NoContent
      => Wir müssen meistens auch das UI patchen (da(her) no content)

**PATCH**
* Update Single Properties (idempotent => execute multiple times)
* Hat Body
* Response
    * 204 => NoContent
      => Wir müssen meistens auch das UI patchen (da(her) no content)

**DELETE**
* Delete (idempotent => execute multiple times)
* Response
    * 204 => NoContent
      => Wir müssen meistens auch das UI patchen (da(her) no content)
    * 400 => Verschlucken => 204
    * 404 => Verschlucken => 204

**OPTIONS**
* Darf ich die Operation ausführen, resp. gibt es einen Endpoint dafür?

## StatusCodes
* 2xx => Success
* 4xx => Client error => Aufrufer (Client) kann dur Anpassung des Request ein anderes Resultat erhalten
* 500 => InternalServerError => nur bei Programmierfehler, es wird nie von uns explizit zurückgegeben

## Idempotent
> A request method is considered "idempotent" if the intended effect on the server of multiple identical requests with that method is the same as the effect for a single such request.

The HTTP specification states that following methods __must be idempotent__.

* GET
* PUT
* DELETE

But following methods are __not guaranteed to be idempotent__.

* POST