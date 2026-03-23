---
applyTo: "**"
---

# Figma MCP Write Server — Copilot Playbook

When designing or building anything in Figma through this workspace, **always use the MCP tool calls below** rather than describing actions in prose. Every tool is available as `mcp_figma-mcp-wri_<tool_name>` with an `operation` parameter (except alignment, which uses `horizontalOperation`/`verticalOperation`).

The MCP server prefix is: **`mcp_figma-mcp-wri_`**

---

## Tool Reference

### `mcp_figma-mcp-wri_figma_nodes`
Create, get, update, delete, and duplicate geometric shape nodes.

| Operation | What it does |
|---|---|
| `create_rectangle` | Create a rectangle node |
| `create_ellipse` | Create an ellipse/circle node |
| `create_frame` | Create a frame node |
| `create_section` | Create a section node |
| `create_slice` | Create a slice node |
| `create_star` | Create a star shape |
| `create_polygon` | Create a polygon shape |
| `update_rectangle` | Update an existing rectangle |
| `update_ellipse` | Update an existing ellipse |
| `update_frame` | Update an existing frame |
| `update_section` | Update an existing section |
| `update_slice` | Update an existing slice |
| `update_star` | Update an existing star |
| `update_polygon` | Update an existing polygon |
| `get` | Get node properties by ID |
| `list` | List nodes on the current page |
| `update` | Update properties of any node |
| `delete` | Delete a node |
| `duplicate` | Duplicate a node |

```
mcp_figma-mcp-wri_figma_nodes(operation: "create_frame", name: "Hero Section", width: 1440, height: 900)
mcp_figma-mcp-wri_figma_nodes(operation: "create_rectangle", name: "Card", width: 320, height: 200, x: 100, y: 100)
mcp_figma-mcp-wri_figma_nodes(operation: "get", nodeId: "123:456")
mcp_figma-mcp-wri_figma_nodes(operation: "delete", nodeId: "123:456")
```

---

### `mcp_figma-mcp-wri_figma_text`
Create, update, and format text nodes with full typography control.

| Operation | What it does |
|---|---|
| `create` | Create a new text node |
| `update` | Update text content or style |
| `get` | Get text node properties |
| `delete` | Delete a text node |
| `set_range` | Apply styling to a character range |
| `get_range` | Get styling of a character range |
| `delete_range` | Remove styling from a character range |
| `insert_text` | Insert text at a position |
| `delete_text` | Delete text at a position |
| `search_text` | Search for text content across the document |

```
mcp_figma-mcp-wri_figma_text(operation: "create", characters: "Hello World", x: 100, y: 100)
mcp_figma-mcp-wri_figma_text(operation: "update", nodeId: "123:456", fontSize: 24, fontWeight: 700)
mcp_figma-mcp-wri_figma_text(operation: "set_range", nodeId: "123:456", start: 0, end: 5, fillColor: "#FF0000")
mcp_figma-mcp-wri_figma_text(operation: "search_text", query: "Button Label")
```

---

### `mcp_figma-mcp-wri_figma_fills`
Manage fills on any node — solid, gradient, image, or pattern.

| Operation | What it does |
|---|---|
| `get` | Get all fills on a node |
| `add_solid` | Add a solid color fill |
| `add_gradient` | Add a gradient fill |
| `add_image` | Add an image fill |
| `add_pattern` | Add a pattern fill |
| `update` | Update fill by index |
| `update_solid` | Update a solid fill's color/opacity |
| `update_gradient` | Update gradient stops or angle |
| `update_image` | Update image fill properties |
| `update_pattern` | Update pattern fill properties |
| `delete` | Remove a fill by index |
| `reorder` | Change fill stacking order |
| `clear` | Remove all fills |
| `duplicate` | Duplicate a fill at a new index |

```
mcp_figma-mcp-wri_figma_fills(operation: "add_solid", nodeId: "123:456", color: "#4A90E2", opacity: 1)
mcp_figma-mcp-wri_figma_fills(operation: "add_gradient", nodeId: "123:456", gradientType: "LINEAR", stops: [...])
mcp_figma-mcp-wri_figma_fills(operation: "clear", nodeId: "123:456")
```

---

### `mcp_figma-mcp-wri_figma_strokes`
Manage strokes and stroke paint layers on nodes.

