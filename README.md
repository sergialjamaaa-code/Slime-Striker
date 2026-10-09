{
  "project": {
    "working_title": "Slime Strike",
    "one_sentence": "Estilo CS2 por equipos, pero disparas slimes y puedes absorber las balas-slime de otras armas para devolverlas.",
    "host_game": { "slug": "slime-rancher-2", "role": "primary", "engine": "unity", "loader": "melonloader" },
    "companions": [
      { "slug": "counter-strike-2", "role": "companion", "reads": ["weapon models", "weapon sounds"], "ships_cs2_files": false, "launched_with_mod": false }
    ],
    "mode": "multiplayer, teams (attackers vs defenders)",
    "first_playable": "3 weapons, each with its slime type, plus absorb-bullets",
    "later": ["return absorbed bullets (throw back)", "slime bomb plant/defuse", "full rounds", "maps"]
  },

  "sheet_weapons": {
    "columns": ["id", "cs2_source_asset", "model_path_token", "sound_path_token", "slime_ammo_id", "damage", "fire_rate_rps", "clip_size", "reload_s", "verified"],
    "rows": [
      { "id": "ak47",  "cs2_source_asset": null, "model_path_token": "{game:counter-strike-2}", "sound_path_token": "{game:counter-strike-2}", "slime_ammo_id": "slime_rapid", "damage": null, "fire_rate_rps": null, "clip_size": null, "reload_s": null, "verified": false },
      { "id": "awp",   "cs2_source_asset": null, "model_path_token": "{game:counter-strike-2}", "sound_path_token": "{game:counter-strike-2}", "slime_ammo_id": "slime_heavy", "damage": null, "fire_rate_rps": null, "clip_size": null, "reload_s": null, "verified": false },
      { "id": "deagle","cs2_source_asset": null, "model_path_token": "{game:counter-strike-2}", "sound_path_token": "{game:counter-strike-2}", "slime_ammo_id": "slime_burst", "damage": null, "fire_rate_rps": null, "clip_size": null, "reload_s": null, "verified": false }
    ]
  },

  "sheet_slime_ammo": {
    "columns": ["id", "base_sr2_slime", "projectile_speed", "on_hit_effect", "absorbable", "returnable_later", "verified"],
    "rows": [
      { "id": "slime_rapid", "base_sr2_slime": null, "projectile_speed": null, "on_hit_effect": null, "absorbable": true, "returnable_later": true, "verified": false },
      { "id": "slime_heavy", "base_sr2_slime": null, "projectile_speed": null, "on_hit_effect": null, "absorbable": true, "returnable_later": true, "verified": false },
      { "id": "slime_burst", "base_sr2_slime": null, "projectile_speed": null, "on_hit_effect": null, "absorbable": true, "returnable_later": true, "verified": false }
    ]
  },

  "sheet_systems": {
    "columns": ["id", "description", "depends_on", "in_first_playable", "verified"],
    "rows": [
      { "id": "shoot_slime",     "description": "Disparar el arma lanza un proyectil-slime del tipo del arma", "depends_on": ["sheet_weapons", "sheet_slime_ammo"], "in_first_playable": true,  "verified": false },
      { "id": "absorb_bullets",  "description": "Mantener el botón de absorber atrapa proyectiles enemigos y los convierte en munición/almacén", "depends_on": ["sheet_slime_ammo"], "in_first_playable": true,  "verified": false },
      { "id": "return_bullets",  "description": "Lanzar de vuelta los proyectiles absorbidos", "depends_on": ["absorb_bullets"], "in_first_playable": false, "verified": false },
      { "id": "slime_bomb",      "description": "Plantar y desactivar la bomba slime", "depends_on": ["teams"], "in_first_playable": false, "verified": false },
      { "id": "teams",           "description": "Atacantes vs defensores", "depends_on": ["multiplayer"], "in_first_playable": true,  "verified": false },
      { "id": "multiplayer",     "description": "Sesión compartida con unión por enlace de Melty", "depends_on": [], "in_first_playable": true, "verified": false }
    ]
  },

  "sheet_hooks_into_sr2": {
    "note": "Pendiente de leer game_info y el código del juego: cómo el mod lee cámara, teclas y jugadores en sesión.",
    "columns": ["id", "sr2_system", "how_found", "verified"],
    "rows": [
      { "id": "camera",          "sr2_system": null, "how_found": null, "verified": false },
      { "id": "key_bindings",    "sr2_system": null, "how_found": null, "verified": false },
      { "id": "vacpack_absorb",  "sr2_system": null, "how_found": null, "verified": false },
      { "id": "projectile_spawn","sr2_system": null, "how_found": null, "verified": false },
      { "id": "session_players", "sr2_system": null, "how_found": null, "verified": false }
    ]
  },

  "sheet_multiplayer": {
    "columns": ["field", "value", "verified"],
    "rows": [
      { "field": "maxPlayers", "value": null, "verified": false },
      { "field": "how_players_host_join", "value": null, "verified": false },
      { "field": "relay_or_lobby", "value": null, "verified": false },
      { "field": "connect.address (log + 'after' text)", "value": null, "verified": false },
      { "field": "connect.join (args/env/file/uri)", "value": null, "verified": false },
      { "field": "tested_with_two_instances", "value": false, "verified": false }
    ]
  },

  "sheet_listing_draft": {
    "title": "Slime Strike",
    "tagline": "Tiroteos por equipos con armas de CS2 que disparan slimes, y balas que puedes absorber.",
    "description": "Juega dentro de Slime Rancher 2 con armas de Counter-Strike 2 (modelos y sonidos leídos de tu propia copia). Cada arma dispara un tipo de slime distinto y puedes absorber las balas de tus rivales. Necesitas ambos juegos.",
    "credits": null,
    "content_license": null,
    "allow_remix": null,
    "screenshot": null,
    "status": "draft"
  },

  "preflight_open_items": [
    "Todas las celdas null de sheet_weapons y sheet_slime_ammo",
    "Todos los hooks de sheet_hooks_into_sr2",
    "Todo sheet_multiplayer (sin inventar maxPlayers)",
    "Créditos, licencia y remix (no se adivinan)",
    "Capturas reales del build funcionando",
    "game_info y search_mashups de Melty (no ejecutados)",
    "Comprobar que las armas de CS2 se pueden leer de la copia instalada sin riesgo de cuenta"
  ]
}
