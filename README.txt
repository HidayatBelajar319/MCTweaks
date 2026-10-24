# Minecraft Tweaks — Ultimate Text & Item Customization Toolkit

## 1. Project Overview

Create a complete, polished Minecraft utility mod named **Minecraft Tweaks** for **Minecraft Java Edition 1.16.5 using Fabric**.

The mod's primary purpose is to improve text editing, item naming, character insertion, text formatting, and customization workflows throughout Minecraft. Instead of implementing isolated improvements in individual screens, build a cohesive toolkit with reusable editors, formatting controls, character pickers, presets, clipboard utilities, and a consistent user interface.

### Reference Projects

Use these projects as functional references for research and inspiration:

- Stendhal: https://modrinth.com/mod/stendhal
- Text Utilities: https://modrinth.com/mod/text-utilities
- Edit Everything: https://modrinth.com/mod/edit-everything

Study their publicly documented features, screenshots, and relevant implementation details when available.

Do not assume that features supported by their modern Minecraft versions are available in 1.16.5. Reimplement compatible functionality using the correct Fabric APIs, Yarn mappings, vanilla screen classes, and text representation for the target version.

Create an original implementation with its own UI, code, and assets.

**Target environment: Minecraft Java Edition 1.16.5 + Fabric.** Do not silently switch to Forge or a newer Minecraft version.

---

## 2. Universal Text Editor

Create a reusable text-editing component that can be integrated into multiple Minecraft screens.

### Formatting Toolbar

Provide buttons for:

- Bold
- Italic
- Underline
- Strikethrough
- Obfuscated text
- Text colors supported by the target version
- Reset formatting
- Clear selected formatting
- Undo and redo, where reliable

Allow users to apply formatting to selected text without unnecessarily overwriting surrounding content.

Support Minecraft 1.16.5-compatible legacy formatting codes wherever the relevant context accepts them. Investigate the limitations of each screen instead of assuming every context interprets formatting identically.

### Unicode and Symbol Picker

Build a searchable popup with categories such as:

- Common symbols
- Decorative characters
- Arrows and navigation symbols
- Mathematical symbols
- Currency symbols
- Geometric shapes
- Box-drawing characters
- Greek letters
- Accented characters
- Emoji-like Unicode characters
- Frequently used characters

Include search, recently used characters, favorites, and one-click insertion.

Preserve the text cursor and selection when inserting characters.

Provide a glyph-availability indicator or diagnostic preview when feasible. Explain when a character requires a resource pack or cannot be displayed correctly by Minecraft 1.16.5's default font.

Do not claim that all modern emoji render correctly.

### Text Editing Utilities

Implement reusable operations for:

- Copy, cut, and paste
- Select all
- Find and replace
- Undo and redo
- Clear text
- Insert saved snippets
- Remove unwanted whitespace
- Duplicate selected text
- Character and line counters
- Formatting preview
- Keyboard shortcuts

Prevent shortcuts from interfering with vanilla controls, commands, and other mods.

---

## 3. Book & Quill and Written Books

Enhance the vanilla Book & Quill editing interface.

Features:

- Integrated formatting toolbar
- Unicode and symbol picker
- Page navigation and page management
- Character and page-limit indicators
- Copy and paste page contents
- Clear current page
- Copy the complete book's text
- Find and replace within a page or book
- Undo and redo
- Text snippets and reusable templates
- Readable text-file export
- Text-file import where compatible
- Improved keyboard navigation
- Live formatting preview where feasible

Create starter templates for:

- Adventure journals
- Player guides
- Server rules
- Quest descriptions
- Item documentation
- Storybooks
- Coordinates and travel notes
- Checklists

Templates must be editable, and users must be able to create their own.

For signed books, provide reading, navigation, search, and export utilities where feasible. Do not silently bypass vanilla restrictions on editing signed books.

Preserve existing page contents and formatting when editing.

---

## 4. Anvil and Universal Item Renaming

Improve the vanilla Anvil screen with an integrated naming toolbar.

Features:

- Unicode character picker
- Formatting and color buttons where supported
- Copy, paste, clear, and reset controls
- Name-length indicator
- Saved naming presets
- Live preview of the resulting name
- Find and replace
- Recent names and favorite names
- Cursor-aware text insertion

Preserve normal Anvil functionality, including repair costs, enchantment combinations, item consumption, and output-slot restrictions.

### Apply One Naming Toolkit to All Relevant Items

The Anvil already handles the renaming of many item types. The same improved interface should work with, where supported by vanilla mechanics:

