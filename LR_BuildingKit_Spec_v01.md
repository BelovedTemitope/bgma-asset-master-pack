# Lagos Rush: Building Kit Pack, spec v01

Pack 1 of the Asset Master Pack (D130, D131). This sheet defines **every kit piece** (size, pivot, code) and a **recipe for every building type**: which pieces build it, its snapped footprint, entries, interior and loot. Blockout v030 is built from this sheet.

Status: **draft for Temitope's review**. The grid is ours for now and will be confirmed with Saheed (D133).

---

## 1. Grid and scale (applies to all four kits)

| Rule | Value | Why / source |
|---|---|---|
| Unit | 1 stud = 0.28 m; character 5 studs | D-scale, Kit Rules v03 |
| Snap | **4 studs** | D133 |
| Bay (wall module) | **16 studs** wide; **8-stud** half bay for corridors, ends and stairs | D133; 16 = CVR-H1 wall length; Roblox showcase grid |
| Storey | **12 studs floor to floor**: 1-stud slab + 11 clear | D-scale. R-INT-6 asks for 12 clear; **11 to be tested in Studio** with the mobile camera |
| Wall thickness | **1 stud**, centred on the grid line | Fixed like Fortnite's, so collision and bullet rules are the same on every wall |
| Door opening | **4 × 7** | R-BLD-3 |
| Window opening | **4 wide × 4 tall, sill at 3.5** (crouch cover height) | R-INT-7 |
| Big door / shutter | 8 × 8 (shop shutter), 12 × 10 (shed door) | |
| Rooms / corridors | Room ≥ 12 × 12 (a 16 bay gives 15 clear); corridor ≥ 6 (an 8 bay gives 7 clear) | R-BLD-3 |
| Footprints | **Multiples of 8**, most multiples of 16 | Kits always meet |
| Pivot | **Ground level, centre of the piece**; for walls, centre of the wall's base on the grid line | Skyrim kit rule |
| Roof overhang | 2 studs, outside the grid (doesn't affect snapping) | |

**Naming:** `KIT-` + kit letter (none = masonry, `T` timber, `H` steel hall, `X` tower) + part + size + opening. Variant suffix `-01`…`-04` (D132). Example: `KIT-W16D-02` = masonry wall, 16 wide, with a door, look variant 2. Colour and age come from a material set (`Mat = M3`), never a new code.

---

## 2. K1 Masonry kit (block and plaster): 41 pieces

Builds: H1, H2, Q1, U1, T1, S1, S2, G1–G5, S3, E1, C1, C2 body, X4, landmark bodies in town.

### 2.1 Walls (one storey tall: 12 high × 1 thick)
| Code | Piece | Size (w × h) | Openings |
|---|---|---|---|
| KIT-W16 | Wall, solid | 16 × 12 | — |
| KIT-W16W | Wall, one window | 16 × 12 | 1 window, centred |
| KIT-W16WW | Wall, two windows | 16 × 12 | 2 windows |
| KIT-W16D | Wall, door | 16 × 12 | 1 door 4×7, centred |
| KIT-W16DW | Wall, door + window | 16 × 12 | door left, window right |
| KIT-W16B | Wall, balcony door | 16 × 12 | door 4×7 opening onto a balcony |
| KIT-W16S | Wall, shop shutter | 16 × 12 | shutter opening 8 × 8 |
| KIT-W16G | Wall, broken / breach | 16 × 12 | ragged hole 6 × 6 (R-INT-1 extra route) |
| KIT-W8 | Half bay, solid | 8 × 12 | — |
| KIT-W8D | Half bay, door | 8 × 12 | door |
| KIT-W8W | Half bay, window | 8 × 12 | window |
| KIT-WC | Corner post | 1 × 1 × 12 | — |
| KIT-WI16 / KIT-WI8 / KIT-WI16D / KIT-WI8D | Interior partitions (0.5 thick) | 16 or 8 × 11 | solid or door |
| KIT-WP16 / KIT-WP8 | Parapet / half wall | 16 or 8 × 3.5 | crouch cover, = CVR-H2 height |

### 2.2 Floors, roofs and stairs
| Code | Piece | Size | Notes |
|---|---|---|---|
| KIT-F16 | Floor/ceiling slab | 16 × 16 × 1 | |
| KIT-F8 | Half slab | 8 × 16 × 1 | |
| KIT-FS | Slab with stair hole | 16 × 16 × 1 | hole 8 × 12 |
| KIT-S12 | Internal stair, straight | 8 × 16, rises 12 | central stair (R-BLD-2) |
| KIT-S12E | External stair with landing | 8 × 20, rises 12 | T1, G1 (R-INT-5) |
| KIT-S12R | Roof hatch stair | 8 × 12 | roof access, T1/U1 |
| KIT-BAL16 | Balcony slab + rail | 16 × 6 | rail 3.5 high = crouch cover |
| KIT-RAIL16 / 8 | Rail / burglar-bar balustrade | 16 or 8 × 3.5 | see-through cover |
| KIT-RF16 | Flat roof slab | 16 × 16 | with KIT-WP parapets |
| KIT-RZG16 | Zinc gable roof bay | 16 deep, spans 16–40 | corrugated, 2 overhang |
| KIT-RZL16 | Zinc lean-to bay | 16 deep | back extensions, Q1 |
| KIT-RZH | Hip roof set (end + bay) | modular | estate G3/G4 (tile material set) |
| KIT-RREBAR | Rebar stubs strip | 16 long | unfinished U1 top |

### 2.3 Openings, inserts and trim (separate pieces that sit in openings)
| Code | Piece | Notes |
|---|---|---|
| KIT-OD | Door leaf (wood / metal) | swings; can be left open |
| KIT-OS | Roller shutter | loud entry (S1, S2) |
| KIT-OW | Window: glass + frame | |
| KIT-OWL | Louvre window (Naco glass louvres) | Lagos signature |
| KIT-OWB | Burglar-proof bars | see and shoot through, can't climb (R-INT-7) |
| KIT-BAND | Storey band / drip | façade trim per storey |
| KIT-PLINTH | Plinth strip | base of walls |
| KIT-SIGN | Shop fascia board | S1, S2 |
| KIT-TANKSTAND | Rooftop poly tank on stand | silhouette; links to LIF-PolyTank |

**K1 material sets (4–6, D132):** M1 raw sandcrete block (unfinished) · M2 village plaster, faded cream/ochre · M3 town paint, bright (blue, pink, green, yellow) · M4 estate render, white/grey with trims · M5 weathered and mould-streaked · roofs: rusted zinc, new zinc, long-span aluminium (estate), tile-look (estate).

---

## 3. K2 Timber stilt kit: 15 pieces

Builds: M1, M3, M4, M5, waterfront outposts (WFT), jetties; shares deck pieces with WLK-.

| Code | Piece | Size | Notes |
|---|---|---|---|
| KIT-TW8 / KIT-TW8D / KIT-TW8W | Plank wall: solid / door / window flap | 8 × 9 | single storey height 9 (stilt houses are low) |
| KIT-TW8H | Plank wall, tall (hall) | 8 × 14 | M4 halls |
| KIT-TP | Stilt pile | Ø1, 6–10 long | sunk into the water |
| KIT-TD8 | Deck section | 8 × 8 | = WLK-D module |
| KIT-TD8E | Deck edge with rail | 8 long | |
| KIT-TF8 | Plank floor | 8 × 8 | |
| KIT-TR8 | Zinc roof sheet bay | 8 deep | gable or mono-pitch |
| KIT-TL | Ladder | 8 high | water to deck |
| KIT-TST | Timber stair, one storey | 4 × 12 | M3 upper floor |
| KIT-TRACK | Fish-drying rack | 8 × 2 × 4 | waist cover (M5) |
| KIT-TWK4 / KIT-TWK8 | Walkway plank run | 4 wide, 8 or 16 long | = WLK-1, WLK-1X |
| KIT-TBR | Footbridge step | 4 × 8, +3 or +7 | = WLK-3, WLK-3H |

**K2 material sets:** T1 dark weathered plank · T2 patched plank with zinc sheets · T3 painted plank (church/school hall).

Grid note: stilt pieces use the **8-stud** module; one 16-stud masonry bay = two timber bays, so the waterfront meets the land kit cleanly.

---

## 4. K3 Steel hall kit: 10 pieces

Builds: W1 warehouses, Depot sheds, F1 canopy, boatyard sheds (P2_18), market roofs, open sheds on land.

| Code | Piece | Size | Notes |
|---|---|---|---|
| KIT-HFRAME | Portal frame (columns + rafter) | spans 32/48/64, 16 apart | 1 frame per bay |
| KIT-HCLAD16 | Wall cladding panel | 16 × 14 | corrugated sheet |
| KIT-HCLAD16L | Cladding with clerestory strip | 16 × 14 | light band at top |
| KIT-HDOOR | Big sliding door | 12 × 10 | vehicles can enter |
| KIT-HDOORS | Side door | 4 × 7 | |
| KIT-HROOF16 | Roof sheet bay | 16 deep | |
| KIT-HOPEN16 | Open-sided bay (no cladding) | 16 | sheds, market |
| KIT-HCANOPY | Canopy roof + columns | 16 × 16 modules | F1 filling station |
| KIT-HGANTRY | Internal gantry / mezzanine strip | 16 × 6, at +8 | INT-H high-low fights |
| KIT-HLADDER | Gantry ladder | 8 high | |

**K3 material sets:** S1 galvanised grey · S2 rusted · S3 painted (Depot blue/red, brand-free).

---

## 5. K4 Tower kit: 10 pieces

Builds: X1 tank stands, X2 estate water tower, X5 telecom mast, the mosque minaret, the P2_11 jetty tower.

| Code | Piece | Size | Notes |
|---|---|---|---|
| KIT-XLEG8 | Tank-stand leg segment + bracing | 8 × 8 footprint, 8 high | stack 1–4 |
| KIT-XTANK | Tank platform + poly tanks | 8 × 8 | 2–4 tanks |
| KIT-XSHAFT | Concrete shaft segment | 8 × 8, 8 high | X2 |
| KIT-XBOWL | Elevated tank bowl | Ø22 | X2 top |
| KIT-XLAT | Lattice mast segment | 3 × 3, 8 high | X5 |
| KIT-XANT | Antenna crown | 3 × 3 | X5 top |
| KIT-XMIN | Minaret shaft segment | Ø6, 8 high | C2 |
| KIT-XMINCAP | Minaret balcony + cap | Ø8 | high point |
| KIT-XLAD | Caged ladder run | 8 high | |
| KIT-XLAND | Landing platform | 6 × 6 | every 16 of ladder |

**K4 material sets:** X1 concrete · X2 painted steel · X3 black/blue poly tanks.

---

## 6. Building recipes: the 29 types

Footprints are **current → snapped** (proposal for v030). Bays = front × depth in 16-stud bays (½ = an 8 bay). Entries count doors + other routes (R-BLD-1, R-INT-1). Loot = slots per copy (Kit Rules v03). Variants = planned look variants (≤ 4, D132); interior variants ≤ 2 (R-INT-3).

### 6.1 Village and residential (K1)
| Type | Snapped footprint | Bays | Storeys | Walls used | Roof | Entries | Interior | Loot | Variants |
|---|---|---|---|---|---|---|---|---|---|
| **BLD-H1** rooming house | 32×54 → **32×56** | 2 × 3½ | 1 | W16W, W8D (both ends), WI16D partitions, WC | RZG16 | 2 ends + back yard + 1 window | INT-C | 4–6 | 3 (M2, M3, M5) |
| **BLD-H2** family house | 36×40 → **40×40** | 2½ × 2½ | 2 | W16W, W16D, W16B, FS, S12, BAL16 | RZG16 or RF16 | 2–3 + balcony drop | INT-L | 4 | 4 |
| **BLD-Q1** boys' quarters | **16×24** | 1 × 1½ | 1 | W16D, W8W | RZL16 | 1 + window | INT-R | 1–2 | 2 |
| **BLD-U1** unfinished shell | 30×40 → **32×40** | 2 × 2½ | 1–2 | Same as H2 **without** inserts, plaster or roof; W16G breaches; RREBAR | none (slab as vantage) | many | INT-H | 2–3 | 3 (1-storey, 2-storey, half-built) |

### 6.2 Town and commercial (K1, K3)
| Type | Snapped footprint | Bays | Storeys | Pieces | Roof | Entries | Interior | Loot | Variants |
|---|---|---|---|---|---|---|---|---|---|
| **BLD-T1** tenement | 30×48 → **32×48** | 2 × 3 | 2–4 | W16W/WW, W16B, FS, S12 + S12E, BAL16, OWB | RF16 + WP16 + S12R | 2 + external stair + roof | INT-S | 6–10 | 3 (2, 3, 4 storeys) |
| **BLD-S1** shophouse | 27×46 → **24×48** | 1½ × 3 | 2–3 | Ground W16S + OS; upper W16W, BAL16; S12 | RF16 or RZG16 | shutter + back door + balcony | INT-R (shop) / INT-S (upper) | 4–6 | 4 |
| **BLD-S2** lock-up shop row | **12×12 per unit** (rows of 3–6) | ¾ per unit | 1 | W16S cut to 12, OS, KIT-SIGN | RZL16 | 1 shutter each | — | 1 each | 2 |
| **BLD-K1** container kiosk | 10×20 | — | 1 | **Prop, not kit** (= CVR-H3 with a hatch) | — | 1 | INT-R | 1 | colour sets only |
| **BLD-W1** warehouse | 60×120 → **64×120** | K3: 4 frames × 7½ bays | 1 high | HFRAME, HCLAD16, HDOOR, HGANTRY | HROOF16 | 3+ big doors | INT-H | 6–8 | 2 |

### 6.3 Civic, religious, school (K1, K3, K4)
| Type | Snapped footprint | Pieces | Hero piece (unique) | Entries | Interior | Loot | Variants |
|---|---|---|---|---|---|---|---|
| **BLD-C1** church hall | 50×90 → **48×88** | K1 long bays W16W, tall walls (2 storeys high, no floor), RZG16 | Front gable with cross | 3 | INT-H | 4 | 2 |
| **BLD-C2** mosque | **40×40** + minaret | K1 walls, RF16; K4 XMIN + XMINCAP | Dome | 2–3 + minaret | INT-H | 3 | 2 |
| **BLD-E1** school block | wings **32×120**, L or U | K1 W16W/WW, open corridor BAL16 + RAIL along the yard side, S12E | Gate arch (with CMP-D) | many | INT-Y | 6–8 | 2 |
| **BLD-F1** filling station | canopy **48×64** + shop **24×32** | K3 HCANOPY; shop from K1 | Pump islands (props) | open | INT-R | 3 | 2 (brand-free) |

### 6.4 Gated estate, TMH (K1 + estate material set M4)
| Type | Snapped footprint | Storeys | Pieces | Entries | Interior | Loot | Variants |
|---|---|---|---|---|---|---|---|
| **BLD-G1** government block | 30×72 → **32×72** | 2 + flat roof | W16W/WW, open central stairwell (S12 + FS), access balcony BAL16, RF16 + WP16 | 2 stairs + ground-flat back doors | INT-S | 8–10 | 2 |
| **BLD-G2** King Tower | **40×60** (on grid already ±) | 6 + roof | G1 pieces stacked; S12E fire stair | central + fire stair + roof | INT-S | 14 | 1 (hero) — crown + mast KIT-XLAT unique |
| **BLD-G3** detached duplex | 36×34 → **40×32** | 2 | W16W, W16D, W16B, BAL16, FS, S12 | front, kitchen back, balcony drop | INT-L | 4 | 4 |
| **BLD-G4** terrace row | 27×42 → **24×40 per unit**, rows of 4 | 2 | G3 pieces in a row; middle units closed façades | front + back (end units) | INT-L | 3 (end units) | 2 |
| **BLD-G5** clubhouse | 60×38 → **64×40** | 1 + roof terrace | W16WW, glazed W16D, RF16 + WP16, S12E to roof | 3 + roof stair | INT-L | 6 | 1 |
| **BLD-S3** gatehouse / office | 16×11 · 22×14 → **16×12 · 24×16** | 1 | W8W, W16D, RF16 | 2 | INT-R | 2 | 2 |

### 6.5 Utility and towers (K4, K1)
| Type | Snapped footprint | Pieces | Notes | Loot |
|---|---|---|---|---|
| **BLD-X1** tank stand | 10×10 → **8×8** | XLEG8 × 1–3, XTANK, XLAD | high point, exposed | 1 |
| **BLD-X2** estate water tower | shaft 9×9 → **8×8**, bowl Ø22 | XSHAFT × 6, XBOWL, XLAD + XLAND | landmark, 56 high | 2 |
| **BLD-X4** borehole house | 22×14 → **24×16** | K1 W16D, W8W, RF16 | utility, INT-R | 2 |
| **BLD-X5** telecom mast | 3×3 | XLAT × 4, XANT | silhouette only, not climbable (S1) | — |

### 6.6 Makoko stilt (K2)
| Type | Snapped footprint | Pieces | Entries | Interior | Loot | Variants |
|---|---|---|---|---|---|---|
| **BLD-M1** one-room stilt house | 20×24 → **24×24** (deck 32×32) | TW8/TW8D/TW8W, TP, TD8, TF8, TR8 | walkway door + canal door | INT-R | 1–2 | 3 (T1, T2) |
| **BLD-M3** two-storey stilt house | 22×26 → **24×24** | M1 + TST + second floor + front balcony | 2 + balcony | INT-S | 2–4 | 2 |
| **BLD-M4** stilt hall | 36×60 → **32×56** | TW8H, TP, TD8, TR8 (tall gable) | 3+ | INT-H | 6 | 2 (church, school) |
| **BLD-M5** fish-smoking shed | 24×30 → **24×32** | TP, TD8, TR8 on posts, TRACK racks, no walls | open all round | open | 2 | 2 |

### 6.7 Landmark one-offs
| Type | Approach |
|---|---|
| **BLD-L1** (one per P1) | Body from kits; the silhouette piece is a unique hero model (e.g. the Makoko A-frame hall, the Depot roof) |
| **Depot structures** (now `DFD-STRUCT`, to recode as BLD-W1 / BLD-S3 / BLD-L1 in v030) | K3 sheds + K1 office; the Depot roof is the hero piece |

---

## 7. Totals

| Kit | Pieces (approx.) | Builds |
|---|---|---|
| K1 Masonry | 41 | 20 types |
| K2 Timber stilt | 15 | 4 types + walkways/jetties |
| K3 Steel hall | 10 | 2 types + canopy, sheds, market roofs |
| K4 Tower | 10 | 4 types + minaret, jetty tower |
| Hero pieces | about 10 | church gable, dome, King Tower crown, estate gate wall + sign, Depot roof, Makoko A-frame, school gate arch, pump islands, dredge (P2_01), mast top |
| **All** | **76 kit pieces + about 10 hero pieces** | **29 building types** |

## 8. Checks before blockout v030

1. Every recipe meets R-BLD-1 (2 exits), R-INT-1 (one extra route), R-INT-2 (a loop when 3+ rooms) and R-INT-3 (≤ 2 interior variants).
2. Snapped footprints keep each type within one grid step of its plan size, so the master layout and compounds still fit; any that don't are listed in the v030 report.
3. Storey clear height 11 vs R-INT-6's 12: test with the mobile camera in Studio; if it clips, the storey becomes 13 (floor to floor) and the kit heights change in v02.
4. Wall thickness 1 vs CVR-H1 compound walls at 1.2: keep cover walls separate (they're CVR, not KIT) or align them to 1 in Pack 2.

## 9. Next

1. Temitope reviews this sheet.
2. Grey-box the four kits in Blender (`Blockout/LR_BuildingKit_v01.blend`), contact sheet of every piece, and 4 proof buildings (H1, H2, T1, M1) assembled from the kit.
3. Blockout v030 from the kit.
4. Concept breakdown sheets per kit (masonry first) in Flow, over the grey-box.
