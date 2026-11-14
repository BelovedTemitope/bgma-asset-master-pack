# Lagos Rush: How big studios organise map assets (research for the Asset Master Pack)

**Status:** v01 research note (14 Nov 2026). Written for the team before building the Asset Master Pack. It is a reference document, not a decision record: nothing here overrides `_BGMA_Concepting_Decisions.md` or the kit rules in `LR_Map_Kit_and_Density_Rules_v03.md`.

**How to read the evidence.** Quotes in "double quotes" are verbatim from the source linked in the Sources list. Text marked **[Inferred]** is our reasoning, not something a studio has said. Text marked **[Community]** comes from fan wikis or press, not the developer. Public information is thin for Valorant asset management and almost absent for Call of Duty Mobile; this note says so where it applies rather than filling the gap.

---

## 1. The short version

1. **Everyone builds from kits snapped to a grid.** Fortnite uses a 512 cm cell; Skyrim used footprints that are "multiples of each other"; Roblox's own showcase game used a 16-stud grid. Our kit should have one base footprint too.
2. **Variants are mostly cheap swaps on a shared base mesh.** PUBG: "we often take the base mesh of the building and simply apply other materials, roof, and set dressing". Roblox: "90% of the architectural elements used a handful of swappable trim sheet sets".
3. **Names follow a fixed pattern with a two-digit variant number.** Allar's Unreal guide: `Prefix_BaseAssetName_Variant_Suffix`, variants `01`, `02`…, and "you should never require a three digit variant number."
4. **Gameplay pieces and decoration are kept apart on purpose.** Riot keeps "a clean gameplay zone", with detail below about 1 foot or above 9 feet. PUBG has "very strict rules" on interiors and window placement so looting is fast.
5. **The engine itself holds the tags.** Unreal uses Data Layers and Level Instances; Roblox uses CollectionService tags, Attributes and Packages. The tracker and the map stay in sync by counting what is tagged in the place file, not by hand.

---

## 2. Fortnite (Epic Games)

### 2.1 The grid and the building kit
Epic's UEFN architectural guidelines publish the actual Fortnite building metrics. Every structural piece sits on one cell:

| Piece | Size (cm) | Notes |
|---|---|---|
| Wall | 512 wide × 384 high × 24 thick | Half wall 192 high, quarter wall 96 high |
| Floor / ceiling | 512 × 512 × 24 | "Floor and ceiling actors are hybrids." |
| Stair | 512 × 512 × 384 | "Stay within the gridspace outlined above when creating stairs." |
| Roof | 512 × 512 × 384 | "Stay within the gridspace when creating roofs." |

Key rules from the same page: "Build using the existing building metrics and boundaries already used in UEFN", "Make sure your pivot points are in the correct position to work with the existing building system", and "The main goal when creating a wall is to ensure that the majority of the thickness of the wall remains at 24 cm total thickness." Thickness is fixed because the player build system, collision and destruction all depend on it. **[Inferred]** That is why Fortnite map buildings and player builds can share one destruction and cover system.

### 2.2 Prefabs and galleries: how Epic groups props for creators
The clearest public view of Epic's taxonomy is the Creative/UEFN content library:

- "Prefabs are ready-made structures, and galleries are themed collections of building pieces and props."
- "A prefab is a prefabricated structure, like a fully furnished building, bridge, environment backdrop, or floating island."
- "Unlike a prefab, a gallery is not assembled into a structure." Galleries are "broken into categories like props, walls, and doors."
- **Themes** sit above both. Prefab themes: Cabin, Castle, Farm, Industrial, Military, Residential, Prehistoric, Retail, Seaside, Sports, Terrain, Western. Gallery themes add Decoration ("Variety of non-themed props that can be placed for design"), Nature and Terrain, Vehicle, Seasonal and others.

So Epic's hierarchy is effectively **Theme > Prefab (assembled building) or Gallery (kit) > Category (walls, doors, props) > individual asset**. Gameplay props with behaviour (for example the Hiding Prop Gallery: Port-a-Potty, Haystack, Garbage Dumpster, Scarecrow) are shipped as **device galleries**, separate from decorative galleries. That is a useful precedent: **props with gameplay behaviour live in their own group, even if they look like set dressing.**

