# Lagos Rush BR Island: asset groups breakdown v01

Built from blockout v029 (6,437 coded objects in visible layers) and the locked concept masters, 14 Nov 2026. **11 categories, 39 groups, 198 asset types.** Visual version: `index.html` in this folder. Per-type spreadsheet: `LR_Asset_Register_v01.csv`. Raw counts: `LR_Blockout_v029_Inventory.json`.

Exists in: B = blockout v029, C = concept art only, P = plans only.

| Category | Groups | Asset types | Objects placed |
|---|---|---|---|
| TER Terrain, ground and water | 4 | 29 | 33 |
| BLD Buildings | 7 | 29 | 574 |
| CMP Compounds, places and prefabs | 4 | 24 | 22 |
| MOV Roads and paths (modular) | 3 | 13 | 27 |
| BRG Bridges and elevated structures | 3 | 10 | 223 |
| WLK Waterfront walkways and decks | 3 | 9 | 26 |
| CVR Cover, walls and fences | 3 | 17 | 1,196 |
| VEH Vehicles and boats | 2 | 11 | 393 |
| VEG Vegetation | 5 | 27 | 4,224 |
| LIF Life props and set dressing | 4 | 23 | 98 |
| GPL Gameplay objects (to plan) | 1 | 6 | 0 |

## TER: Terrain, ground and water (4 groups, 29 types)

The base everything sits on: the height map, the sea and lagoon, the painted ground cover classes and the shore types.

### Base surfaces (2)

| Code | Asset | Placed | In | Note |
|---|---|---|---|---|
| TER-Terrain | Island height-field (1 unit = 1 stud) | 1 | B | one mesh, 4-stud voxels in Roblox |
| TER-Water | Sea and lagoon surface | 1 | B |  |

### Ground cover classes (GC) (13)

| Code | Asset | Placed | In | Note |
|---|---|---|---|---|
| GC-1 | Worn bare earth / laterite |  | B | painted on the terrain, not placed |
| GC-2 | Lived-in short grass |  | B | painted on the terrain, not placed |
| GC-3 | Vacant-plot weeds |  | B | painted on the terrain, not placed |
| GC-4 | Farm plots incl. cassava |  | B | painted on the terrain, not placed |
| GC-5 | Fallow / thicket ground |  | B | painted on the terrain, not placed |
| GC-6 | Woodlot floor |  | B | painted on the terrain, not placed |
| GC-7 | Hill crown |  | B | painted on the terrain, not placed |
| GC-8 | Sand shore |  | B | painted on the terrain, not placed |
| GC-9 | Swamp / mangrove edge |  | B | painted on the terrain, not placed |
| GC-10 | Strand creeper mat |  | B | painted on the terrain, not placed |
| GC-11 | Estate lawn |  | B | painted on the terrain, not placed |
| GC-12 | Paving (interlock / asphalt) |  | B | painted on the terrain, not placed |
| GC-13 | Tilled cassava soil |  | B | painted on the terrain, not placed |

### Shore types (SHR) (4)

| Code | Asset | Placed | In | Note |
|---|---|---|---|---|
| SHR-1 | Sand beach |  | B | 57.7% of shore |
| SHR-2 | Mudflat |  | B | Makoko bay, coves |
| SHR-3 | Revetment / sea wall | 1 | B | where masonry is near water |
| SHR-4 | Cut bank / bluff |  | B |  |

### Landscape features (LND) (10)

| Code | Asset | Placed | In | Note |
|---|---|---|---|---|
| LND-F | Farmland |  | P |  |
| LND-B | Bush / scrub belt |  | P |  |
| LND-R | Laterite ridge |  | B |  |
| LND-H | Hill crown |  | B |  |
| LND-Q | Sand / borrow pit | 27 | B | 14 sizes |
| LND-S | Swamp / mangrove edge |  | B |  |
| LND-C | Creek / canal |  | B |  |
| LND-E1 | Estate football field | 1 | B |  |
| LND-E2 | Swimming pool | 1 | B |  |
| LND-E3 | Tennis / basketball court | 1 | B |  |

## BLD: Buildings (7 groups, 29 types)

Everything with walls and a roof that players read as a building. Most are enterable and carry an interior code and loot slots.

### Village and residential (4)