| Operation | What it does |
|---|---|
| `get` | Get all stroke paints on a node |
| `add_solid` | Add a solid stroke |
| `add_gradient` | Add a gradient stroke |
| `add_image` | Add an image stroke |
| `add_pattern` | Add a pattern stroke |
| `update` | Update stroke by index |
| `update_solid` | Update a solid stroke color/opacity |
| `update_gradient` | Update a gradient stroke |
| `update_image` | Update an image stroke |
| `update_pattern` | Update a pattern stroke |
| `delete` | Remove a stroke paint by index |
| `reorder` | Change stroke stacking order |
| `clear` | Remove all strokes |
| `duplicate` | Duplicate a stroke paint |

```
mcp_figma-mcp-wri_figma_strokes(operation: "add_solid", nodeId: "123:456", color: "#000000", strokeWeight: 2)
mcp_figma-mcp-wri_figma_strokes(operation: "clear", nodeId: "123:456")
```

---

### `mcp_figma-mcp-wri_figma_effects`
Manage visual effects — drop shadows, inner shadows, blurs, and background blurs.

| Operation | What it does |
|---|---|
| `create` | Add a new effect to a node |
| `update` | Update an effect by index |
| `delete` | Remove an effect by index |
| `get` | Get all effects on a node |
| `reorder` | Change effect stacking order |
| `duplicate` | Duplicate an effect |

```
mcp_figma-mcp-wri_figma_effects(operation: "create", nodeId: "123:456", effectType: "DROP_SHADOW", color: "#00000040", offsetX: 0, offsetY: 4, blur: 8)
mcp_figma-mcp-wri_figma_effects(operation: "create", nodeId: "123:456", effectType: "LAYER_BLUR", radius: 10)
mcp_figma-mcp-wri_figma_effects(operation: "delete", nodeId: "123:456", index: 0)
```

---

### `mcp_figma-mcp-wri_figma_styles`
Create, apply, and manage paint, text, effect, and grid styles.

| Operation | What it does |
|---|---|
| `create` | Create a new style |
| `update` | Update an existing style |
| `list` | List all styles in the document |
| `apply` | Apply a style to a node |
| `delete` | Delete a style |
| `get` | Get a style by ID or name |
| `duplicate` | Duplicate a style |

```
mcp_figma-mcp-wri_figma_styles(operation: "create", styleType: "PAINT", name: "Brand/Primary", color: "#4A90E2")
mcp_figma-mcp-wri_figma_styles(operation: "list", styleType: "TEXT")
mcp_figma-mcp-wri_figma_styles(operation: "apply", nodeId: "123:456", styleId: "S:abc123")
mcp_figma-mcp-wri_figma_styles(operation: "create", styleType: "TEXT", name: "Heading/H1", fontSize: 48, fontWeight: 700)
```

---

### `mcp_figma-mcp-wri_figma_variables`
Create design tokens (variables) and bind them to node properties.

| Operation | What it does |
|---|---|
| `create_collection` | Create a variable collection |
| `update_collection` | Rename or update a collection |
| `delete_collection` | Delete a collection |
| `get_collection` | Get a collection by ID |
| `list_collections` | List all collections |
| `duplicate_collection` | Duplicate an entire collection |
| `add_mode` | Add a mode to a collection (e.g., Light/Dark) |
| `remove_mode` | Remove a mode |
| `rename_mode` | Rename a mode |
| `create_variable` | Create a variable in a collection |
| `update_variable` | Update variable value or name |
| `delete_variable` | Delete a variable |
| `get_variable` | Get a variable by ID |
| `list_variables` | List all variables |
| `bind_variable` | Bind a variable to a node property |
| `unbind_variable` | Remove a variable binding |

```
mcp_figma-mcp-wri_figma_variables(operation: "create_collection", name: "Design Tokens")
mcp_figma-mcp-wri_figma_variables(operation: "add_mode", collectionId: "VC:abc", name: "Dark")
mcp_figma-mcp-wri_figma_variables(operation: "create_variable", collectionId: "VC:abc", name: "color/primary", resolvedType: "COLOR", value: "#4A90E2")
mcp_figma-mcp-wri_figma_variables(operation: "bind_variable", nodeId: "123:456", property: "fills", variableId: "V:abc")
```

---

### `mcp_figma-mcp-wri_figma_components`
Create and manage reusable components and component sets.

| Operation | What it does |
|---|---|
| `create` | Create a component from a frame or group |
| `create_set` | Create a component set (variants) |
| `update` | Update component properties |
| `delete` | Delete a component |
| `publish` | Publish a component to the library |
| `list` | List all components in the document |
| `get` | Get component by ID |