### 2.3 World Partition, Data Layers and Level Instances
Epic's UE 5.1 blog on Fortnite Chapter 4 says the game moved to UE5's World Partition with automatic streaming on every platform, replacing the custom streaming of earlier seasons, and lists the toolset as World Partition, Data Layers, Level Instances, automatic HLODs and One File Per Actor. (The blog page blocked our fetch, so this is a summary of it, not a quote.) Epic's Level Instancing docs say level instances and packed level actors support Data Layers, and that actors inside a level instance inherit its data layer.

**[Inferred]** For a team our size, the lessons are: (a) one building = one reusable container (a Level Instance in Unreal, a Model or Package in Roblox); (b) layers or tags mark *what the asset is for* (gameplay, decoration, seasonal), separate from *where it is*.

### 2.4 Destruction by material
**[Community]** Fortnite's player-built walls have different max health per material (wood lowest, stone middle, metal highest). The exact numbers have changed across patches (fan sources quote wood 150 or 200, stone 300, metal 400, 450 or 500), so don't treat any single figure as fact. World props also give different resource types depending on what they're made of. We found no Epic document that sets out the health tiers for map props. The pattern worth copying is **one material class per asset, which then sets its destruction or penetration behaviour**, not the numbers.

### 2.5 Naming and audits
Epic doesn't publish Fortnite's internal naming scheme. The widely used community standard for Unreal (Allar, section 7) is the best public proxy. No public Fortnite asset-audit process was found.

---

## 3. PUBG (KRAFTON / PUBG Studios)

### 3.1 How buildings are produced (primary source: a PUBG environment artist)
Carlos Sánchez, 3D Environment Artist at PUBG, interviewed by 80.lv (2021):

- Team: "Our team was formed by around 15 people, most of them Environment Artists in charge of developing the entire map".
- Process: reference buildings picked from Street View that "we like or that we think can be fun to play", then "a simple blockout in collaboration with the level design team".
- **Variants from one base:** "we often take the base mesh of the building and simply apply other materials, roof, and set dressing".
- Modularity: "we used to always have some modular parts, like roofs, trims, etc." For one season they went much further: "almost every building is 80% modular", with the modules "assembled inside Unreal". The risk he names: modularity "might make your buildings look too similar to each other."
- **Gameplay rules beat art:** "We have very strict rules when it comes to interior layouts or window placement for instance." "we want our buildings to be as simple and recognizable as possible to make the looting fast and smooth." "Having a clear and simple looting path is key."
- Standards: texel density "1024px-3m for us"; "a unique mask per building since we decided not to use Vertex Paint."
- Detail budget: "almost 50% of the time I had to create all the buildings on small assets" (corners, windows, stone bases).

### 3.2 Map-level decisions
- Sanhok (GamesBeat interview): "We knew we were going to increase the loot density. Therefore, we also simplified the layout." Layout complexity and loot density are set together.
- Vikendi Reborn dev Q&A: the map grew from 6×6 km to 8×8 km, and a cable-car route was cut after "we discovered risks during our map performance test". **Assets get cut on performance grounds late in production**, so the tracker needs a "cut" status.
- The Erangel remaster (2019) added buildings and building groups and tied the work to loot balance ("new ways to balance loot and otherwise improve our maps, Erangel being the first", quoted in press coverage). No public asset-pipeline breakdown of it was found.

### 3.3 Loot tagging per building type
**[Inferred / Community]** Players widely note that PUBG loot spawns sit at fixed points inside each building type, so every copy of a building type has the same spawn-point layout. We found no developer source that documents the tagging system. The design consequence, which we already use: **the building type (BLD-H1 and so on) fixes the interior layout and the number of loot points; variants change only the look.**

### 3.4 PUBG Mobile
Lightspeed Studios gave a GDC talk, "PUBG MOBILE: Performance Optimization on Mobile Platform" (Fan Zhang). PocketGamer.biz's write-up reports over 22,000 device models, with over 55% low-end. We couldn't get the talk's foliage and LOD rules from public text. The takeaway, that every asset needs a performance tier and the low tier is the majority of players, is direct. The specific numbers are not public.

---

## 4. Valorant (Riot Games)

Public material is about **process and readability**, not asset tracking. Riot has not published naming or ownership schemes.

