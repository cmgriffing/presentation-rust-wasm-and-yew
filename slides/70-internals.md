# Internals

## web-sys OR stdweb

- web-sys <-> wasm-bindgen

- stdweb <-> cargo-web

## Debugging: Panics

`console_error_panic`: nicer stacktraces

- **not** compatible with **cargo-web**

## Debugging: console.log

`log`: rust standard crate just works

`ConsoleService`: Yew wrapper service

## Yewtil

- NeqAssign: shallow prop checks

- PureComponent: uses NeqAssign (memoized based on props)

- Lrc: linked list reference counted smart pointer

- Mrc/Irc: Mutable/Immutable reference counted smart pointers

- History: A history tracking wrapper that uses a `VecDeque`

## Undocumented

- Component lifecycle state machine

- VDOM diff algorithm
