# Mission Tree Framework

This mod adds a fourth Journal tab, `Mission Tree`, next to `Nation Formation`.

The mission-node proportions follow EU4 `countrymissionsview.gui`: each slot is `104 x 152`, the frame is `103 x 123`, the mission icon is `59 x 63` at `{ 22 20 }`, and the title box is `90 x 22` at `{ 8 84 }`.

## Files

- `gui/journal.gui`: copied from vanilla and modified only to add the fourth tab and a `mission_tree_panel` call.
- `gui/mission_tree.gui`: reusable mission button and arrow components, plus the example `FRA` tree.
- `common/scripted_guis/mt_mission_tree_sguis.txt`: clickable mission logic and GUI status checks.
- `common/scripted_triggers/mt_mission_tree_triggers.txt`: tag/tree visibility checks.
- `localization/english/mt_mission_tree_l_english.yml`: tab, mission names, and tooltips.

## Adding A New Tag Tree

1. Add a tree visibility trigger in `common/scripted_triggers/mt_mission_tree_triggers.txt`.
2. Add that trigger to `mt_has_active_tree` in `common/scripted_guis/mt_mission_tree_sguis.txt`.
3. Add `done` and `claim` scripted GUI blocks for every mission.
4. Copy the `FRA` container in `gui/mission_tree.gui`, change its `visible` scripted GUI, mission names, textures, and positions.
5. Place arrows between missions with:
   - `mt_arrow_down`
   - `mt_arrow_down_left`
   - `mt_arrow_down_right`
   These use copied official EU4 mission-tree assets from `Europa Universalis IV/gfx/interface/missions`.
6. Add localization for the tree header, mission names, and tooltips.

Mission state is stored on the country with variables named like `mt_fra_expand_industry_done`. To make a mission depend on another mission, add `has_variable = previous_mission_done` to its `claim` scripted GUI `is_valid` block.
