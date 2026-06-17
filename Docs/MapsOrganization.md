# Maps Folder Organization

`Maps/` is organized into subfolders by location and category. This is purely an
organizational layout — it does **not** affect behavior:

- The `Maps` resource pack uses `RecursiveInput = True` (`TLA.fomain`), so the baker
  picks up `.fomap`/`.foloc` files from any subfolder automatically.
- Maps and locations are identified by their **proto name** (filename / `$Name`) and
  reference each other by proto name (e.g. `Grid_ToMap = redding`), never by file path.
- No code, config, or generated file (`Content.fos`) references map paths, so files can
  be moved freely between these folders.

Verification after the move: a full `ForceBakeResources` baked **550** maps — identical to
the pre-reorganization count, confirming nothing was lost or broken.

## Structure

| Folder | Contents |
| --- | --- |
| `Towns/<Town>/` | A town's location protos (`.foloc`) and all its maps (`.fomap`) |
| `Encounter/` | Generic random-encounter maps (terrain/city/cave/etc.) |
| `Encounter/SpecialEncounter/` | Special encounters (`se_*` maps + named special-encounter locations) |
| `Encounter/Raiders/` | Raider camps / caves |
| `Quest/` | Quest maps (`q_*`) |
| `Replication/` | Replication (respawn) maps |
| `Special/` | Intro, Purgatory, Primal Tribe, Barter Ground |

## Categorization rules (filename prefix -> folder)

Applied in order; first match wins. Anything unmatched defaults to `Encounter/SpecialEncounter`.

| Prefix(es) | Folder |
| --- | --- |
| `replication*`, `repl*` | `Replication` |
| `q_*` | `Quest` |
| `se_*` | `Encounter/SpecialEncounter` |
| `raiders*` | `Encounter/Raiders` |
| `arroyo*` | `Towns/Arroyo` |
| `klamath*` | `Towns/Klamath` |
| `modoc*` | `Towns/Modoc` |
| `mariposa*` | `Towns/Mariposa` |
| `navarro*` | `Towns/Navarro` |
| `redding*`, `redd*` | `Towns/Redding` |
| `broken*` | `Towns/BrokenHills` |
| `newr*`, `new_reno*` | `Towns/NewReno` |
| `ncr*` | `Towns/NCR` |
| `cath*`, `church_of_atom*` | `Towns/Cathedral` |
| `gecko*`, `geck*` | `Towns/Gecko` |
| `sad*`, `silo*`, `sierra_army_depot*` | `Towns/SierraArmyDepot` |
| `hubologists*`, `sf*`, `san_francisco*` | `Towns/SanFrancisco` |
| `vcity*`, `vc*` | `Towns/VaultCity` |
| `vault*`, `v<digits>*` | `Towns/Vaults` |
| `den*` | `Towns/Den` |
| `desert*`, `coast*`, `mountain*`, `cavern*`, `ocean*`, `warehouse*`, `atoll*`, `mad*`, `city*`, `e_*` | `Encounter` |
| `intro*`, `purgatory*`, `hub_purgatory*`, `primal*`, `barter*`, `sacr*` | `Special` |

## File mapping

### `Maps/Encounter/`