| Code | Asset | Placed | In | Note |
|---|---|---|---|---|
| BLD-H1 | Face-me-I-face-you rooming house | 45 | B | 31 sizes on map |
| BLD-H2 | Family house / duplex | 85 | B | 40 sizes on map |
| BLD-Q1 | Boys' quarters | 39 | B |  |
| BLD-U1 | Unfinished block shell | 110 | B | signature cover-loot piece |

### Town and commercial (5)

| Code | Asset | Placed | In | Note |
|---|---|---|---|---|
| BLD-T1 | Tenement storey building (2-4 floors) | 13 | B |  |
| BLD-S1 | Shophouse | 12 | B |  |
| BLD-S2 | Lock-up shop row | 11 | B |  |
| BLD-K1 | Container shop / kiosk | 25 | B |  |
| BLD-W1 | Warehouse / shed | 5 | B |  |

### Civic, religious, school (4)

| Code | Asset | Placed | In | Note |
|---|---|---|---|---|
| BLD-C1 | Church hall | 4 | B |  |
| BLD-C2 | Mosque + minaret | 4 | B |  |
| BLD-E1 | School block | 2 | B |  |
| BLD-F1 | Filling station | 4 | B |  |

### Gated estate (TMH) (6)

| Code | Asset | Placed | In | Note |
|---|---|---|---|---|
| BLD-G1 | Government estate block | 4 | B |  |
| BLD-G2 | King Tower high-rise | 1 | B |  |
| BLD-G3 | Detached duplex | 11 | B |  |
| BLD-G4 | Terrace town-house row | 4 | B |  |
| BLD-G5 | Clubhouse | 1 | B |  |
| BLD-S3 | Gatehouse / estate office | 2 | B |  |

### Utility and towers (4)

| Code | Asset | Placed | In | Note |
|---|---|---|---|---|
| BLD-X1 | Water tank stand | 45 | B |  |
| BLD-X2 | Elevated estate water tower | 2 | B |  |
| BLD-X4 | Borehole house | 1 | B |  |
| BLD-X5 | Telecom mast | 1 | B |  |

### Makoko stilt buildings (4)

| Code | Asset | Placed | In | Note |
|---|---|---|---|---|
| BLD-M1 | Stilt house, one room | 88 | B |  |
| BLD-M3 | Stilt house, two-storey | 21 | B |  |
| BLD-M4 | Stilt hall (church / school) | 6 | B |  |
| BLD-M5 | Open fish-smoking shed | 23 | B |  |

### Landmark one-offs (2)

| Code | Asset | Placed | In | Note |
|---|---|---|---|---|
| BLD-L1 | POI landmark building | 1 | B | one per P1 |
| DFD-STRUCT | Danfo Depot sheds and office | 4 | B | needs proper BLD codes |

## CMP: Compounds, places and prefabs (4 groups, 24 types)

Groups of assets saved and reused as one unit: a walled family compound, a school, a whole minor place. These are 'prefabs' in game-studio terms.

### Compound types (CMP) (7)

| Code | Asset | Placed | In | Note |
|---|---|---|---|---|
| CMP-A | Family compound | 1 | B |  |
| CMP-B | Rooming compound |  | B |  |
| CMP-C | Mechanic / vulcaniser yard |  | P |  |
| CMP-D | School compound | 1 | B |  |
| CMP-E | Estate plot (duplex + BQ + tank) | 11 | B | was 'church compound' before v03 |
| CMP-F | Unfinished estate |  | B |  |
| CMP-R | Religious compound (church / mosque) | 2 | B | new in v029 |

### Minor places (P2) (10)

| Code | Asset | Placed | In | Note |
|---|---|---|---|---|
| P2_01 | Tarkwa Dredge | 1 | B |  |
| P2_02 | Mercy Land Chapel | 1 | B |  |
| P2_03 | Iyanrin Sand Market | 1 | B |  |
| P2_04 | Unity Grammar School | 1 | B |  |
| P2_05 | Okun Fish-Smoking Yard | 1 | B |  |
| P2_08 | Bode Laterite Pit | 1 | B |  |
| P2_09 | Alfa Beach Sand-Diggers | 1 | B |  |
| P2_11 | Eja Jetty Tower | 1 | B |  |
| P2_15 | Jum'at Mosque | 1 | B |  |
| P2_18 | Ebute Boatyard | 1 | B |  |

