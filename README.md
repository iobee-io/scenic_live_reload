# ScenicLiveReload

A live reloader for Scenic. Once configured, when you edit a file the current
root scene will be killed, when it is restarted it will use any new code
currently in the running beam instance.

Uses [exsync](https://github.com/falood/exsync) to watch the file system. Then
when you edit a file with your editor, exsync will trigger a recompile and
reload of the affected beam files.

# Demo

In this demo I replace the text "World" with "Scenic", then change the color of
the text to purple. Next I change the shape of the bezier line.

[![Screencast Demo](./demo.gif)](https://raw.githubusercontent.com/axelson/scenic-starter-pack/master/demo.gif)

Note: the code running in the demo can be found at
[scenic-starter-pack](https://github.com/axelson/scenic-starter-pack) (which
uses this repository)

# Installation

Add `scenic_live_reload` to your list of dependencies in `mix.exs`:

```elixir
def deps do
  [
    ...
    {:scenic_live_reload, github: "axelson/scenic_live_reload", only: :dev},
  ]
end
```

Add this configuration to your `config.exs`:
```
case Mix.env() do
  :dev ->
    config :exsync,
      reload_timeout: 75,
      reload_callback: {ScenicLiveReload, :reload_current_scene, []}

  _ -> nil
end
```

# Development

NOTE: This currently relies on a private scenic api to get the root scene which may change in future Scenic releases

TODO:
- [x] Write nicer description
- [x] Request new exsync release
- [ ] Publish to hex
- [ ] Announce