- android.foloc
- atoll.foloc
- atoll.fomap
- bridge_keeper.foloc
- broc_and_xander.foloc
- bunker_bos.foloc
- cafe.foloc
- cavern_0.foloc
- cavern_1.foloc
- cavern_2.foloc
- cavern_3.foloc
- cavern_4.foloc
- cavern_5.foloc
- city_1.foloc
- city_2.foloc
- city_3.foloc
- city_4.foloc
- city_5.foloc
- city_6.foloc
- city_7.foloc
- city_8.foloc
- coast_1.foloc
- coast_10.foloc
- coast_11.foloc
- coast_2.foloc
- coast_3.foloc
- coast_4.foloc
- coast_5.foloc
- coast_6.foloc
- coast_7.foloc
- coast_8.foloc
- coast_9.foloc
- dappo_lost_caravan.foloc
- desert_1.foloc
- desert_10.foloc
- desert_11.foloc
- desert_12.foloc
- desert_2.foloc
- desert_3.foloc
- desert_4.foloc
- desert_5.foloc
- desert_6.foloc
- desert_7.foloc
- desert_8.foloc
- desert_9.foloc
- doll_holodisk.foloc
- doughnut.foloc
- e_cave0_in.fomap
- e_cave0_out.fomap
- e_cave1_in.fomap
- e_cave1_out.fomap
- e_cave2_in.fomap
- e_cave2_out.fomap
- e_cave3_in.fomap
- e_cave3_out.fomap
- e_cave4_in.fomap
- e_cave4_out.fomap
- e_cave5_in.fomap
- e_cave5_out.fomap
- e_cave5_out1.fomap
- e_city1.fomap
- e_city2.fomap
- e_city3.fomap
- e_city4.fomap
- e_city4_sewer.fomap
- e_city5.fomap
- e_city6.fomap
- e_city7.fomap
- e_city8.fomap
- e_coast1.fomap
- e_coast10.fomap
- e_coast11.fomap
- e_coast12.fomap
- e_coast2.fomap
- e_coast3.fomap
- e_coast4.fomap
- e_coast5.fomap
- e_coast5_cave.fomap
- e_coast6.fomap
- e_coast7.fomap
- e_coast8.fomap
- e_coast9.fomap
- e_desert1.fomap
- e_desert10.fomap
- e_desert11.fomap
- e_desert12.fomap
- e_desert2.fomap
- e_desert3.fomap
- e_desert4.fomap
- e_desert5.fomap
- e_desert6.fomap
- e_desert7.fomap
- e_desert8.fomap
- e_desert9.fomap
- e_mountain1.fomap
- e_mountain2.fomap
- e_mountain3.fomap
- e_mountain4.fomap
- e_mountain5.fomap
- e_mountain6.fomap
- e_mountain7.fomap
- e_ocean1.fomap
- e_ocean2.fomap
- e_ocean3.fomap
- e_ocean_raft.fomap
- e_ocean_trader.fomap
- first_special.foloc
- guardian_of_forever.foloc
- kidnappers_hideout.foloc
- killer_bunny.foloc
- king_arthur_and_knights.foloc
- knights_of_the_wasteland.foloc
- mad_brahmins.foloc
- mad_scientists_lab.foloc
- mountain_1.foloc
- mountain_2.foloc
- mountain_3.foloc
- mountain_4.foloc
- mountain_5.foloc
- mountain_6.foloc
- mountain_7.foloc
- nancy_and_sid.foloc
- ocean_1.foloc
- ocean_2.foloc
- ocean_3.foloc
- ocean_raft.foloc
- ocean_trader.foloc
- pariahs.foloc
- rats_colony.foloc
- se_android_basement.fomap
- se_android_entrance.fomap
- se_atom_ground.fomap
- se_atom_level1.fomap
- se_atom_reactor.fomap
- se_bax_church.fomap
- se_bax_underground.fomap
- se_bridge.fomap
- se_bunker_bs.fomap
- se_cafe.fomap
- se_children.fomap
- se_doughnut.fomap
- se_doughnut_basement.fomap
- se_first.fomap
- se_forvr.fomap
- se_forvr_v13.fomap
- se_head.fomap
- se_holo1_bunker.fomap
- se_holo1_ground.fomap
- se_holo2_basement.fomap
- se_holo2_ground.fomap
- se_holo3_cave.fomap
- se_holo3_ground.fomap
- se_holy1.fomap
- se_holy21.fomap
- se_holy22.fomap
- se_kotw_ground.fomap
- se_kotw_level1.fomap
- se_kotw_level2.fomap
- se_kotw_level3.fomap
- se_mad.fomap
- se_pariah.fomap
- se_shuttle.fomap
- se_teleport.fomap
- se_teleport_dung.fomap
- se_tim.fomap
- se_toxic.fomap
- se_truck_ncola.fomap
- se_ufo.fomap
- se_unwashed.fomap
- se_whale.fomap
- se_woodsman.fomap
- se_zerg_cave.fomap
- se_zerg_lab.fomap
- se_zerg_town.fomap
- soldiers_bunker.foloc
- star_trek_shuttle.foloc
- tim_cain.foloc
- tin_woodsman.foloc
- toxic.foloc
- trappers_home.foloc
- truck_nuka_cola.foloc
- ufo.foloc
- unwashed_villagers.foloc
- wanamingo_cavern.foloc
- warehouse.foloc
- warehouse1.foloc
- warehouse2.foloc
- warehouse3.foloc
- warehouse4.foloc
- warehouse5.foloc
- warehouse6.foloc
- wasteland_children.foloc
- whale.foloc
- zergs_laboratory.foloc

### `Maps/Encounter/Raiders/`

- raiders.foloc
- raiders_camp_1.foloc
- raiders_camp_2.foloc
- raiders_cave1.fomap
- raiders_cave2.fomap
- raiders_cave3.fomap
- raiders_enter.fomap
- raiders_exit.fomap

### `Maps/Encounter/SpecialEncounter/`

