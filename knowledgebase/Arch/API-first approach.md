By this approach I mean that firstly API spec should be written, than - everything else.

## Workflows

For server:
1. Write/Update API spec
2. Generate types/schemes from spec
3. Write/Update code that handles added/changed API calls

For client:
1. Generate API client (client+types+schemes) from API spec
2. Update code to support changes is types/schemes

## Pros/Cons

Pros:
1. There is one source of truth, that describes contract between Server and Client
2. Types, generated from API spec, will help during coding
3. Schemes generated from API spec make runtime checking easier

Cons:
1. Another abstraction, One more dep in your project
2. Type and Schemes generators should be written additionaly (but only one time)

