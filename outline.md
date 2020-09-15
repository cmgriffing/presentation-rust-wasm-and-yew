Intro

- Yew: what is it
- Yew: when? how old is the project? how active is the project?
- Yew: who? how many maintainers?

- Wasm: what is it
- Wasm: links and examples

Getting Started

- Project Setup: Manual
- Starter Templates: wasm-pack or parcel based
- Examples

Core Features

- html! macro: jsx-like `#![recursion_limit="1024"]`
- Components: lifecycle
- Agents: Like Angular Services
  - lifecycle
  - types
  - Bridges and Dispatchers
- Router
- Yew Services: Wrappers around web_sys or stdweb based on config
  - Storage (Local and Session)
  - Fetch
  - RenderService (rAF)
  - Interval/Timeout
  - and more

Example goes here

- Cellule Life (personal project)
- point out dev vs release.
- mention why my dev mode is so slow (dev is not slow by default)

Internals

- Rust Libs:
  - web-sys OR stdweb
  - web-sys, js-sys, etc
- Undocumented: Component-lifecycle state machine, vdom diff algorithm.
- Debugging
- Yewtil

Optimizations

- Runtime Optimizations
  - neq_assign
  - RC, for properties that take a lot of ram
  - Unsupported natively: Pure or Function Components
- Build Optimizations:
  - Rust: wee-alloc and release profile
  - wasm: wasm-opt
- Compile Optimization: Cargo Workspaces

  - Compile time seems to correlate with the quantity of code found within html! macro blocks
  - it makes sense to break apart your code across multiple crates to minimize the amount of work the compiler has to do for each change made.

  - make your main crate handle routing/page selection
  - move all commonly shared code to another crate
  - make a different crate for each page

    - each page could be a different component
    - just a big function that produces Html

  - In the best case scenario, you go from rebuilding all of your code on each compile to rebuilding only the main crate, and one of your page crates.

  - In the worst case, where you edit something in the "common" crate, you will be right back to where you started: compiling all code that depends on that commonly shared crate

- you can use an example crate to create a more simple implementation

Whats missing

- docs
- native CSS support
- testing
- external libs wrapping major CSS frameworks

Wrapping Up

- https://yew.rs/docs/more/roadmap
- Other frameworks (Seed)
- links

Bullet points:

- Web Developers will feel right at home with Yew.

- With Yew, multi-threaded web applications are a breeze.

- With the power of Rust/Wasm nothing can stop Yew.

-