```
mcp_figma-mcp-wri_figma_components(operation: "create", nodeId: "123:456", name: "Button/Primary")
mcp_figma-mcp-wri_figma_components(operation: "list")
mcp_figma-mcp-wri_figma_components(operation: "create_set", componentIds: ["1:1", "1:2", "1:3"])
```

---

### `mcp_figma-mcp-wri_figma_instances`
Create, update, and manage component instances.

| Operation | What it does |
|---|---|
| `create` | Create an instance of a component |
| `update` | Update instance overrides |
| `duplicate` | Duplicate an instance |
| `detach` | Detach an instance from its component |
| `swap` | Swap one component for another |
| `reset_overrides` | Reset all overrides to component defaults |
| `get` | Get instance properties |
| `list` | List all instances in the document |

```
mcp_figma-mcp-wri_figma_instances(operation: "create", componentId: "C:abc123", x: 100, y: 200)
mcp_figma-mcp-wri_figma_instances(operation: "swap", nodeId: "123:456", componentId: "C:newComponent")
mcp_figma-mcp-wri_figma_instances(operation: "reset_overrides", nodeId: "123:456")
```

---

### `mcp_figma-mcp-wri_figma_auto_layout`
Configure auto layout (flexbox-style) on frames.

| Operation | What it does |
|---|---|
| `get` | Get auto layout settings for a node |
| `set_horizontal` | Set horizontal auto layout (row) |
| `set_vertical` | Set vertical auto layout (column) |
| `set_grid` | Set grid auto layout |
| `set_freeform` | Set freeform (canvas) auto layout |
| `set_child` | Configure child sizing within auto layout |
| `reorder_children` | Reorder children within an auto layout frame |

```
mcp_figma-mcp-wri_figma_auto_layout(operation: "set_vertical", nodeId: "123:456", gap: 16, paddingTop: 24, paddingRight: 24, paddingBottom: 24, paddingLeft: 24)
mcp_figma-mcp-wri_figma_auto_layout(operation: "set_horizontal", nodeId: "123:456", gap: 8, counterAxisAlignItems: "CENTER")
mcp_figma-mcp-wri_figma_auto_layout(operation: "set_child", nodeId: "123:789", layoutGrow: 1)
```

---

### `mcp_figma-mcp-wri_figma_alignment`
Align, distribute, or spread nodes. **No `operation` field** — use `horizontalOperation` and/or `verticalOperation`.

| Parameter | Values | What it does |
|---|---|---|
| `horizontalOperation` | `align` | Align to left, center, or right edge |
| `horizontalOperation` | `position` | Set exact x position |
| `horizontalOperation` | `distribute` | Distribute with equal spacing horizontally |
| `horizontalOperation` | `spread` | Spread with exact pixel gaps horizontally |
| `verticalOperation` | `align` | Align to top, middle, or bottom edge |
| `verticalOperation` | `position` | Set exact y position |
| `verticalOperation` | `distribute` | Distribute with equal spacing vertically |
| `verticalOperation` | `spread` | Spread with exact pixel gaps vertically |

```
mcp_figma-mcp-wri_figma_alignment(nodeIds: ["1:1","1:2","1:3"], horizontalOperation: "align", horizontalAlign: "center")
mcp_figma-mcp-wri_figma_alignment(nodeIds: ["1:1","1:2","1:3"], verticalOperation: "distribute")
mcp_figma-mcp-wri_figma_alignment(nodeIds: ["1:1","1:2"], horizontalOperation: "align", horizontalAlign: "left", verticalOperation: "align", verticalAlign: "top")
mcp_figma-mcp-wri_figma_alignment(nodeIds: ["1:1","1:2","1:3"], verticalOperation: "spread", verticalSpread: 16)
```

---

### `mcp_figma-mcp-wri_figma_constraints`
Set layout constraints for responsive behavior.

| Operation | What it does |
|---|---|
| `get` | Get current constraints for a node |
| `set` | Set horizontal and/or vertical constraints |
| `reset` | Reset constraints to defaults |

```
mcp_figma-mcp-wri_figma_constraints(operation: "set", nodeId: "123:456", horizontal: "STRETCH", vertical: "TOP")
mcp_figma-mcp-wri_figma_constraints(operation: "set", nodeId: "123:456", horizontal: "CENTER")
```

---

### `mcp_figma-mcp-wri_figma_hierarchy`
Group, ungroup, re-parent, and move nodes between pages.

