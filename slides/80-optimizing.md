# Optimizing

## Optimizing Runtime

- neq_assign
- RC
- (non-native) Pure Components
- (missing) Function Components (coming soon?)

## Optimizing Build Size

- wee-alloc
- release compile profile
- wasm-opt: Loads WebAssembly and runs Binaryen IR passes on it.

<div class="notes">
My starter did all this for me
</div>

## Optimizing Build: wee-alloc

`wee_alloc`: The <b>W</b>asm-<b>E</b>nabled, <b>E</b>lfin Allocator.

- **Elfin, i.e. small**:

  - less than a kilobyte of uncompressed WebAssembly code.
  - Doesn't pull in the heavy panicking or formatting infrastructure.

- **WebAssembly enabled**: Designed for the wasm32-unknown-unknown target and #![no_std].

## Optimizing Compilation Time

Cargo Workspaces

- make your **main** crate handle routing/page selection

- move all **commonly shared** code to another crate

- make a different crate for **each page**

<div class="notes">

- compile time based on html! content

- break apart your code across multiple crates

  - each page could be a different component
  - just a big function that produces Html

- best case: rebuilding only the main crate, and one of your page crates

- worst case: edit something in the "common" crate compiling all code that depends on that

</div>

## What does batman use to climb a tree?

## His Yew-tility belt

![](./assets/batman.gif)
