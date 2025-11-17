# Codename Engine: Fake Lua System

A **fake Lua-like configuration system** for Codename Engine.
This allows you to **configure gameplay, characters, camera, sound, and more** via **variables in separate Haxe files**, without writing raw Haxe code for each tweak.

> ⚠️ Note: This is **not actual Lua**. It’s a Haxe-based “fake Lua” system designed to simulate Lua-style configuration in Codename Engine.

---

## Installation

1. Place the entire folder into your game’s scripts directory:

```lua
/data/scripts/codenameluanotreally/
```

2. Make sure all `.hx` files are present, along with `fakeLuaConfig.hx`.

---

## File Structure

| File                | Description                                        |
| ------------------- | -------------------------------------------------- |
| PlayState.hx        | Configure health, note speed, max notes, positions |
| Reflection.hx       | Reflection-like dynamic property changes           |
| Spritesheet.hx      | Add or preload custom sprites                      |
| FlxAnimate.hx       | Configure character animations                     |
| Text.hx             | Configure UI text elements                         |
| Sound.hx            | Background music and sound effects                 |
| Shaders.hx          | Fake shader control                                |
| Camera.hx           | Camera shake, flash, zoom, and scroll              |
| Input.hx            | Control input settings and key behavior            |
| Tween.hx            | Tween objects like characters                      |
| Timer.hx            | Timers and delayed events                          |
| Character.hx        | Visibility, flip, scale, tint for characters       |
| FileIO.hx           | Load/save JSON or text files                       |
| Language.hx         | Language and localization settings                 |
| Achievements.hx     | Unlock achievements                                |
| Substate.hx         | Custom substate management                         |
| Precache.hx         | Preload textures, sounds, and fonts                |
| Score.hx            | Score and combo settings                           |
| SaveData.hx         | Manage save slots and auto-save                    |
| Script.hx           | Run custom scripts at certain times                |
| Discord.hx          | Update Discord Rich Presence (optional)            |
| Uncategorized.hx    | Misc variables for experimentation                 |
| StateFunction.hx    | Custom state functions (onCreate, onBeat, etc.)    |
| SubstateFunction.hx | Custom substate functions                          |
| fakeLuaConfig.hx    | Main config loader that applies all files          |

---

## How to Use

1. **Edit the variables in each `.hx` file** to tweak your gameplay, camera, sound, characters, and more.

   * Example: `PlayState.hx` → change `noteSpeed = 1.5;` to make notes faster.
   * Example: `Camera.hx` → change `shakeAmount = 0.1;` for stronger camera shake.

2. **Load `fakeLuaConfig.hx` in your Mod/Week**:

```haxe
addLuaScript("codenameluanotreally/fakeLuaConfig");
```

3. **Automatic updates**:

   * All variables are applied on `onCreate`.
   * Per-beat updates happen in `onBeatHit()`.
   * Some settings can be applied on update or manually via `apply()`.

4. **Custom functions**:

   * `StateFunction.hx` and `SubstateFunction.hx` allow you to run **custom behaviors** on creation, beat, or step.
   * Use `stateParam1`, `stateParam2`, `substateParam1`, and `substateParam2` to pass information to your custom function.

---

## Notes

* **No actual Lua execution**: This system only mimics Lua-style configuration using Haxe variables.
* **Safe for mods**: You can tweak gameplay without touching main Haxe code.
* **Expandable**: Add more functions by creating new `.hx` files and importing them into `fakeLuaConfig.hx`.

---

## Example: Changing Note Speed & Camera Shake

```haxe
// PlayState.hx
noteSpeed = 1.5;

// Camera.hx
shakeAmount = 0.12;
shakeLength = 0.25;
```

After saving, launch your mod and these changes take effect automatically.
