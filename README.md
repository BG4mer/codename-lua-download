# Codename Engine — Psych-Style Lua Integration (REAL DROP-IN)

This pack adds **FULL Psych-style Lua scripting** into **Codename Engine**, including:
- State scripts (`data/states/StateName.lua`)
- Menu scripts
- PlayState scripts
- Substates
- Lifecycle hooks (onCreate, onUpdate, onDestroy, etc.)
- `setProperty`, `getProperty`, `changeState`, `pushSubstate`, `popSubstate`
- Optional per-state separate Lua runtimes

This pack **does NOT depend on Codename officially supporting Lua**. It runs entirely through a bundled Lua bridge.

## ⚡ What this pack actually gives you
- A complete Lua handler system with:
  - A Lua interpreter bridge
  - State manager hook layer
  - Psych-like API exposed to Lua
  - Example scripts for menus + playstates
  - Clean Haxe-side integration

## 📁 Folder Layout
```
src/lua/              → Lua bridge + handlers
scripts/              → Example Lua state scripts
install.md            → Installation steps
examples/             → Mini usage examples
```

## 🧩 How It Works (simple)
Codename runs states.
This pack attaches **Lua scripts to those states**.

Each state can have a script named:
```
StateName.lua
```
Example:
```
PlayState → PlayState.lua
MainMenu  → MainMenu.lua
PauseMenu → PauseMenu.lua
```

The Lua script receives callbacks:
- `onCreate()`
- `onUpdate(dt)`
- `onDestroy()`
- state/substate events

This mimics Psych’s behavior closely.

## 🔧 Lua API (Psych-like)
### Available functions in Lua:
```
setProperty{ key="something", value=123 }
getProperty{ key="something" }
changeState{ name="SomeState" }
pushSubstate{ name="PauseMenu" }
popSubstate{}
log{ message="text" }
```

### Example
```
function onCreate()
    log{message = "Loaded MainMenu"}
    setProperty{key="menuTitle", value="Codename Menu"}
end
```

## 🗂 Script Location
By default:
```
data/states/
```
But you can change it in LuaHandler.

## 🛠 Requirements
You must provide **one** of these:
- LuaJIT native binding (recommended) OR
- Lua 5.4 native binding OR
- Pure Haxe Lua VM (slow but no native setup)
- Generate target-specific native binding for Windows/macOS/Linux (hxcpp/hxcpp + C++) to load LuaJIT and forward 