| Operation | What it does |
|---|---|
| `group` | Group nodes together |
| `ungroup` | Ungroup a group node |
| `parent` | Move a node into a parent |
| `unparent` | Move a node out of its parent to the page |
| `order_by_index` | Change z-order by specifying an index |
| `order_by_depth` | Move to front, back, forward, or backward |
| `move_to_page` | Move nodes to another page |

```
mcp_figma-mcp-wri_figma_hierarchy(operation: "group", nodeIds: ["1:1","1:2","1:3"], name: "Card Group")
mcp_figma-mcp-wri_figma_hierarchy(operation: "parent", nodeId: "1:5", parentId: "1:2")
mcp_figma-mcp-wri_figma_hierarchy(operation: "order_by_depth", nodeId: "1:5", depth: "front")
mcp_figma-mcp-wri_figma_hierarchy(operation: "move_to_page", nodeId: "1:5", pageId: "0:2")
```

---

### `mcp_figma-mcp-wri_figma_pages`
Manage document pages.

| Operation | What it does |
|---|---|
| `list` | List all pages in the document |
| `get` | Get a page by ID |
| `get_current` | Get the currently active page |
| `create` | Create a new page |
| `update` | Rename or update page properties |
| `delete` | Delete a page |
| `duplicate` | Duplicate a page |
| `switch` | Switch to a page |
| `reorder` | Change page order |
| `create_divider` | Create a divider page (visual separator) |

```
mcp_figma-mcp-wri_figma_pages(operation: "list")
mcp_figma-mcp-wri_figma_pages(operation: "create", name: "Design System")
mcp_figma-mcp-wri_figma_pages(operation: "switch", pageId: "0:2")
mcp_figma-mcp-wri_figma_pages(operation: "reorder", pageId: "0:2", newIndex: 0)
```

---

### `mcp_figma-mcp-wri_figma_selection`
Get or change the active selection; search and filter nodes.

| Operation | What it does |
|---|---|
| `get_selection` | Get currently selected nodes |
| `set_selection` | Set selection to specific node IDs |
| `list_nodes` | List/search nodes with filters (type, name, etc.) |

```
mcp_figma-mcp-wri_figma_selection(operation: "get_selection")
mcp_figma-mcp-wri_figma_selection(operation: "set_selection", nodeIds: ["123:456","123:789"])
mcp_figma-mcp-wri_figma_selection(operation: "list_nodes", nodeType: "TEXT")
mcp_figma-mcp-wri_figma_selection(operation: "list_nodes", nameFilter: "Button")
```

---

### `mcp_figma-mcp-wri_figma_vectors`
Create and manipulate vector shapes and paths.

| Operation | What it does |
|---|---|
| `create_vector` | Create a vector node with a VectorNetwork |
| `get_vector` | Get vector node data |
| `update_vector` | Update vector paths, position, or size |
| `create_line` | Create a simple line |
| `get_line` | Get line node data |
| `update_line` | Update a line's endpoints or style |
| `flatten` | Flatten multiple nodes into a single vector |
| `convert_stroke` | Convert stroke to fills (outline stroke) |
| `convert_shape` | Convert any shape to a vector node |
| `convert_text` | Convert text to vector outlines |
| `extract_element` | Extract a region or path from a vector |

```
mcp_figma-mcp-wri_figma_vectors(operation: "create_line", startX: 0, startY: 0, endX: 200, endY: 0, strokeColor: "#000000", strokeWidth: 2)
mcp_figma-mcp-wri_figma_vectors(operation: "flatten", nodeIds: ["1:1","1:2"], name: "Combined Shape")
mcp_figma-mcp-wri_figma_vectors(operation: "convert_shape", nodeId: "123:456")
mcp_figma-mcp-wri_figma_vectors(operation: "convert_text", nodeId: "123:456")
```

---

### `mcp_figma-mcp-wri_figma_boolean_operations`
Combine vector shapes with boolean operations.

| Operation | What it does |
|---|---|
| `union` | Merge shapes into one |
| `subtract` | Subtract bottom shapes from top |
| `intersect` | Keep only the overlapping area |
| `exclude` | Keep only the non-overlapping areas |

```
mcp_figma-mcp-wri_figma_boolean_operations(operation: "union", nodeIds: ["1:1","1:2"])
mcp_figma-mcp-wri_figma_boolean_operations(operation: "subtract", nodeIds: ["1:1","1:2"])
mcp_figma-mcp-wri_figma_boolean_operations(operation: "intersect", nodeIds: ["1:1","1:2"])
```