- Pipeline (The Art of VALORANT Map Environments): "greybox (the earliest playable version of a map)", then art blockout ("it's better to work with simple shapes during the blockout phase to avoid having to re-do work"), then art production. Team: "fairly small, and consists of level designers, 3D, concept, lighting, and QA."
- Reuse: "we primarily use tiling textures and trim sheets on our buildings and large structures." Instancing: "if there is a pile of the same 20 rocks, we can instance them together, so that the engine reads them as one mesh."
- QA: playtests check that there is "accurate collision" and "areas that are too noisy."
- **The gameplay vs. decoration split** (The Birth of Ascent): "One rule that we try to adhere to is the idea of a clean gameplay zone across the map." "we keep the majority of artistic detail of the map below about 1 foot in elevation or higher than 9 feet." Block-in goal: "fully understand what every single structure and cover object looks like." "Essentially we ask how can the art make the map play better?"
- Phase lengths: "Art Production can last upwards of 6 months".
- Riot's tech blog on shaders explains that they skip dynamic shadows in the playable space so low-settings players don't lose information.

**[Inferred]** Riot's "1 ft / 9 ft" rule converts to about **1 stud and 10 studs** at our scale (1 stud = 0.28 m; 9 ft ≈ 2.74 m ≈ 9.8 studs). That is a ready-made rule for where LIF- decoration may go without creating fake cover.

---

## 5. Call of Duty: Warzone and Call of Duty Mobile

Public information on asset management is thin. What exists:

- Infinity Ward used **block streaming** so Verdansk's many enterable buildings didn't all have to load at once (GamesRadar interview).
- The Kabul location was considered partly because its desert textures and materials would need less memory (EssentiallySports, reporting a developer interview). **Material variety is treated as a memory budget.**
- Multiplayer design directors describe blockout first, then hand-off to environment art, with ongoing back-and-forth on placement and readability (Dexerto interview).
- Activision released the **Caldera** Warzone map as an OpenUSD data set. Activision says it is "not the actual production data but rather a conversion". Its folder layout includes a prefabs directory, which publicly confirms that **CoD maps are assembled from prefabs** (reusable grouped assemblies). Caldera was "primarily authored by the team at Raven Software", with help from other studios.
- GDC 2023 had a Call of Duty talk on on-demand texture streaming (Sledgehammer Games): install size and memory drive the texture pipeline.

**Not found:** any public source on how CoD tracks variants (material swaps, damage states), names assets or tags them. Nothing public was found about Call of Duty Mobile's (TiMi) map asset pipeline. Anything we say about it would be guesswork, so this note says nothing more.

---

## 6. General industry practice

### 6.1 Modular kits: Skyrim (Joel Burgess and Nathan Purkeypile, GDC 2013)
From the Game Developer reprint of the talk:

- "Kits, first and foremost, are systems." "This kit, as most, snaps together using a grid system."
- "The footprint is the foundation of the entire kit." "those footprints should be multiples of each other", e.g. "a 512x512x512 room will always tile nicely with a 256x256x256 hallway".
- "Level designers tend to build on a grid snap setting of one-half the size of the footprint."
- Pivots: "Generally, the pivots of our kit pieces are at the ground plane of the kit and in the center."
- **Kit > sub-kit > piece:** "A sub-kit is what we call each part of the kit that works with the rest of it." "The cave kit has seven sub-kits, while the Ratway has only three." One cave sub-kit "has around 50 pieces"; "The Ratway hall sub-kit has only seven pieces."
- **Naming:** "The key to good naming is balancing brevity with readability." "Try to choose naming conventions that will make sense to someone who has never seen it before." "It's wise to add 01 as a suffix to any piece which will feature visual variants".
- **Track usage:** the Cave kit was used "over 200 times", while the Ratway kit was "only used twice". Seven kits produced "well over 400 cells", with two full-time kit artists. **Counting how often a kit is used tells you where to spend art time.**

### 6.2 The Level Design Book (Robert Yang)
- A modular kit is "a 3D tileset of modules, meshes designed to snap together."
- Basic pieces: "floor, ceiling, wall, doorway (single), doorway (double), window, corner."
- In blockout: "DO NOT MAKE VARIANTS YET, just build basic pieces first." In the art pass, texture variations are cheap because "you don't have to test and validate the module geometry again."
- "pay attention to naming, level designers and kit artists need to agree on a pattern."

### 6.3 Naming: Allar's Unreal style guide
- "Any asset that is part of this logical group should follow the standard of `Prefix_BaseAssetName_Variant_Suffix`."
- "For unique but generic variations of assets, `Variant` is a two digit number starting at `01`." "Except for rare exceptions, you should never require a three digit variant number."
- Prefixes: static mesh (the guide says "Many use SM_. We use S_."), `M_` material, `MI_` material instance (e.g. `MI_Rock_Snow`), `T_` texture with suffixes `_D` `_N` `_R` `_M` and so on.
- Folders: group by asset (base name), not by type; no spaces ("Spaces can cause various engineering tools and batch processes to fail.").

