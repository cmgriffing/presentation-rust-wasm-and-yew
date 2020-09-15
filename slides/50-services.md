# Services

Used to abstract Browser APIs

## Storage

```rust
let storage = StorageService::new(Area::Local).expect("storage was disabled by the user");
let Json(database) = storage.restore(KEY);
```

## Fetch

```rust
fn fetch_json(&mut self, binary: AsBinary) -> yew::services::fetch::FetchTask {
        let callback = self.link.callback(
            move |response: Response<Json<Result<DataFromFile, Error>>>| {
                // Handle response
            },
        );
        let request = Request::get("/data.json").body(Nothing).unwrap();

        FetchService::fetch(request, callback).unwrap()
        }
    }
```

## Render (requestAnimationFrame)

```rust
let render_frame = self.link.callback(Msg::Render);
let handle = RenderService::request_animation_frame(render_frame);
```

## Interval/Timeout

```rust
TimeoutService::spawn(Duration::from_secs(3), self.callback_done.clone());
```

```rust
IntervalService::spawn(Duration::from_secs(1), self.callback_tick.clone());
```

## And More

- Keyboard
- Resize
- WebSocket
- Dialog
- Console

<div class="notes">
Didnt see Scroll
</div>

## Where do devs go to learn about Yew?

## A Yew-niversity

![](./assets/graduation.jpeg)