- Tools and weapons
- Armor and shields
- Food and consumables
- Potions and tipped arrows
- Bows, fishing rods, and other equipment
- Maps
- Books
- Banners
- Shulker boxes
- Fireworks
- Name Tags
- Spawn eggs and other renamable items

The mod should not need a separate, incompatible editor for every item category.

Test the actual behavior of each category in Minecraft 1.16.5. Some custom names may be stored correctly but displayed differently depending on the item or screen.

### Name Tags and Entities

Improve the workflow for naming mobs through Name Tags and the Anvil.

Provide:

- Saved mob-name presets
- Unicode and formatting assistance
- Quick insertion of commonly used names
- Optional name templates for pets, villagers, and other entities

Do not change mob behavior or bypass server-side naming restrictions.

---

## 5. Item Description and Lore Editor

Add an optional **Item Details Editor** for supported item metadata.

This feature must be separate from the vanilla Anvil because Minecraft 1.16.5 does not provide a normal vanilla interface for freely editing item lore.

Where technically possible, support:

- Custom display names
- Multi-line item lore
- Formatting and color previews
- Unicode characters
- Adding, removing, and reordering lore lines
- Copying and pasting lore
- Reusable lore templates
- Previewing the final tooltip
- Resetting modifications before applying them

### Compatibility Rules

- Clearly identify which operations are available in single-player, Creative mode, or compatible multiplayer environments.
- Prefer safe draft editing before applying modifications.
- Do not claim that a client-only GUI can permanently change server-owned item data.
- Use the appropriate 1.16.5 item NBT representation where applicable.
- Require compatible server support or another legitimate writable environment when the server controls the relevant data.
- Never silently overwrite item data unrelated to the requested change.

If reliable editing cannot be implemented for a particular environment, provide a read-only preview and explain the limitation.

---

## 6. Sign Editor and Sign Utilities

Enhance sign editing with:

- Formatting toolbar
- Unicode picker
- Copy and paste
- Clear-line controls
- Line-length indicators
- Saved sign templates
- Undo and redo where reliable
- Character compatibility warnings
- Text preview

Create useful templates for:

- Directional signs
- Storage labels
- Shop labels
- Farm indicators
- Warning signs
- Server information
- Decorative signs
- Coordinate markers

### Sign Copy and Retention

Where compatible with the environment, add:

- Copy text from an existing sign to another sign
- Retain sign text when breaking and replacing a sign
- Optional remembered sign templates
- Quick access to recent sign contents

Implement these operations safely and distinguish local conveniences from persistent world changes requiring server cooperation.

Do not silently change the behavior of existing signs or block interactions.

---

## 7. Chat Text Toolkit

Improve the in-game chat input with an optional compact toolbar.

Features:

- Unicode and symbol picker
- Text snippets
- Formatting-code insertion
- Copy, paste, and find utilities where appropriate
- Saved messages
- Recently used characters
- Configurable keyboard shortcuts
- Optional text templates for commands and ordinary messages

Include a configurable shortcut for opening the character picker.

Preserve command input, chat history, autocomplete, cursor position, and existing keybindings.

Do not send messages automatically or bypass server chat restrictions.

Formatting codes should be inserted only when appropriate for the target context and server.

---

## 8. Additional Text and Customization Features

### A. Item Tooltip Inspector

Add an optional tooltip-inspection utility.

- Display custom item names and lore in a readable format.
- Allow users to copy visible tooltip text.
- Show relevant text formatting and Unicode information.
- Distinguish display names, lore, and other metadata when accessible.
- Provide a comparison view for two items where practical.

This utility should be read-only unless the user explicitly opens an appropriate editor.

### B. Map Naming and Organization

Enhance map-renaming workflows through the Anvil.

- Suggest readable naming templates.
- Allow saved naming patterns.
- Support coordinate or location labels in names.
- Make it easy to copy names from other maps.
- Preserve vanilla map data and functionality.

Do not promise that the mod can freely edit map artwork or map markers through a text editor.

### C. Item Frame and Display Utilities

Provide optional quality-of-life tools for item frames.

- Copy visible item names and tooltip text.
- Offer a convenient way to prepare labels for displayed items.
- Support reusable display-label templates.
- Allow configurable click-through behavior when safe and compatible.
- Avoid blocking interactions with containers behind signs or item frames.

Do not assume item frames contain editable text. Their primary purpose is displaying items, so use the text toolkit to assist with the items they display.

### D. Banner and Shield Naming

