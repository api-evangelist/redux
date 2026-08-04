# Redux

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Redux is a predictable state container for JavaScript apps. It helps you write applications that behave consistently, run in different environments (client, server, and native), and are easy to test. The Redux ecosystem includes React Redux for React bindings, Redux Toolkit for simplified development, and Redux DevTools for time-travel debugging.

**Human URL:** [https://redux.js.org](https://redux.js.org)

**GitHub Organization:** [https://github.com/reduxjs](https://github.com/reduxjs)

## Tags

- State Management
- Javascript
- Frontend
- Predictable State
- Flux Architecture
- React
- Typescript

## APIs

### Redux Core API
Core Redux library providing createStore, combineReducers, applyMiddleware, compose, and bindActionCreators.

**URL:** [https://redux.js.org](https://redux.js.org)

- [Documentation](https://redux.js.org/introduction/getting-started)
- [API Reference](https://redux.js.org/api/api-reference)
- [GitHub Repository](https://github.com/reduxjs/redux)
- [npm Package](https://www.npmjs.com/package/redux)

### React Redux API
Official React bindings for Redux with hooks (useSelector, useDispatch) and Provider component.

**URL:** [https://react-redux.js.org](https://react-redux.js.org)

- [Documentation](https://react-redux.js.org/introduction/getting-started)
- [API Reference](https://react-redux.js.org/api/hooks)
- [GitHub Repository](https://github.com/reduxjs/react-redux)
- [npm Package](https://www.npmjs.com/package/react-redux)

### Redux Toolkit API
The official, batteries-included toolset with configureStore, createSlice, createAsyncThunk, and RTK Query.

**URL:** [https://redux-toolkit.js.org](https://redux-toolkit.js.org)

- [Documentation](https://redux-toolkit.js.org/introduction/getting-started)
- [API Reference](https://redux-toolkit.js.org/api/configureStore)
- [GitHub Repository](https://github.com/reduxjs/redux-toolkit)
- [npm Package](https://www.npmjs.com/package/@reduxjs/toolkit)
- [RTK Query](https://redux-toolkit.js.org/rtk-query/overview)

### Redux DevTools API
Developer tools for time-travel debugging and action/state inspection.

**URL:** [https://github.com/reduxjs/redux-devtools](https://github.com/reduxjs/redux-devtools)

- [Documentation](https://github.com/reduxjs/redux-devtools/blob/main/README.md)
- [GitHub Repository](https://github.com/reduxjs/redux-devtools)
- [Chrome Extension](https://chrome.google.com/webstore/detail/redux-devtools/lmhkpmbekcpmknklioeibfkpmmfibljd)
- [Firefox Extension](https://addons.mozilla.org/en-US/firefox/addon/reduxdevtools/)

### Redux Saga
Middleware for managing async side effects using ES6 Generators.

- [Documentation](https://redux-saga.js.org/docs/introduction/GettingStarted)
- [GitHub Repository](https://github.com/redux-saga/redux-saga)

### Redux Observable
RxJS-based middleware for composing async actions as observable streams.

- [Documentation](https://redux-observable.js.org/docs/basics/Epics.html)
- [GitHub Repository](https://github.com/redux-observable/redux-observable)

### Redux Thunk
Thunk middleware enabling action creators that return functions for async logic.

- [GitHub Repository](https://github.com/reduxjs/redux-thunk)

### Reselect
Memoized selector library for computing derived data from Redux state.

- [Documentation](https://reselect.js.org/)
- [GitHub Repository](https://github.com/reduxjs/reselect)

## Artifacts

### JSON Schema

| Schema | Description |
|--------|-------------|
| [Redux Store Schema](json-schema/redux-store-schema.json) | Schema for Redux store configuration and state tree |
| [Redux Action Schema](json-schema/redux-action-schema.json) | Flux Standard Action schema for Redux action objects |

### JSON Structure

| Structure | Description |
|-----------|-------------|
| [Redux Store Structure](json-structure/redux-store-structure.json) | Structural documentation for the Redux store API surface |

### JSON-LD

| Context | Description |
|---------|-------------|
| [Redux Context](json-ld/redux-context.jsonld) | JSON-LD context mapping Redux vocabulary to schema.org |

### Vocabulary

| Vocabulary | Description |
|------------|-------------|
| [Redux Vocabulary](vocabulary/redux-vocabulary.yml) | Normative vocabulary for Redux concepts, patterns, and terminology |

## Common Properties

- [Website](https://redux.js.org)
- [GitHub Organization](https://github.com/reduxjs)
- [Blog](https://blog.isquaredsoftware.com/)
- [Community](https://discord.gg/redux)
- [Twitter](https://twitter.com/reduxjs)
- [Stack Overflow](https://stackoverflow.com/questions/tagged/redux)
- [Style Guide](https://redux.js.org/style-guide/style-guide)
- [FAQ](https://redux.js.org/faq)
- [Tutorials](https://redux.js.org/tutorials/essentials/part-1-overview-concepts)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
