# Contact Center

The common contact-center vocabulary -- the queues that hold waiting customers, the interactions routed through them, the skills that decide who takes them, the states agents are in and the dispositions recorded when they finish -- distilled from the APIs that already exist. Agents belong to the help-desk context and calls to telephony. Part of [Schema Commons](https://github.com/api-commons/schema-commons),
published by the [API Commons](https://apicommons.org).

Built from the providers tagged Contact Center, Call Center, CCaaS, Contact Center as a Service, Workforce Engagement, Customer Engagement in [APIs.io](https://apis.io) that
publish their own OpenAPI. Only harvested contracts count -- nothing API Evangelist
generated. Every number below is a count of providers.

## What the market already agrees on

<!-- commons:summary -->
| Concept | Expose it | Readable schema | Core properties (share) | Collection named |
| --- | ---: | ---: | --- | --- |
| queue | 10 | 10 | id 80%, name 80%, created_at 50% | queues 8, queue 2, call-queues 1, call_queues 1 |

Cohort: 93 providers with harvested OpenAPI, 10 crosswalks. Of the providers exposing a queue: 70% create, 90% list, 80% fetch, 70% update, 60% delete. Generated 2026-11-11 by build.py.
<!-- /commons:summary -->

Shares are of the providers with a readable resource schema for that concept. The
extended tier and the long tail of every concept are in [profile.yml](profile.yml).

## What the measurement shows

- Contact center is the thinnest context in the commons. Queues agree on id, name and created_at across ten CPaaS and business-phone providers; every other concept is exposed by three providers or fewer, and Genesys is the only platform that publishes all of them.
- The major contact-center platforms are largely absent: of Amazon Connect, Five9, NICE and Talkdesk, none has harvested OpenAPI in this cohort.

## Artifacts

- [openapi.yml](openapi.yml) -- OpenAPI 3.1 of the shared operations. No one serves it; it
  is the shape to map to. Lints clean against the
  [naming ruleset](https://github.com/api-commons/schema-commons/blob/main/ruleset/schema-commons-naming.yaml).
- [schema/](schema) -- JSON Schema 2020-12 per concept; each property carries
  `x-commons-tier`, `x-commons-share`, `x-commons-providers` and the spellings seen.
- [crosswalk/](crosswalk) -- one per provider, common name -> their name, with the harvested
  spec and operations each mapping was read from.
- [adopters.yml](adopters.yml) -- who exposes which concept, linked to their APIs.io page.
- [concepts.yml](concepts.yml) -- the only hand-written input: concepts, path segments and
  their qualifiers, aliases, reviewed exclusions, merged duplicates, and the decisions below.
- [census/](census) -- the cohort and the raw census the profile is built from.

## Decisions

These are calls, not measurements, recorded so they can be revisited as the method matures.

- Only queues are published. Interactions, skills, agent states and dispositions were measured and dropped: with Genesys the only full publisher, their 'common' shape would be one vendor's.
- Agents are the help-desk context's and calls telephony's; neither is duplicated.
- Call queues, hunt groups, ring groups and workgroups are queues.

## Rebuild

```bash
../schema-commons/scripts/run.sh .
```

## License

Artifacts CC BY-NC-SA 4.0 ([LICENSE](LICENSE)); code Apache 2.0 ([LICENSE-CODE](LICENSE-CODE)).
