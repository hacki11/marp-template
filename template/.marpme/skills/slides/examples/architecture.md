# Architecture slide pattern

Use a takeaway title followed by a compact flow and no more than three supporting
notes.

````markdown
## One gateway keeps client integrations stable

```text
Client → API gateway → Domain service → Data store
             └──────→ Event stream
```

- The gateway owns authentication and version negotiation.
- Domain services own business rules.
- Events decouple downstream consumers from the request path.
````

Avoid generic titles such as “Architecture” when the slide can state the design
decision or consequence directly.