### Named locations (P1) (5)

| Code | Asset | Placed | In | Note |
|---|---|---|---|---|
| ILE | Ile Isoko (dense core) | 1 | B |  |
| BUS | Bus Stop (market hub) | 1 | B |  |
| DFD | Danfo Depot | 1 | B |  |
| TMH | Third Mainland Heights estate | 1 | B |  |
| MKS | Makoko | 1 | B | 7 stilt villages |

### Small repeat sets (2)

| Code | Asset | Placed | In | Note |
|---|---|---|---|---|
| WFT | Waterfront outpost (stilt row + jetty) |  | B | bay and creek shores |
| VEG-S06+CVR-F | Household cassava plot + stick fence | 18 | B | one per lived-in house (D124) |

## MOV: Roads and paths (modular) (3 groups, 13 types)

Everything players and vehicles travel along on land. Best built from a small modular kit of road pieces.

### Road classes (5)

| Code | Asset | Placed | In | Note |
|---|---|---|---|---|
| MOV-R1 | Dual carriageway (R1, bridge approach) | 2 | B | 48 / 67 studs wide |
| MOV-R2 | Two-lane road | 11 | B | 26 wide |
| MOV-R3 | Town street |  | P | 16-20 wide |
| MOV-R4 | Alley / footway |  | P | min 6 wide |
| MOV-R5 | Estate road (boulevard / loop / close) | 6 | B | 3 variants |

### Paths (2)

| Code | Asset | Placed | In | Note |
|---|---|---|---|---|
| PTH-1 | Footpath |  | B | hidden layer in v029 |
| PTH-2 | Farm track |  | B | hidden layer in v029 |

### Road furniture (6)

| Code | Asset | Placed | In | Note |
|---|---|---|---|---|
| RD-Roundabout | Roundabout + island | 2 | B |  |
| RD-Turn | Turning head (close) | 2 | B |  |
| RD-Median | Planted / concrete median | 3 | B |  |
| LIF-SpeedBump | Speed bump | 1 | B |  |
| CVR-H8 | Open drain / gutter |  | P | planned along every R2/R3 |
| RD-Kerb | Kerb |  | C | in concepts |

## BRG: Bridges and elevated structures (3 groups, 10 types)

Big linear structures built from repeating modules: the Third Mainland Bridge and the Blue Line rail viaduct.

### Third Mainland Bridge (3)

| Code | Asset | Placed | In | Note |
|---|---|---|---|---|
| BRG-TMB-Deck | Bridge deck | 1 | B | no code yet |
| BRG-TMB-Median | Deck median | 1 | B | no code yet |
| BRG-TMB-Pillar | Pier pillar | 18 | B | no code yet |

### Blue Line viaduct (4)

| Code | Asset | Placed | In | Note |
|---|---|---|---|---|
| BRG-BL-Pillar | Viaduct pillar | 50 | B | no code yet |
| BRG-BL-PierCap | Pier cap | 50 | B | no code yet |
| BRG-BL-Deck | Deck span | 50 | B | no code yet |
| BRG-BL-Band | Side band / parapet | 50 | B | no code yet |

### Other crossings (3)

| Code | Asset | Placed | In | Note |
|---|---|---|---|---|
| MOV-B | Road bridge over creek | 3 | B | no code yet |
| MOV-F | Pedestrian footbridge |  | P | Lagos signature, not placed |
| MOV-BL | Blue Line platform / station |  | P | D112, next task |

## WLK: Waterfront walkways and decks (3 groups, 9 types)

The timber network of Makoko and the waterfront outposts: walkways, footbridges, decks and jetties.

### Walkways (4)

| Code | Asset | Placed | In | Note |
|---|---|---|---|---|
| WLK-1 | Row walkway | 5 | B | 21 runs in plan |
| WLK-1X | Exposed plank / pier | 1 | B |  |
| WLK-2 | Main boardwalk / causeway | 2 | B |  |
| WLK-R | Railed connector | 1 | B |  |

### Footbridges (2)

| Code | Asset | Placed | In | Note |
|---|---|---|---|---|
| WLK-3 | Canal footbridge (+3) | 1 | B |  |
| WLK-3H | High footbridge (+7) |  | P |  |

### Decks and jetties (3)

