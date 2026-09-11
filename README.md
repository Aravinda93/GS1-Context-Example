# GS1 Context Example

Test contexts for EPCIS 2.1 JSON-LD work. Nothing here is official GS1 material.

## Warning

The two `GS1-WebVoc-context-*` files are **modified copies** of the GS1 Web
Vocabulary, changed on purpose so that protected terms can be tested. Do not use
them in production and do not treat them as GS1 publications. The official file
is at https://ref.gs1.org/voc/data/GS1-WebVoc-context.jsonld

## Files

| File | What it is |
|---|---|
| `GS1-WebVoc-context-UNPROTECTED.jsonld` | Web Vocabulary with every `@protected` key removed |
| `GS1-WebVoc-context-PROTECTED-FALSE.jsonld` | Web Vocabulary with `@protected` set to `false` |
| `epcis-context-UNPROTECTED-TEST.jsonld` | EPCIS 2.1 context referencing the first of those |
| `epcis-context-PROTECTED-FALSE-TEST.jsonld` | EPCIS 2.1 context referencing the second |
| `event-to-test.json` | Sample event. Replace the placeholder in `@context` with the URL you want to test |

Load them through jsDelivr, which serves `application/ld+json`:

https://cdn.jsdelivr.net/gh/Aravinda93/GS1-Context-Example@main/<file>

## What these show

An EPCIS event whose own `@context` declares a `geo` prefix, teste

| Context used | Result |
|---|---|
| Published EPCIS 2.1 | Error: "tried to redefine a protected term
| `@protected` removed | Loads, but `geo:22.300,-118.44` silently becomes `http://www.w3.org/2003/01/geo/wgs84_pos#22.300,-118.44` |
| `@protected: false` written | Error: "Cyclical context definition detected" |

Measured with jsonld.js, the engine behind the JSON-LD Playground.
