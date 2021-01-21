# Idempotent
> A request method is considered "idempotent" if the intended effect on the server of multiple identical requests with that method is the same as the effect for a single such request.

The HTTP specification states that following methods __must be idempotent__.

* GET
* PUT
* DELETE

But following methods are __not guaranteed to be idempotent__.

* POST