---

### `mcp_figma-mcp-wri_figma_images`
Create and export image nodes.

| Operation | What it does |
|---|---|
| `list` | List all image hashes on the current page |
| `get` | Get detailed image node information |
| `export` | Export image data from a node |
| `create` | Create a new image node from a URL or data |

```
mcp_figma-mcp-wri_figma_images(operation: "list")
mcp_figma-mcp-wri_figma_images(operation: "create", imageUrl: "https://...", x: 100, y: 100, width: 400, height: 300)
mcp_figma-mcp-wri_figma_images(operation: "export", nodeId: "123:456", format: "PNG", scale: 2)
```

---

### `mcp_figma-mcp-wri_figma_exports`
Manage export presets and export nodes to files.

| Operation | What it does |
|---|---|
| `get_setting` | Get export settings for a node |
| `create_setting` | Add an export preset |
| `update_setting` | Update an existing export preset |
| `delete_setting` | Remove an export preset |
| `reorder_setting` | Change preset order |
| `clear_settings` | Remove all export presets |
| `duplicate_setting` | Duplicate an export preset |
| `export` | Trigger an export |

```
mcp_figma-mcp-wri_figma_exports(operation: "create_setting", nodeId: "123:456", format: "PNG", scale: 2, suffix: "@2x")
mcp_figma-mcp-wri_figma_exports(operation: "create_setting", nodeId: "123:456", format: "SVG")
mcp_figma-mcp-wri_figma_exports(operation: "export", nodeId: "123:456")
```

---

### `mcp_figma-mcp-wri_figma_fonts`
Search and validate fonts in Figma.

| Operation | What it does |
|---|---|
| `search_fonts` | Search for fonts by name |
| `check_availability` | Check if a font is available in Figma |
| `get_missing` | List fonts used in the document that are missing |
| `get_font_styles` | Get all available styles for a font |
| `validate_font` | Validate a font family + style combination |
| `get_font_info` | Get detailed information about a font |
| `preload_fonts` | Preload fonts for use in the document |
| `get_project_fonts` | List all fonts used in the document |
| `get_font_count` | Get the count of fonts used |

```
mcp_figma-mcp-wri_figma_fonts(operation: "search_fonts", query: "Inter")
mcp_figma-mcp-wri_figma_fonts(operation: "get_project_fonts")
mcp_figma-mcp-wri_figma_fonts(operation: "check_availability", family: "Inter", style: "Regular")
mcp_figma-mcp-wri_figma_fonts(operation: "get_missing")
```

---

### `mcp_figma-mcp-wri_figma_annotations`
Add design annotations visible in Dev Mode.

| Operation | What it does |
|---|---|
| `add_annotation` | Add an annotation to a node |
| `edit_annotation` | Edit an existing annotation |
| `remove_annotation` | Remove an annotation |
| `list_annotations` | List all annotations on the page |
| `list_categories` | List available annotation categories |
| `cleanup_orphaned` | Remove annotations with no associated node |

```
mcp_figma-mcp-wri_figma_annotations(operation: "add_annotation", nodeId: "123:456", label: "Use 8px border-radius", categoryId: "note")
mcp_figma-mcp-wri_figma_annotations(operation: "list_annotations")
mcp_figma-mcp-wri_figma_annotations(operation: "cleanup_orphaned")
```

---

### `mcp_figma-mcp-wri_figma_measurements`
Add spacing and sizing redlines/measurements.

| Operation | What it does |
|---|---|
| `add_measurement` | Add a measurement between two nodes |
| `edit_measurement` | Edit an existing measurement |
| `remove_measurement` | Remove a measurement |
| `list_measurements` | List all measurements on the page |

```
mcp_figma-mcp-wri_figma_measurements(operation: "add_measurement", fromNodeId: "1:1", toNodeId: "1:2")
mcp_figma-mcp-wri_figma_measurements(operation: "list_measurements")
```

---

### `mcp_figma-mcp-wri_figma_dev_resources`
Generate CSS and manage developer handoff resources.

| Operation | What it does |
|---|---|
| `generate_css` | Generate CSS code for a node |
| `set_dev_status` | Set the dev status (ready, in-progress, etc.) |
| `add_dev_link` | Add a link resource to a node |
| `remove_dev_link` | Remove a link resource |
| `get_dev_resources` | Get all dev resources for a node |