Provide naming presets for banners and shields through the Anvil.

Examples include:

- Team names
- Base identifiers
- Faction labels
- Decorative Unicode symbols

Keep banner-pattern editing separate. Banner patterns are graphical designs, not text fields, and should not be modified by the text editor.

### E. General Inventory Text Tools

Where appropriate, allow users to inspect or copy names and visible text from inventory items.

Potential utilities:

- Copy an item's displayed name
- Save a name as a preset
- Reuse a previous name
- Compare item descriptions
- Open the Item Details Editor when the item and environment support it

Do not add invasive inventory automation or modify unrelated item data.

---

## 9. Presets, Templates, and Clipboard Manager

Build a shared preset system used by the Book Editor, Sign Editor, Anvil, Chat, and Item Details Editor.

Features:

- Save custom text snippets
- Create named folders or categories
- Search saved snippets
- Mark favorites
- Store recently used text
- Duplicate and rename presets
- Import and export presets as readable files
- Provide a preview before inserting a preset
- Allow users to choose whether formatting is preserved

Suggested preset categories:

- Decorative symbols
- Common formatting
- Server announcements
- Item names
- Item lore
- Sign templates
- Book templates
- Chat snippets
- Coordinates and labels

Store configuration and presets in the Minecraft configuration directory.

Use safe file handling and avoid storing sensitive chat information by default.

---

## 10. Configuration and Accessibility

Provide a clear configuration system.

Allow users to:

- Enable or disable each feature independently
- Configure toolbar positions
- Toggle compact mode
- Customize keyboard shortcuts
- Enable or disable formatting controls
- Configure character-picker categories
- Manage saved presets
- Choose between mouse and keyboard interaction
- Reset settings to defaults

Ensure the UI scales correctly across resolutions and GUI scales.

Use clear tooltips, consistent button placement, and readable icons. Avoid covering important vanilla controls.

The mod must remain lightweight and suitable for older computers.

---

## 11. Technical Requirements

- Minecraft Java Edition 1.16.5
- Fabric Loader
- Java
- Compatible Fabric API
- Compatible Fabric Loom and Yarn mappings
- Compatible build toolchain

Before implementing any feature, verify the relevant classes, methods, mappings, dependencies, and behavior for Minecraft 1.16.5.

Use Mixins only when necessary. Keep injection points narrow and avoid brittle modifications to vanilla screens.

Prefer client-side implementations for UI improvements. Use server integration only where necessary for persistent world or item-data changes.

Avoid unnecessary dependencies, excessive memory use, and expensive rendering operations.

Keep the mod modular, maintainable, and compatible with common Fabric client-side mods wherever practical.

---

## 12. Testing and Quality Assurance

Create a feature checklist and test each feature independently.

Verify:

1. Book editing, formatting, page management, and export.
2. Anvil renaming for representative vanilla item categories.
3. Unicode insertion and missing-glyph handling.
4. Sign editing and sign-copy behavior.
5. Chat toolbar compatibility.
6. Item tooltip inspection.
7. Lore editing in supported environments.
8. Preset saving, loading, import, and export.
9. Keyboard shortcuts and cursor preservation.
10. GUI scaling and button placement.
11. Single-player behavior.
12. Multiplayer limitations and server compatibility.
13. Compatibility with Minecraft 1.16.5 Fabric dependencies.
14. Startup, runtime, and compilation errors.

Fix actual errors instead of leaving placeholder methods, fake buttons, or incomplete implementations.

Do not report a feature as tested unless it was actually tested.

If a feature cannot be implemented reliably, document the limitation and provide a useful compatible alternative.

---

## 13. Deliverables

Produce a complete, buildable Minecraft 1.16.5 Fabric project containing:

- Java source code
- Fabric metadata
- Mixin configuration when required
- Compatible Gradle build files
- Resource files and original UI assets
- Default configuration
- Example text presets and templates
- README with installation and usage instructions
- Build and testing instructions
- A documented list of client-only and server-dependent features

Produce a compiled `.jar` only after a successful build.

The project must be usable and maintainable, not merely a visual prototype.

## Final Objective

Build **Minecraft Tweaks** as a unified text and item customization toolkit for Minecraft Java 1.16.5 Fabric.

The mod should improve nearly every relevant text-editing workflow available in vanilla Minecraft, while adding carefully designed utilities for item metadata, templates, clipboard management, and sign organization.

Prioritize compatibility, reliability, performance, and genuine functionality. Every visible control must perform its advertised action, and every feature must respect the limitations of the target Minecraft version.