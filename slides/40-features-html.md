# Features: html!

## html!

<ul class="inline-list">
  <li>• A jsx-like syntax</li>
  <li>• HTML and SVG</li>
</ul>

Beware! Recursion Limit Error Prone

```rust

#![recursion_limit="1024"]

html! {
    <div>
        <button onclick=self.link.callback(|_| Msg::AddOne)>{ "+1" }</button>
        <p>{ self.value }</p>
        <ul class="item-list">
            { self.props.items.iter().map(renderItem).collect::<Html>() }
        </ul>
    </div>
}
```

## html!: Fragments

```rust
html! {
    <>
        <div></div>
        <p></p>
    </>
}
```

<div class="notes">
Looks familiar to most React or Vue devs in JS world
</div>

## html!: Iterators

```rust
html! {
    <ul class="item-list">
        { self.props.items.iter().map(renderItem).collect::<Html>() }
    </ul>
}
```

```rust
html! {
    <ul class="item-list">
        { for self.props.items.iter().map(renderItem) }
    </ul>
}
```

<div class="notes">
renderItem is a function that returns another html! block
</div>

## html!: CSS Classes

```rust
html! {
  <div class="container"></div>
  <div class="container center-align"></div>
  <div class=format!("{}-container", size)></div>
  <div class=("class-1", "class-2")></div>
  <div class=vec!["class-1", "class-2"]></div>
  <div class=self.classes()></div>
}
```

## html!: Literals

```rust
let text = "lorem ipsum";
html!{
    <>
        <div>{text}</div>
        <div>{"dolor sit"}</div>
        <span>{42}</span>
    </>
}
```

<div class="notes">

No bare text.
It is considered an expression.

Wrap literals with {}

</div>

## html!: Expressions

```rust
html! {
  <div>
    {
      if show_link {
        html! {
          <a href="https://example.com">{"Link"}</a>
        }
      } else {
        html! {}
      }
    }
  </div>
}
```

<div class="notes">
Often cleaner to extract to function

must have else and else must return html!

</div>