```
mcp_figma-mcp-wri_figma_dev_resources(operation: "generate_css", nodeId: "123:456")
mcp_figma-mcp-wri_figma_dev_resources(operation: "set_dev_status", nodeId: "123:456", status: "READY_FOR_DEV")
mcp_figma-mcp-wri_figma_dev_resources(operation: "add_dev_link", nodeId: "123:456", name: "Storybook", url: "https://storybook.example.com/button")
```

---

### `mcp_figma-mcp-wri_figma_plugin_status`
Diagnostics and connection health.

| Operation | What it does |
|---|---|
| `ping` | Simple liveness check |
| `status` | Get plugin+server status |
| `health` | Full health report |
| `system` | Get system information |
| `figma` | Get Figma document/user context |

```
mcp_figma-mcp-wri_figma_plugin_status(operation: "ping")
mcp_figma-mcp-wri_figma_plugin_status(operation: "health")
mcp_figma-mcp-wri_figma_plugin_status(operation: "figma")
```

---

## Common Design Workflows

### Create a button component
```
1. mcp_figma-mcp-wri_figma_nodes(operation: "create_frame", name: "Button/Primary", width: 120, height: 40)
2. mcp_figma-mcp-wri_figma_auto_layout(operation: "set_horizontal", nodeId: "<frameId>", gap: 8, paddingTop: 10, paddingRight: 20, paddingBottom: 10, paddingLeft: 20, primaryAxisAlignItems: "CENTER", counterAxisAlignItems: "CENTER")
3. mcp_figma-mcp-wri_figma_fills(operation: "add_solid", nodeId: "<frameId>", color: "#4A90E2")
4. mcp_figma-mcp-wri_figma_text(operation: "create", characters: "Button", parentId: "<frameId>")
5. mcp_figma-mcp-wri_figma_components(operation: "create", nodeId: "<frameId>", name: "Button/Primary")
```

### Apply a design token to a property
```
1. mcp_figma-mcp-wri_figma_variables(operation: "list_collections")
2. mcp_figma-mcp-wri_figma_variables(operation: "list_variables", collectionId: "<collectionId>")
3. mcp_figma-mcp-wri_figma_variables(operation: "bind_variable", nodeId: "<nodeId>", property: "fills", variableId: "<variableId>")
```

### Set up a page with sections
```
1. mcp_figma-mcp-wri_figma_pages(operation: "create", name: "Components")
2. mcp_figma-mcp-wri_figma_nodes(operation: "create_section", name: "Buttons", x: 0, y: 0)
3. mcp_figma-mcp-wri_figma_nodes(operation: "create_section", name: "Forms", x: 0, y: 600)
```

### Export assets
```
1. mcp_figma-mcp-wri_figma_exports(operation: "create_setting", nodeId: "<nodeId>", format: "PNG", scale: 1, suffix: "")
2. mcp_figma-mcp-wri_figma_exports(operation: "create_setting", nodeId: "<nodeId>", format: "PNG", scale: 2, suffix: "@2x")
3. mcp_figma-mcp-wri_figma_exports(operation: "create_setting", nodeId: "<nodeId>", format: "SVG")
4. mcp_figma-mcp-wri_figma_exports(operation: "export", nodeId: "<nodeId>")
```

---

## Decision Guide

| I want to... | Use this tool |
|---|---|
| Draw shapes / frames | `figma_nodes` |
| Add / style text | `figma_text` |
| Color a shape | `figma_fills` |
| Outline a shape | `figma_strokes` |
| Add shadows or blurs | `figma_effects` |
| Create reusable styles | `figma_styles` |
| Create design tokens | `figma_variables` |
| Make components | `figma_components` |
| Place component instances | `figma_instances` |
| Auto-layout / spacing | `figma_auto_layout` |
| Align / distribute nodes | `figma_alignment` |
| Responsive constraints | `figma_constraints` |
| Group / ungroup / stack | `figma_hierarchy` |
| Switch / create pages | `figma_pages` |
| Select / find nodes | `figma_selection` |
| Draw paths / lines | `figma_vectors` |
| Merge shapes | `figma_boolean_operations` |
| Place images | `figma_images` |
| Set up exports | `figma_exports` |
| Check font availability | `figma_fonts` |
| Add dev annotations | `figma_annotations` |
| Add redline measurements | `figma_measurements` |
| Generate CSS | `figma_dev_resources` |
| Check server connection | `figma_plugin_status` |
