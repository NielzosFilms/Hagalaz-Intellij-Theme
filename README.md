# Hagalaz — IntelliJ / JetBrains IDE theme

Full UI theme (chrome + editor) for JetBrains IDEs, ported from the Hagalaz
Omarchy/Hyprland desktop theme. Ash-black, bone, iron, blood red.

## Quick install (no build tools needed)

This is a data-only plugin (no compiled code), so the pre-built jar just
needs to be installed directly:

1. Open any JetBrains IDE → **Settings/Preferences → Plugins**
2. Click the gear icon (⚙️) → **Install Plugin from Disk...**
3. Pick `hagalaz-theme.jar`
4. Restart the IDE when prompted
5. **Settings → Appearance & Behavior → Appearance → Theme → Hagalaz**

The editor color scheme installs alongside it automatically (it's
referenced from the theme). You can also select it independently under
**Settings → Editor → Color Scheme → Hagalaz** if you want the syntax
colors without the full UI theme.

## Editing the theme

The source lives under `src/main/resources/`:

- `META-INF/plugin.xml` — plugin metadata + the `themeProvider` registration
- `theme/Hagalaz.theme.json` — UI chrome colors (buttons, tool windows,
  trees, tabs, popups, scrollbars, etc.) — see JetBrains' theme.json key
  reference for anything not covered here
- `theme/Hagalaz.xml` — editor syntax highlighting, built on top of Darcula
  as a parent scheme so anything not explicitly overridden falls back
  sensibly

After editing, rebuild the jar with:

```bash
cd src/main/resources
zip -r ../../../hagalaz-theme.jar META-INF theme
```

(delete the old jar first, or add `-u` to update in place)

## If you want a real Gradle build later

Once you outgrow hand-editing JSON/XML — e.g. you want custom icons, a
`runIde` sandbox to preview live, or to publish to the JetBrains
Marketplace — scaffold a proper project with the **IntelliJ Platform
Gradle Plugin** (2.x). JetBrains only supports Gradle for this; there's
no maintained Maven path. The official theme-plugin template is at:
https://github.com/JetBrains/intellij-platform-plugin-template

Drop this `src/` tree into that template's `src/main/resources/` and
`buildPlugin` will produce a proper distributable zip.

## Palette reference

| Role | Hex |
|---|---|
| Background (ash black) | `#0a0807` |
| Soot (bars/popups) | `#14100e` |
| Iron (borders/selection) | `#2e2724` |
| Muted | `#6b635c` |
| Bone (foreground) | `#d5cbbb` |
| Accent (blood red) | `#c1121f` |
| Accent tail (dried blood) | `#5a0d10` |

Syntax mapping follows the same near-monochrome logic as the terminal
scheme: keywords/tags in blood red, strings in sage, numbers in dusty
gold, functions in grey-blue, classes/annotations in dusty mauve,
interfaces in muted teal, comments in muted grey-italic.