- android.foloc
- bridge_keeper.foloc
- broc_and_xander.foloc
- bunker_bos.foloc
- cafe.foloc
- dappo_lost_caravan.foloc
- doll_holodisk.foloc
- doughnut.foloc
- first_special.foloc
- guardian_of_forever.foloc
- kidnappers_hideout.foloc
- killer_bunny.foloc
- king_arthur_and_knights.foloc
- knights_of_the_wasteland.foloc
- nancy_and_sid.foloc
- pariahs.foloc
- rats_colony.foloc
- se_android_basement.fomap
- se_android_entrance.fomap
- se_atom_ground.fomap
- se_atom_level1.fomap
- se_atom_reactor.fomap
- se_bax_church.fomap
- se_bax_underground.fomap
- se_bridge.fomap
- se_bunker_bs.fomap
- se_cafe.fomap
- se_children.fomap
- se_doughnut.fomap
- se_doughnut_basement.fomap
- se_first.fomap
- se_forvr.fomap
- se_forvr_v13.fomap
- se_head.fomap
- se_holo1_bunker.fomap
- se_holo1_ground.fomap
- se_holo2_basement.fomap
- se_holo2_ground.fomap
- se_holo3_cave.fomap
- se_holo3_ground.fomap
- se_holy1.fomap
- se_holy21.fomap
- se_holy22.fomap
- se_kotw_ground.fomap
- se_kotw_level1.fomap
- se_kotw_level2.fomap
- se_kotw_level3.fomap
- se_mad.fomap
- se_pariah.fomap
- se_shuttle.fomap
- se_teleport.fomap
- se_teleport_dung.fomap
- se_tim.fomap
- se_toxic.fomap
- se_truck_ncola.fomap
- se_ufo.fomap
- se_unwashed.fomap
- se_whale.fomap
- se_woodsman.fomap
- se_zerg_cave.fomap
- se_zerg_lab.fomap
- se_zerg_town.fomap
- soldiers_bunker.foloc
- star_trek_shuttle.foloc
- tim_cain.foloc
- tin_woodsman.foloc
- toxic.foloc
- trappers_home.foloc
- truck_nuka_cola.foloc
- ufo.foloc
- unwashed_villagers.foloc
- wanamingo_cavern.foloc
- wasteland_children.foloc
- whale.foloc
- zergs_laboratory.foloc

### `Maps/Quest/`

- q_arroyo_mynoc_defence1.fomap
- q_arroyo_mynoc_defence2.fomap
- q_cave_wan.fomap
- q_dappo_lost_c.fomap
- q_hub_judgement.fomap
- q_hub_lab_basement.fomap
- q_hub_lab_ground.fomap
- q_modoc_farm.fomap
- q_modoc_vamp_cave.fomap
- q_modoc_vamp_farm.fomap
- q_ncr_siege1.fomap
- q_ncr_siege2.fomap
- q_ncr_siege3.fomap
- q_ncr_siege4.fomap
- q_ncr_siege4_cave.fomap
- q_ncr_siege5.fomap
- q_nr_wri_kidnap.fomap
- q_racing_checkpoint.fomap
- q_rats_in.fomap
- q_rats_out.fomap
- q_silo1.fomap
- q_silo2.fomap
- q_silo3.fomap
- q_silo4.fomap
- q_silo5.fomap
- q_silo_ambush.fomap
- q_slim_sidnancy.fomap
- q_vc_attack_out.fomap
- q_vc_recon_in.fomap
- q_vc_recon_out.fomap
- q_warehouse.fomap
- q_warehouse1.fomap
- q_warehouse2.fomap
- q_warehouse3.fomap
- q_warehouse4.fomap
- q_warehouse5.fomap
- q_warehouse6_1.fomap
- q_warehouse6_2.fomap

### `Maps/Replication/`

- repl1.fomap
- repl2.fomap
- repl3.fomap
- repl4.fomap
- repl4a.fomap
- repl_bank_broken.fomap
- repl_bank_den.fomap
- repl_bank_gecko.fomap
- repl_bank_klamath.fomap
- repl_bank_modoc.fomap
- repl_bank_ncr.fomap
- repl_bank_newreno.fomap
- repl_bank_redding.fomap
- repl_bank_sf.fomap
- repl_bank_vcity.fomap
- repl_ground.fomap
- repl_ground4.fomap
- repl_hell.fomap
- replication_1.foloc
- replication_2.foloc
- replication_3.foloc
- replication_4.foloc
- replication_hell.foloc

### `Maps/Special/`

- barter_ground.foloc
- barter_ground.fomap
- hub_purgatory.foloc
- intro_init.fomap
- intro_martin.foloc
- intro_martin.fomap
- primal_tribe.foloc
- primal_tribe.fomap
- purgatory1.fomap
- purgatory2.fomap
- purgatory3.fomap
- sacr_satter.fomap

