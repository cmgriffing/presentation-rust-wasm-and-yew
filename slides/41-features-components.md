# Features: Components

## Components: Lifecycle

<img class="no-border" src="./assets/components-v4.png" />

## Components: Props Example

```rust
pub struct Container(Props);

#[derive(Properties, Clone)]
pub struct Props {
    pub children: Children,

    #[props_or_default]
    pub some_string,

    #[props_or_(true)]
    pub some_boolean,
}

impl Component for Container {
    type Properties = Props;

    fn view(&self) -> Html {
       html! {
           <div id="container">
               { self.0.children.render() }
           </div>
       }
    }
}
```

<div class="notes">
Things to call out:

- derive properties (do not implement manually)
- Props and default values
- children
</div>

## Components: Event Example

```rust
pub struct Container{
    props: Props,
    link: ComponentLink<Self>,
}

#[derive(Properties, Clone)]
pub struct Props { }

#[derive(Clone, PartialEq)]
pub enum Msg {
    Reset,
    HandleClick,
    HandleInput(event)
}

impl Component for Container {
    type Properties = Props;

    fn create(props: Self::Properties, link: ComponentLink<Self>) -> Self {
        Self {
            props,
            link,
        }
    }

    fn update(&mut self, msg: Self::Message) -> ShouldRender {
        match msg {
            Msg::HandleClick => {
                info!("HANDLING CLICK");
            }
            Msg::HandleInput(input_value) => {
                info!("HANDLING INPUT {:?}", input_value);
            }
        }

        true
    }

    fn view(&self) -> Html {
        html! {
            <div id="container">
                <input
                  oninput=self.link.callback(|event: InputData| Msg::handleInput(event.value))
                />
                <button
                  onclick=self.link.callback(|_| Msg::handleClick)
                >{"Click Me"}</button>
            </div>
        }
    }
}
```

<div class="notes">

</div>

## Components: Refs

```rust
// In create
self.node_ref = NodeRef::default();
​
// In view
html! {
    <div ref=self.node_ref.clone()></div>
}
​
// In update
let has_attributes = self.node_ref.try_into::<Element>().has_attributes();

```
