# Grant Proposal: Subgraph Unit Testing Framework

The Graph Protocol needs a subgraph unit testing framework to ensure mapping logic is correct.

The framework must allow developers to test their mapping logic against a known store state and against test fixtures (events).

Assertions can be made using a snapshot-style approach.

## User Stories

### As a user I want to hydrate the store with a certain state

Users must be able to hydrate the store with a known state of entities. Ideally both:

- Hydrate state programmatically using Entity objects

### As a user I want to call a mapping function with an event

The user must be able to create an event Entity and pass it to a mapping function that is bound to the hydrated store.

### As a user I want to call all of the mappings with event fixtures

The user must be able to call the mappings with test fixtures.

- Fixtures could be set up programmatically as a list of Events

### As a user I want to mock contract calls

Users must be able to mock a contract call:

```
const mock = mockContract('0x...'):
mock.expects('myContractFunction').withArgs(a, b, c).shouldReturn(x)
```

Users must also be able to mock reverts:

```
mock.expects('myContractFunction').withArgs(a, b, c).once().reverts()
```

### As a user I want to assert the state of the store

The user should be able to assert the final state of the store in a snapshot-style approach (compare store state against expected).

- Must be able to assert entities
- Possibly assert entire state of store to assert non-existence as well

### As a user I want to assert a subgraph failure

The user should be able to assert that a subgraph fails in an expected way.

### As a user I want to see test run time durations

It could be useful to see how fast tests run.  The log output should include test run duration.

## Additional Requirements

### Language

The framework should be written in Rust.

- Unit tests themselves will be written in AssemblyScript and compiled to wasm.
- The framework will be used via CLI.

### Performance

The framework should be fast: it should not spin up nodes or child processes.  The framework must stub out the store and test the mappings.

### Test Coverage

The framework should be tested with coverage exceeding 90%

## Scope and Budget

N/A