### `Maps/Towns/Arroyo/`

- arroyo.foloc
- arroyo.fomap
- arroyo_bridge.fomap
- arroyo_garden.fomap
- arroyo_temple.fomap
- arroyo_temple_entrance.fomap

### `Maps/Towns/BrokenHills/`

- broken.fomap
- broken_basement.fomap
- broken_caves1.fomap
- broken_caves2.fomap
- broken_dungeon.fomap
- broken_hills.foloc
- broken_mine.fomap

### `Maps/Towns/Cathedral/`

- cath_enter.fomap
- cath_level1.fomap
- cath_level2.fomap
- cath_level3.fomap
- cath_main.fomap
- cathedral.foloc
- church_of_atom.foloc

### `Maps/Towns/Den/`

- den.foloc
- den.fomap
- den_carstop.fomap
- den_leanna_base.fomap
- den_racing_checkpoint.foloc

### `Maps/Towns/Gecko/`

- geck01.fomap
- geck02.fomap
- geck_city.foloc
- gecko.foloc
- gecko_dungeon.fomap
- gecko_junkyard.fomap
- gecko_power_plant.fomap
- gecko_settlement.fomap

### `Maps/Towns/Klamath/`

- klamath.foloc
- klamath.fomap
- klamath_canyon.fomap
- klamath_graz.fomap
- klamath_mall.fomap
- klamath_ratcv1.fomap
- klamath_ratcv2.fomap
- klamath_ratcv3.fomap
- klamath_toilet.fomap
- klamath_trap.fomap

### `Maps/Towns/Mariposa/`

- mariposa.foloc
- mariposa_enter.fomap
- mariposa_level1.fomap
- mariposa_level2.fomap
- mariposa_level3.fomap
- mariposa_level4.fomap

### `Maps/Towns/Modoc/`

- modoc.foloc
- modoc.fomap
- modoc_farm.foloc
- modoc_vampire.foloc

### `Maps/Towns/NCR/`

- ncr.foloc
- ncr_bazaar.fomap
- ncr_council.fomap
- ncr_downtown.fomap
- ncr_ranch.fomap
- ncr_siege_1.foloc
- ncr_siege_2.foloc
- ncr_siege_3.foloc
- ncr_siege_4.foloc
- ncr_siege_5.foloc

### `Maps/Towns/Navarro/`

- navarro.foloc
- navarro_base.fomap
- navarro_gasoline.fomap
- navarro_sub1.fomap
- navarro_sub2.fomap

### `Maps/Towns/NewReno/`

- new_reno.foloc
- newr1.fomap
- newr2.fomap
- newr3.fomap
- newr4.fomap
- newr4_base.fomap
- newr_bish1.fomap
- newr_bish2.fomap
- newr_box.fomap
- newr_carstop.fomap
- newr_desp.fomap
- newr_desp_base.fomap
- newr_eld.fomap
- newr_salv.fomap

### `Maps/Towns/Redding/`

- redding.foloc
- redding_lost.fomap
- redding_mine.fomap
- redding_miners.fomap
- redding_outer.fomap
- redding_tun1.fomap
- redding_tun2.fomap
- redding_wan1.fomap
- redding_wan2.fomap

### `Maps/Towns/SanFrancisco/`

- hubologists_initialization.foloc
- hubologists_lab.foloc
- hubologists_victims.foloc
- san_francisco.foloc
- sf_bro.fomap
- sf_china.fomap
- sf_dock.fomap
- sf_emp.fomap
- sf_hubb.fomap
- sf_shi.fomap
- sf_shuttle.fomap
- sf_tanker.fomap
- sf_tanker2.fomap
- sf_tanker3.fomap

### `Maps/Towns/SierraArmyDepot/`

- sad_enter.fomap
- sad_level1.fomap
- sad_level2.fomap
- sad_level3.fomap
- sad_level4.fomap
- sad_powersub.fomap
- sierra_army_depot.foloc
- silo_ambush_farm.foloc
- silo_base.foloc

### `Maps/Towns/VaultCity/`

- vc_recon.foloc
- vc_recon_mutants.foloc
- vcity.fomap
- vcity_courtyard.fomap
- vcity_vault_1.fomap
- vcity_vault_2.fomap
- vcity_vault_3.fomap

### `Maps/Towns/Vaults/`

- v13_0.fomap
- v13_1.fomap
- v13_2.fomap
- v13_3.fomap
- v13_out1.fomap
- v13_out2.fomap
- v15_door.fomap
- v15_level1.fomap
- v15_level2.fomap
- v15_level3.fomap
- v15_village.fomap
- vault_13.foloc
- vault_15.foloc
- vault_city.foloc
- vault_dwellers_head.foloc