| Code | Asset | Placed | In | Note |
|---|---|---|---|---|
| WLK-D | Deck / pier head | 1 | B |  |
| WLK-J | Jetty | 1 | B | new v029 |
| MKS-Raft | Floating raft | 14 | B | no code yet |

## CVR: Cover, walls and fences (3 groups, 17 types)

Gameplay pieces whose job is to stop bullets (hard) or hide players (soft). The single most important group for fights.

### Hard cover (8)

| Code | Asset | Placed | In | Note |
|---|---|---|---|---|
| CVR-H1 | Block wall, full | 294 | B | 34 lengths |
| CVR-H2 | Block wall, half | 369 | B | 18 lengths |
| CVR-H3 | Shipping container | 79 | B |  |
| CVR-H4 | Wreck (car / danfo / keke) | 146 | B | 3 wreck variants |
| CVR-H5 | Concrete barrier | 4 | B |  |
| CVR-H6 | Laterite outcrop / rock | 122 | B |  |
| CVR-H7 | Tyre stack | 29 | B |  |
| CVR-H9 | Generator house / transformer | 1 | B |  |

### Walls, gates, fences (3)

| Code | Asset | Placed | In | Note |
|---|---|---|---|---|
| CVR-W1 | Estate perimeter wall | 103 | B |  |
| CVR-Gate | Compound gate | 11 | B |  |
| CVR-F | Stick fence | 18 | B | cassava plots |

### Soft cover (6)

| Code | Asset | Placed | In | Note |
|---|---|---|---|---|
| CVR-S1 | Bush cluster |  | B | placed as VEG-S01 |
| CVR-S2 | Shade tree |  | B | placed as VEG-T |
| CVR-S3 | Palm |  | B | placed as VEG-P |
| CVR-S4 | Crop / tall-grass field |  | B | placed as VEG-G01 |
| CVR-S5 | Market stalls / umbrellas | 20 | B |  |
| CVR-S6 | Billboard |  | P |  |

## VEH: Vehicles and boats (2 groups, 11 types)

Anything with wheels or a hull, parked or drivable. Drivable vehicles are gameplay assets with spawns; parked ones are cover.

### Road vehicles (7)

| Code | Asset | Placed | In | Note |
|---|---|---|---|---|
| VEH-Danfo | Danfo bus (parked) | 88 | B | 61 at the Depot + 27 at kerbs |
| VEH-Car | Parked car | 28 | B | coded LIF- today |
| VEH-Tipper | Tipper truck |  | C | sand places P2_01/03 |
| VEH-Keke | Keke (tricycle) |  | C | Bus Stop concepts |
| VEH-Okada | Okada (motorbike) |  | C |  |
| VEH-Digger | Excavator |  | C | P2_08 pit |
| VEH-Hauler | Drivable hauler spawn | 3 | B | gameplay spawn |

### Boats (4)

| Code | Asset | Placed | In | Note |
|---|---|---|---|---|
| BOT-1 | Dugout canoe | 225 | B |  |
| BOT-2 | Fishing boat with outboard | 46 | B |  |
| BOT-3 | Sand barge | 3 | B |  |
| BOT-Dredge | Dredge barge + crane |  | C | P2_01 |

## VEG: Vegetation (5 groups, 27 types)

Real Lagos species, placed by biome. Few species, many instances: variety comes from scale, rotation and tint, not new models.

### Palms (5)

| Code | Asset | Placed | In | Note |
|---|---|---|---|---|
| VEG-P01 | Oil palm | 199 | B |  |
| VEG-P02 | Coconut palm | 145 | B |  |
| VEG-P03 | Raffia palm | 45 | B |  |
| VEG-P04 | Nypa palm | 12 | B |  |
| VEG-P06 | Royal palm (planted) | 8 | B |  |

### Trees (10)

| Code | Asset | Placed | In | Note |
|---|---|---|---|---|
| VEG-T01 | Mango | 300 | B |  |
| VEG-T02 | Indian almond | 43 | B |  |
| VEG-T03 | Masquerade tree | 95 | B |  |
| VEG-T04 | Neem | 126 | B |  |
| VEG-T05 | Flamboyant | 5 | B |  |
| VEG-T06 | Teak / Gmelina | 58 | B |  |
| VEG-T07 | Silk-cotton | 7 | B |  |
| VEG-T08 | Afara | 81 | B |  |
| VEG-T09 | Fig | 79 | B |  |
| VEG-T10 | Cashew | 170 | B |  |