### 6.4 Trackers
Autodesk Flow Production Tracking (formerly ShotGrid) is the industry tracker for VFX, animation and games. Its model is useful even if we use a spreadsheet:
- One **Asset** entity, with **asset type** as metadata. Autodesk's example: "We recommend using Asset to cover Concepts, Themes and Parts, and use the meta-data (asset type) to distinguish the difference."
- **Tasks** hang off assets, with a pipeline of steps per type ("ShotGrid allows you to define Pipelines per entity type").
- Status history and burndown charts. A third-party guide advises keeping statuses few and recording "who changes status and when".

**[Inferred]** A Google Sheet with one row per Type, a Variants tab, a fixed status list and a weekly burndown gives us 90% of this at our scale. Perforce or Git LFS handles file versioning; on Roblox, package version history does some of that job (section 6.6).

### 6.5 Standards: texel density, trims, LOD
- PUBG texel density: "1024px-3m" (about 341 px/m). Riot: tiling textures and trim sheets on buildings. Roblox's showcase: "90% of the architectural elements used a handful of swappable trim sheet sets".
- **[Inferred]** Trim sheets and shared material sets are what make colour/material variants nearly free, so variants should be defined as **material-set swaps on the same mesh**, never as duplicated meshes.

### 6.6 Roblox-specific practice (we ship here)
**Beyond the Dark** (Roblox's own showcase, Building Architecture doc):
- "we settled on a 16 stud grid size to create most of the modular set."
- "Modular palette pieces are reusable assets, meaning we don't have to create each wall uniquely"; "a palette of Meshparts that easily snapped together".
- Packages: "updates you make to the package are published to all instances of that package"; "we used over 1,000 wall panel instances of a package".
- Materials: "SurfaceAppearance nodes that the MeshParts could share"; naming: "add a postfix of _SA to make them easy to search for"; reuse "improves runtime performance by decreasing object and material draw calls."

**Engine features for tracking:**
- **CollectionService:** "manages groups (collections) of instances with tags." "Tags are sets of strings applied to instances that replicate from the server to the client. They are also serialized when places are saved." `GetTagged` "returns an array of instances with a given tag". This is our counting tool.
- **Attributes:** "Attributes allow you to customize instances with your own data." "Attributes and their values are saved with your place and assets." Use them to store the ID, variant, role and tier on each placed model.
- **Packages:** reuse "single assets or asset hierarchies across games"; AutoUpdate is set on the PackageLink; editing a copy disables auto-update until you publish or revert; version history can be compared and restored. Per the older docs, nested packages don't auto-update. **[Inferred]** Keep one package per Type, not packages inside packages.
- **Instance streaming:** `ModelStreamingMode` Atomic means "all of its initial descendants are streamed in together"; Persistent models are sent "soon after the player joins" and never stream out, but "overuse may negatively impact performance." SLIM LOD lets "distant models… remain visible even when they're not streamed to clients." **[Inferred]** Buildings with interiors and loot should be Atomic models; landmarks (P1 silhouettes) are candidates for the low-detail distant LOD; only a handful of things should be Persistent.

---

## 7. Patterns across all studios

| Question | What the studios do | Source strength |
|---|---|---|
| How are assets grouped? | Theme > kit/gallery > sub-kit/category > piece (Epic, Bethesda) | Strong (primary) |
| What is a variant? | Same base mesh and layout; different materials, roof, dressing (PUBG). Texture variants don't need re-testing (LDB) | Strong |
| How are variants named? | Two-digit suffix from 01 (Allar, Bethesda) | Strong |
| Gameplay vs decoration | Clean gameplay zone; detail below 1 ft or above 9 ft (Riot). Strict interior/window rules (PUBG). Gameplay props in separate device galleries (Epic) | Strong |
| Loot per building type | Fixed per type, the same in every copy | Inferred / community |
| Destruction by material | Material class sets health/behaviour | Community (Fortnite) |
| Budgets | Texel density, trims, instancing, streaming; assets cut after perf tests | Strong (PUBG, Riot, CoD, Roblox) |
| Tracking | Asset + type metadata + task pipeline + status history (ShotGrid); usage counts (Bethesda) | Strong (tool docs), studio internals not public |

---

## 8. Recommendations for our Asset Master Pack

These fit into the codes we already use (`BLD-H1`, `CMP-A`, `CVR-H1`, `VEG-T01`, `MOV-R2`, `INT-C`, Z1–Z6, P1–P4). Nothing is renamed.

### 8.1 Hierarchy: five levels
| Level | Meaning | Example | Already exists? |
|---|---|---|---|
| **Category** | Gameplay purpose (top split) | Structures, Cover, Movement, Landscape, Vegetation, Water, Life, Systems | New, label only |
| **Group** | Our three-letter prefix | `BLD`, `CVR`, `VEG`, `WLK`, `BOT` | Yes |
| **Family** | The letter (and sub-letter) after the prefix | `BLD-H` (houses), `BLD-G` (estate), `CVR-H` (hard cover), `VEG-T` (trees) | Yes |
| **Type** | Family + number: one footprint, one collision, one interior layout | `BLD-H1`, `CVR-H3`, `VEG-T05` | Yes |
| **Variant** | Two-digit suffix: same footprint and layout, different look | `BLD-H1-02` | **New** |
| (Material set) | Colour/material swap; an attribute, not a separate ID | `BLD-H1-02` + `Mat=M3` | **New** |

Suggested categories (labels only, for sorting the tracker): **Structures** (BLD, CMP, INT), **Cover** (CVR), **Movement** (MOV, WLK, PTH), **Landscape and ground** (LND, GND, TOP), **Water** (WTR, BOT), **Vegetation** (VEG), **Life and dressing** (LIF), **Systems** (new prefixes below).

### 8.2 New prefixes (only where nothing exists)
| Prefix | For | Why |
|---|---|---|
| `KIT-` | Modular building pieces (wall, floor, stair, roof, door, window, trim) | Bethesda/Epic: the kit is its own system. Building types are assembled from it |
| `LOOT-` | Loot spawn markers (floor, shelf, crate) | Kept separate so it can be counted per building type |
| `VSP-` | Vehicle and boat spawn markers | Separates the spawn point from the vehicle model (BOT- stays the model) |
| `MAT-` | Material/colour sets (`MAT-M1`…) | Variants reference them; trim-sheet based |

Kit pieces should use our grid. **[Inferred]** Suggest a **4-stud snap** with 8- and 16-stud wall widths and a 12-stud storey (matches D-scale: storey = 12, door = 4×7). Sixteen studs echoes Beyond the Dark and is a multiple of our CVR-H1 wall length (16). Example: `KIT-W16` (16-stud wall), `KIT-W16D` (with door), `KIT-F16` (floor), `KIT-S12` (stair, one storey). Temitope/Saheed to confirm before this becomes a rule.

### 8.3 ID and naming scheme
- **Type ID:** unchanged, `GRP-FamNN` as now (`BLD-H1`, `VEG-T05`).
- **Variant ID:** `GRP-FamN-VV`, two digits from 01: `BLD-H1-01`, `BLD-H1-02`. `-01` is the base. Never three digits (Allar).
- **Material set:** attribute `Mat = "M3"`, written in the tracker as `BLD-H1-02/M3` when needed. Don't make a new ID for a colour swap.
- **Roblox names:** Model name = Variant ID (`BLD-H1-02`). MeshParts inside: `BLD-H1_WallFront_01`. SurfaceAppearance: `MAT-M3_Plaster_SA` (Roblox's own `_SA` convention). No spaces anywhere.
- **Files and folders** (Blender/exports): group by Type, not by file type: `Assets/BLD/BLD-H1/BLD-H1-02.fbx`.

### 8.4 Variant rules: when it's a variant and when it's a new Type
Based on PUBG (same base mesh, other materials/roof/dressing) and the Level Design Book (texture variants don't need re-testing):

1. **Variant** if the footprint, collision, doors/windows, interior layout (INT- code), number of loot points and cover role are **all unchanged**. Only materials, roof finish, signage and decoration differ.
2. **New Type** (next number, e.g. `BLD-H3`) if any of these change: footprint by more than one grid step, number of floors, entries, interior layout, loot count, or cover height class (full/half/low).
3. **New Family** (new letter) if the gameplay role changes (e.g. a house becomes a shop) or the Type count in a family passes about 6, to keep the tracker readable.
4. **Caps** **[Inferred]**: at most **4 geometry variants per Type** and **4–6 material sets per Group**. More than that costs memory on low-end phones (the PUBG Mobile lesson: most players are low-end) and dilutes recognisability (PUBG's "simple and recognizable").
5. **Grey-box has no variants** (Level Design Book). Variants are added only at the "Modelled" stage.

### 8.5 Master tracker columns
One row per **Type**, with a second tab for **Variants** (one row per Variant ID).

| Column | Content / allowed values |
|---|---|
| ID | `BLD-H1` |
| Name | Face-me-I-face-you rooming house |
| Category / Group / Family | Structures / BLD / BLD-H |
| Footprint (studs) | W × D × H, e.g. 32 × 54 × 14 |
| Gameplay role | Building-enterable, Building-closed, Hard cover (full/half/low), Soft cover, Concealment, Loot container, Traversal (ladder, stair, bridge, walkway), Vehicle spawn, Landmark, Decoration |
| Interior code | INT-C / INT-L / INT-S / none |
| Loot points | Number per copy (fixed per Type) |
| Material class | Block, timber, metal sheet, concrete, foliage (sets bullet penetration/destruction later) |
| Variants | Count + list (`-01…-04`) |
| Material sets | `M1, M3` |
| Kit pieces used | `KIT-W16, KIT-F16…` |
| Perf tier | T1 hero/landmark, T2 standard, T3 cheap/instanced; plus LOD/streaming mode (Atomic / Default / Persistent) |
| Tri / part budget | Target triangles and instance count |
| Count planned | From the zone plans |
| Count in map | Filled by the counting script (8.6) |
| Zones / places | Z1–Z6, P1–P4 names |
| Status | Concept → Grey-box → Modelled → Textured → In-game → Approved (plus Cut) |
| Owner | One name |
| Last updated / notes | Date, decision references (D-numbers) |

### 8.6 Keeping the list and the map in sync
1. **Tag every placed model** with CollectionService tags: the Group (`BLD`), the Type (`BLD-H1`) and the Role (`Role_HardCover`, `Role_Loot`, `Role_Decoration`). Tags are saved with the place and `GetTagged` returns every copy.
2. **Set Attributes** on each model: `AssetID = "BLD-H1-02"`, `Mat = "M3"`, `Zone = "Z2"`, `Tier = "T2"`, `Status = "Textured"`.
3. **One Package per Variant**, AutoUpdate on, no nested packages, so a fix to `BLD-H1-02` reaches all copies (Beyond the Dark used one package for 1,000+ wall panels).
4. **A counting script** (Studio command bar or plugin) loops `GetTagged` per Type, reads the Attributes and prints CSV: ID, variant, mat, zone, count, and any untagged models. Paste it into the "Count in map" column weekly. Report: missing IDs, Types placed but not in the tracker, and planned-vs-placed gaps. This is Bethesda's "used over 200 times / only twice" check, done automatically.
5. **Untagged = not done.** A model without `AssetID` fails the weekly audit. Decoration (`LIF-`) must also stay out of Riot's clean zone (about 1–10 studs high) unless it is tagged as cover.
6. **Version the tracker** like the other docs (`_v01`, `_v02`), and record status changes with a date (the ShotGrid "who and when" rule).

### 8.7 What we couldn't confirm
- Riot's and Activision's internal naming and tracking: not public.
- PUBG's loot-tagging system and PUBG Mobile's exact foliage/LOD numbers: not public in text form (the GDC talk is in the Vault).
- Fortnite prop health by material: community data only, and it changes by patch.
- The 4-stud snap, the variant caps and the tier names above are our proposals, for team sign-off.

---

## Sources

**Fortnite / Epic**
- Architectural Modeling Guidelines in UEFN: https://dev.epicgames.com/documentation/en-us/uefn/architectural-modeling-guidelines-in-unreal-editor-for-fortnite
- Using Prefabs and Galleries in Fortnite Creative: https://dev.epicgames.com/documentation/fortnite/using-prefabs-and-galleries-in-fortnite-creative
- Hiding Prop Gallery devices: https://dev.epicgames.com/documentation/fortnite/using-hiding-prop-gallery-devices-in-fortnite-creative
- Battle-testing UE 5.1 on Fortnite Chapter 4 (Epic blog): https://www.unrealengine.com/en-US/blog/battle-testing-unreal-engine-5-1-s-new-features-on-fortnite-battle-royale-chapter-4
- World Partition Data Layers: https://dev.epicgames.com/documentation/en-us/unreal-engine/world-partition---data-layers-in-unreal-engine
- Level Instancing: https://dev.epicgames.com/documentation/en-us/unreal-engine/level-instancing-in-unreal-engine
- Fortnite Re:Imagine London (UEFN grid/voxel build sites): https://www.fortnite.com/news/fortnite-s-re-imagine-london-bringing-london-to-life-in-uefn
- [Community] Building material health changes: https://www.gamerevolution.com/guides/410337-fortnite-building-nerf-new-material-health-pickaxe-damage-other-changes

**PUBG / KRAFTON**
- 80.lv, Creating Diverse Buildings for PUBG (Carlos Sánchez): https://80.lv/articles/creating-diverse-buildings-for-pubg/
- GamesBeat, Making a PUBG map (Sanhok): https://gamesbeat.com/making-a-pubg-map/2
- Dev Talk: Vikendi Reborn – Additional Q&A: https://pubg.com/en/news/1519
- PC Gamer, Erangel map changes: https://www.pcgamer.com/pubg-is-getting-some-big-map-changes-starting-with-erangel
- GDC Vault, PUBG MOBILE: Performance Optimization on Mobile Platform: https://gdcvault.com/play/1029294/LIGHTSPEED-STUDIOS-Developer-Summit-PUBG
- PocketGamer.biz on the PUBG Mobile optimisation talk: https://www.pocketgamer.biz/interview/81247/pubg-mobile-co-developer-discusses-optimising-unreal-for-thousands-of-phone-types/

**Valorant / Riot**
- The Art of VALORANT Map Environments: https://playvalorant.com/en-gb/news/dev/the-art-of-valorant-map-environments/
- The Birth of Ascent: https://playvalorant.com/en-gb/news/dev/the-birth-of-ascent/
- VALORANT Shaders and Gameplay Clarity (Riot tech blog): https://technology.riotgames.com/node/110

**Call of Duty / Activision**
- GamesRadar, Infinity Ward on Warzone (block streaming): https://www.gamesradar.com/as-warzone-season-5-looms-infinity-ward-reflects-on-the-secrets-that-make-its-call-of-duty-battle-royale-sing
- EssentiallySports, Warzone locations that never shipped: https://www.essentiallysports.com/call-of-duty-warzone-developers-reveal-the-idea-behind-the-gulag-and-locations-that-never-saw-the-light-of-day-esports-news
- Dexerto, CoD map design process interview: https://dexerto.com/call-of-duty/interview-call-of-duty-developers-break-down-map-design-process-2150268
- Activision, Caldera data set: https://blog.activision.com/activision/2024/activision-releases-call-of-duty-warzone-caldera-data-set and https://github.com/Activision/caldera
- GDC 2023 CoD texture streaming session: https://gdconf.com/news/learn-ins-and-outs-call-duty-modern-warfare-2-streaming-tech-gdc-2023-session

**General practice**
- Skyrim's Modular Approach to Level Design (Game Developer): https://gamedeveloper.com/design/skyrim-s-modular-approach-to-level-design
- Slides, Modular Level Design for Skyrim: https://www.slideshare.net/JoelBurgess/gdc2013-kit-buildingfinal
- The Level Design Book, Modular kits: https://book.leveldesignbook.com/process/blockout/metrics/modular
- Allar UE5 Style Guide: https://github.com/Allar/ue5-style-guide
- Tom Looman, Unreal naming conventions: https://tomlooman.com/unreal-engine-naming-convention-guide/
- Autodesk Flow Production Tracking: https://www.autodesk.com/products/flow-production-tracking/overview.html
- Autodesk asset-type guidance (automotive example): https://help.autodesk.com/cloudhelp/ENU/SG-Automotive/files/am-getting-started/SG_Automotive_am_getting_started_am_interface_html.html
- ShotGrid status practice (third party): https://gse.kz/en/blog/shotgrid-manage-content-production-statuses

**Roblox**
- Beyond the Dark, Building Architecture: https://create.roblox.com/docs/resources/beyond-the-dark/building-architecture
- CollectionService: https://create.roblox.com/docs/reference/engine/classes/CollectionService
- Properties, Attributes and Tags: https://create.roblox.com/docs/studio/properties
- Packages: https://create.roblox.com/docs/projects/assets/packages
- Instance streaming: https://create.roblox.com/docs/workspace/streaming
