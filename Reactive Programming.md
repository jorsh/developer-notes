# REACTIVE PROGRAMMING

## What is Reactive Programming?

It is a Programming paradigm that works with **asynchronus data streams**
Data Streams can be created by many things

- UI Events
- Http Requests
- File Systems
- Array-like Objects
- Memory / Cache

## What is a **Stream**?

- It is a sequence of ongoing events ordered in time
- Emits a value, error and complete signal

## Observables

- Observables are used to watch these streams and emit functions when value, error or completed signal is returned
- Observables can be subscribed to by an observer
- Observables will constantly watch streams and will update accordingly
- We can interact with data streams as any regular array

## Reactive Extensions / ReactiveX

- A library for composing asynchronus programs by using observable sequences
- Provides a long list of operators which allow us to filter, select, transform, combine and compose observables