### Shrubs and crops (7)

| Code | Asset | Placed | In | Note |
|---|---|---|---|---|
| VEG-S01 | Siam weed / guinea-grass thicket | 1103 | B | most-placed asset |
| VEG-S02 | Plantain | 213 | B |  |
| VEG-S03 | Pawpaw | 171 | B |  |
| VEG-S04 | Clipped hedge | 83 | B |  |
| VEG-S05 | Bamboo | 22 | B |  |
| VEG-S06 | Cassava plot | 18 | B |  |
| VEG-S08 | Coastal shrub (coco plum) | 841 | B |  |

### Grasses and mats (2)

| Code | Asset | Placed | In | Note |
|---|---|---|---|---|
| VEG-G01 | Tall grass clump | 218 | B |  |
| VEG-G02 | Strand creeper mat |  | B | ground layer |

### Wetland (3)

| Code | Asset | Placed | In | Note |
|---|---|---|---|---|
| VEG-W01 | Red mangrove | 4 | B |  |
| VEG-W03 | Water hyacinth mat | 137 | B |  |
| VEG-W04 | Mangrove fern | 41 | B |  |

## LIF: Life props and set dressing (4 groups, 23 types)

The small things that make it Lagos: tanks, poles and wires, stalls, signs, benches. Mostly decoration; a few double as cover.

### Estate props (9)

| Code | Asset | Placed | In | Note |
|---|---|---|---|---|
| LIF-StreetLight | Solar street light | 39 | B |  |
| LIF-Generator | Generator | 11 | B |  |
| LIF-Bench | Bench | 3 | B |  |
| LIF-Boom | Boom barrier | 2 | B |  |
| LIF-Goal | Football goal | 2 | B |  |
| LIF-Sign | Estate name wall | 1 | B |  |
| LIF-Fountain | Fountain | 1 | B |  |
| LIF-Gazebo | Gazebo | 1 | B |  |
| LIF-Playground | Playground | 1 | B |  |

### Waterfront props (5)

| Code | Asset | Placed | In | Note |
|---|---|---|---|---|
| LIF-P | Fish pen (poles + net) | 1 | B |  |
| LIF-T | Water tank on deck | 1 | B |  |
| LIF-DrumOven | Fish-smoking drum oven |  | C | P2_05 |
| LIF-Rack | Drying rack |  | C | P2_05, MKS |
| LIF-Trestle | Canoe trestle / timber stack |  | C | P2_18 |

### Street and town props (8)

| Code | Asset | Placed | In | Note |
|---|---|---|---|---|
| LIF-PolyTank | Rooftop poly water tank |  | C | in almost every concept |
| LIF-Pole | Power pole + wires |  | C | ILE, BUS |
| LIF-Stall | Market table / stall |  | C | ILE, BUS |
| LIF-Umbrella | Market umbrella | 20 | B | Depot |
| LIF-SignBoard | Direction / shop sign | 1 | B |  |
| LIF-Dish | Satellite dish / AC unit |  | C | on walls |
| LIF-Flagpole | Flagpole |  | C | school |
| LIF-SandHeap | Sand heap | 12 | B | coded LND- today |

### Monuments (1)

| Code | Asset | Placed | In | Note |
|---|---|---|---|---|
| LIF-Statue | Statue / roundabout monument | 2 | B | Depot |

## GPL: Gameplay objects (to plan) (1 groups, 6 types)

Invisible or functional objects the game logic needs. Not art, but they live on the map and must be tracked the same way.

### Spawns and markers (6)

| Code | Asset | Placed | In | Note |
|---|---|---|---|---|
| GPL-Loot | Loot spawn point | 1289 | B | stored as loot_slots on buildings |
| GPL-VehSpawn | Vehicle spawn | 3 | B |  |
| GPL-BoatSpawn | Boat spawn |  | P |  |
| GPL-PlayerSpawn | Player / lobby spawn | 1 | B | Makoko dev spawn in Roblox |
| GPL-POI | POI call-out label |  | B | labels layer |
| GPL-LootBox | Loot container / crate |  | P | special assets, D61 |
