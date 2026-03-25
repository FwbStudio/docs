---
layout:
  width: wide
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
---
# \[ESX] ALL Configs Files

{% code title="ESX Config" lineNumbers="true" fullWidth="true" %}

```lua
Config = {}

Config.Marker = {
    type = 2,
    color = { r = 50, g = 205, b = 50, a = 200 },
    size = { x = 0.2, y = 0.2, z = 0.1 },
    font = 0,
    fontSize = 0.4,
}


Config.ShopMarker = {
    type = 27,
    color = { r = 50, g = 205, b = 50, a = 200 },
    size = { x = 1.6, y = 1.6, z = 0.8 },
}


-- Plaaceable will only work if you ensure fs_placeables before this resource and drag fs_placeables script in your resources folder

-- Config.Placeables_enable = false  {placeable will not gonna work}
-- Config.Placeables_enable = true  {placeable will work if you follow documentation}

Config.Placeables_enable = true

Config.Placeables = {
    ['apple_gelato'] = {
        [1] = `fs_prop_cookies_apple_gelato`,
    },

    ['banana_backwoods'] = {
        [1] = `fs_prop_cookies_backwoods_banana`,
    },

    ['backwoods_grape'] = {
        [1] = `fs_prop_cookies_backwoods_grape`,
    },

    ['backwoods_honey'] = {
        [1] = `fs_prop_cookies_backwoods_honey`,
    },

    ['biscotti'] = {
        [1] = `fs_prop_cookies_biscotti_mints`,
    },

    ['backwoods_russian_cream'] = {
        [1] = `fs_prop_cookies_backwoods_russian_cream`,
    },

    ['blue_tomyz'] = {
        [1] = `fs_prop_cookies_blue_tomyz_mints`,
    },

    ['blueberry_jam_cookie'] = {
        [1] = `fs_prop_cookies_blueberry`,
    },

    ['blueberry_cruffin'] = {
        [1] = `fs_prop_cookies_blueberry_cruffin`,
    },

    ['butter_cookie'] = {
        [1] = `fs_prop_cookies_buttercookies`,
    },

    ['cake_mix'] = {
        [1] = `fs_prop_cookies_cake_mix`,
    },

    ['cereal_milk'] = {
        [1] = `fs_prop_cookies_cereal_milk`,
    },

    ['cheetah_piss'] = {
        [1] = `fs_prop_cookies_cheetah_piss`,
    },

    ['collins_ave'] = {
        [1] = `fs_prop_cookies_collins_ave`,
    },

    ['cookie_craze'] = {
        [1] = `fs_prop_cookies_cookiecraze`,
    },

    ['ether'] = {
        [1] = `fs_prop_cookies_ether_jar`,
    },

    ['get_figgy'] = {
        [1] = `fs_prop_cookies_figgycookies`,
    },

    ['fine_china'] = {
        [1] = `fs_prop_cookies_fine_china`,
    },

    ['gary_payton'] = {
        [1] = `fs_prop_cookies_gary_payton`,
    },

    ['gelatti'] = {
        [1] = `fs_prop_cookies_gelatti`,
    },

    ['georgia_pie'] = {
        [1] = `fs_prop_cookies_georgia_pie`,
    },

    ['gmo_cookies'] = {
        [1] = `fs_prop_cookies_gmo_cookies`,
    },

    ['grabba_leaf'] = {
        [1] = `fs_prop_cookies_grabba_leaf`,
    },

    ['ice_cream_cake'] = {
        [1] = `fs_prop_cookies_ice_cream_cake`,
    },


    ['key_lime_cookie'] = {
        [1] = `fs_prop_cookies_keylimes`,
    },

    ['khalifa_kush'] = {
        [1] = `fs_prop_cookies_khalifakhush`,
    },

    ['la_confidential'] = {
        [1] = `fs_prop_cookies_la_confidential`,
    },

    ['lighter'] = {
        [1] = `fs_prop_cookies_ligher`,
    },

    ['cheap_lighter'] = {
        [1] = `fs_prop_cookies_ligher_cheap`,
    },

    ['marathon'] = {
        [1] = `fs_prop_cookies_marathon_og`,
    },

    ['marshmallow_crisp'] = {
        [1] = `fs_prop_cookies_marshmallow_crisp`,
    },

    ['marshmallow_og'] = {
        [1] = `fs_prop_cookies_marshmallow_og`,
    },

    ['moon_rock'] = {
        [1] = `fs_prop_cookies_moon_rock`,
    },

    ['no_99'] = {
        [1] = `fs_prop_cookies_no_99`,
    },

    ['jefe'] = {
        [1] = `fs_prop_cookies_pack_jefe`,
    },

    ['oreoz'] = {
        [1] = `fs_prop_cookies_pack_oreoz`,
    },

    ['zushi'] = {
        [1] = `fs_prop_cookies_pack_zushi`,
    },

    ['paris_fog'] = {
        [1] = `fs_prop_cookies_paris_fog`,
    },

    ['pink_sandy'] = {
        [1] = `fs_prop_cookies_pink_sandy`,
    },

    ['pirckly_pear'] = {
        [1] = `fs_prop_cookies_pirckly_pear`,
    },

    ['pooch_bag'] = {
        [1] = `fs_prop_cookies_pooch_bag`,
    },

    ['pumpkin_cookie'] = {
        [1] = `fs_prop_cookies_pumpkin_cookie`,
    },

    ['runtz_og'] = {
        [1] = `fs_prop_cookies_runtz_og`,
    },

    ['shamrock_cookie'] = {
        [1] = `fs_prop_cookies_shamrock_cookie`,
    },

    ['snow_man'] = {
        [1] = `fs_prop_cookies_snow_man`,
    },

    ['sour_diesel'] = {
        [1] = `fs_prop_cookies_sour_diesel_og`,
    },

    ['weed_spray'] = {
        [1] = `fs_prop_cookies_spray`,
    },

    ['strawberry_jam_cookie'] = {
        [1] = `fs_prop_cookies_strawberry_jam_cookie`,
    },

    ['tahoe_og'] = {
        [1] = `fs_prop_cookies_tahoe_og`,
    },

    ['cinnamon_twists'] = {
        [1] = `fs_prop_cookies_twist`,
    },

    ['vape'] = {
        [1] = `fs_prop_cookies_vape_cheap`,
    },
    ['cheapvape'] = {
        [1] = `fs_prop_cookies_vape_cheap`,
    },
    ['premiumvape'] = {
        [1] = `fs_prop_cookies_vape_premium`,
    },

    ['weed_fertilizer'] = {
        [1] = `fs_prop_cookies_weed_fertilizer`,
    },

    ['weed_leaf'] = {
        [1] = `fs_prop_cookies_weed_leaf`,
    },

    ['seed_weed'] = {
        [1] = `fs_prop_cookies_weed_seeds`,
    },

    ['whitecherry_gelato'] = {
        [1] = `fs_prop_cookies_whitecherry_gelato`,
    },

    ['pogo'] = {
        [1] = `fs_prop_cookies_dropper_pogo`
    },

    ['gelatti_joint'] = {
        [1] = `prop_cigar_03`
    },
    ['gary_payton_joint'] = {
        [1] = `prop_cigar_03`
    },
    ['cereal_milk_joint'] = {
        [1] = `prop_cigar_03`
    },
    ['cheetah_piss_joint'] = {
        [1] = `prop_cigar_03`
    },
    ['snow_man_joint'] = {
        [1] = `prop_cigar_03`
    },
    ['georgia_pie_joint'] = {
        [1] = `prop_cigar_03`
    },
    ['jefe_joint'] = {
        [1] = `prop_cigar_03`
    },
    ['cake_mix_joint'] = {
        [1] = `prop_cigar_03`
    },
    ['white_runtz_joint'] = {
        [1] = `prop_cigar_03`
    },
    ['blueberry_cruffin_joint'] = {
        [1] = `prop_cigar_03`
    },
    ['whitecherry_gelato_joint'] = {
        [1] = `prop_cigar_03`
    },
    ['fine_china_joint'] = {
        [1] = `prop_cigar_03`
    },
    ['pink_sandy_joint'] = {
        [1] = `prop_cigar_03`
    },
    ['zushi_joint'] = {
        [1] = `prop_cigar_03`
    },
    ['apple_gelato_joint'] = {
        [1] = `prop_cigar_03`
    },
    ['biscotti_joint'] = {
        [1] = `prop_cigar_03`
    },
    ['collins_ave_joint'] = {
        [1] = `prop_cigar_03`
    },
    ['marathon_joint'] = {
        [1] = `prop_cigar_03`
    },
    ['oreoz_joint'] = {
        [1] = `prop_cigar_03`
    },
    ['pirckly_pear_joint'] = {
        [1] = `prop_cigar_03`
    },
    ['runtz_og_joint'] = {
        [1] = `prop_cigar_03`
    },
    ['blue_tomyz_joint'] = {
        [1] = `prop_cigar_03`
    },
    ['ether_joint'] = {
        [1] = `prop_cigar_03`
    },
    ['froties_joint'] = {
        [1] = `prop_cigar_03`
    },
    ['gmo_cookies_joint'] = {
        [1] = `prop_cigar_03`
    },
    ['ice_cream_cake_pack_joint'] = {
        [1] = `prop_cigar_03`
    },
    ['khalifa_kush_joint'] = {
        [1] = `prop_cigar_03`
    },
    ['la_confidential_joint'] = {
        [1] = `prop_cigar_03`
    },
    ['marshmallow_og_joint'] = {
        [1] = `prop_cigar_03`
    },
    ['moon_rock_joint'] = {
        [1] = `prop_cigar_03`
    },
    ['sour_diesel_joint'] = {
        [1] = `prop_cigar_03`
    },
    ['tahoe_og_joint'] = {
        [1] = `prop_cigar_03`
    },

}
```

{% endcode %}

{% code title="config-shop.lua" lineNumbers="true" fullWidth="true" %}

```lua
Config.format = {
    currency = 'USD',                               -- This is the format of the currency, so that your currency sign appears correctly
    location = 'en-US'                              -- This is the location of your country, to format the decimal places according to your standard
}

Config.Default = {
    stock = 300,
    price = 500
}

Config.Bill = {
	enable = true,
	keybind = 'F6'
}

Config.AdminGroups = {	-- You have to set your in-game group with /setgroup command
	admin = true,
	superadmin = true,
}

Config.Shop = {
    blip = {enable = true, pos = vector3(-307.5836, -1393.7045, 31.3958), name = 'Cookies', sprite = 89, color = 3, size = 1.0, radius = 0.0, radius_color = 4},                                                           -- job name
    boss_action = vector3(-312.6007, -1387.1134, 31.4795),
    management = vector3(-301.1704, -1390.5695, 31.4136),
    managementRankFor = {
		price = 2,
		stock = 2,
	},
    sell_coords = {                                         -- The coordinates where customes will buy things on this store (coordinates composed of x, y, z)
         vector3(-306.0830, -1401.2332, 31.3097),  
         vector3(-308.1081, -1405.8896, 31.3097),
         vector3(-309.8006, -1397.6663, 31.3097),
         vector3(-315.4385, -1400.4689, 31.3097),
         vector3(-315.3322, -1393.5300, 31.3097),
         vector3(-310.6846, -1391.6528, 30.4125),
        --vector3(-938.7438, -1176.9956, 4.9962),
    },
    data = {
        market_items = {                    -- Here you configure the items definitions
            backwoods_grape = {             -- The item ID
                name = "Backwoods Grape",   -- The item display name
                page = 0                    -- Set on which page this item will appear
            },
            backwoods_honey = {             -- The item ID
                name = "Backwoods Honey",   -- The item display name
                page = 0                    -- Set on which page this item will appear
            },
            backwoods_russian_cream = {             -- The item ID
                name = "Backwoods Russian Cream",   -- The item display name
                page = 0                    -- Set on which page this item will appear
            },
            grabba_leaf = {                 -- The item ID
                name = "Grabba Leaf",       -- The item display name
                page = 0                    -- Set on which page this item will appear
            },
            paxton_pearl_cigars = {                 -- The item ID
                name = "Paxton Pearl Cigars",       -- The item display name
                page = 0                    -- Set on which page this item will appear
            },
            banana_backwoods = {                 -- The item ID
                name = "Banana Backwoods",       -- The item display name
                page = 0                    -- Set on which page this item will appear
            },
            raw_cone_king = {                 -- The item ID
                name = "Raw Cone King",       -- The item display name
                page = 0                    -- Set on which page this item will appear
            },
            
            cake_mix = {                    -- The item ID
                name = "Cake Mix",          -- The item display name
                page = 1,                    -- Set on which page this item will appear
                process = {
                    required = {
                        ['weed_leaf'] = 10,
                        ['pooch_bag'] = 1,
                    },
                    processTime = 10000,
                    reward = 1,
                }
            },
            cereal_milk = {                 -- The item ID
                name = "Cereal Milk",       -- The item display name
                page = 1,                    -- Set on which page this item will appear
                process = {
                    required = {
                        ['weed_leaf'] = 10,
                        ['pooch_bag'] = 1,
                    },
                    processTime = 10000,
                    reward = 1,
                }
            },
            cheetah_piss = {                -- The item ID
                name = "Cheetah Piss",      -- The item display name
                page = 1,                    -- Set on which page this item will appear
                process = {
                    required = {
                        ['weed_leaf'] = 10,
                        ['pooch_bag'] = 1,
                    },
                    processTime = 10000,
                    reward = 1,
                }
            },
            gary_payton = {                 -- The item ID
                name = "Hary Payton",       -- The item display name
                page = 1,                    -- Set on which page this item will appear
                process = {
                    required = {
                        ['weed_leaf'] = 10,
                        ['pooch_bag'] = 1,
                    },
                    processTime = 10000,
                    reward = 1,
                }
            },
            gelatti = {                     -- The item ID
                name = "Gelatti",           -- The item display name
                page = 1,                    -- Set on which page this item will appear
                process = {
                    required = {
                        ['weed_leaf'] = 10,
                        ['pooch_bag'] = 1,
                    },
                    processTime = 10000,
                    reward = 1,
                }
            },
            georgia_pie = {                 -- The item ID
                name = "Georgia Pie",       -- The item display name
                page = 1,                    -- Set on which page this item will appear
                process = {
                    required = {
                        ['weed_leaf'] = 10,
                        ['pooch_bag'] = 1,
                    },
                    processTime = 10000,
                    reward = 1,
                }
            },
            jefe = {                        -- The item ID
                name = "Jefe",              -- The item display name
                page = 1,                    -- Set on which page this item will appear
                process = {
                    required = {
                        ['weed_leaf'] = 10,
                        ['pooch_bag'] = 1,
                    },
                    processTime = 10000,
                    reward = 1,
                }
            },
            white_runtz = {                 -- The item ID
                name = "White Runtz",       -- The item display name
                page = 1,                    -- Set on which page this item will appear
                process = {
                    required = {
                        ['weed_leaf'] = 10,
                        ['pooch_bag'] = 1,
                    },
                    processTime = 10000,
                    reward = 1,
                }
            },
            whitecherry_gelato = {          -- The item ID
                name = "Whitecherry Gelato",-- The item display name
                page = 1,                    -- Set on which page this item will appear
                process = {
                    required = {
                        ['weed_leaf'] = 10,
                        ['pooch_bag'] = 1,
                    },
                    processTime = 10000,
                    reward = 1,
                }
            },
            blueberry_cruffin = {           -- The item ID
                name = "Blueberry Cruffin", -- The item display name
                page = 1,                    -- Set on which page this item will appear
                process = {
                    required = {
                        ['weed_leaf'] = 10,
                        ['pooch_bag'] = 1,
                    },
                    processTime = 10000,
                    reward = 1,
                }
            },
            snow_man = {                    -- The item ID
                name = "Snow Man",          -- The item display name
                page = 1,                    -- Set on which page this item will appear
                process = {
                    required = {
                        ['weed_leaf'] = 10,
                        ['pooch_bag'] = 1,
                    },
                    processTime = 10000,
                    reward = 1,
                }
            },
            fine_china = {                    -- The item ID
                name = "Fine China",          -- The item display name
                page = 1,                    -- Set on which page this item will appear
                process = {
                    required = {
                        ['weed_leaf'] = 10,
                        ['pooch_bag'] = 1,
                    },
                    processTime = 10000,
                    reward = 1,
                }
            },
            pink_sandy = {                    -- The item ID
                name = "Oink Sandy",          -- The item display name
                page = 1,                    -- Set on which page this item will appear
                process = {
                    required = {
                        ['weed_leaf'] = 10,
                        ['pooch_bag'] = 1,
                    },
                    processTime = 10000,
                    reward = 1,
                }
            },
            zushi = {                    -- The item ID
                name = "Zushi",          -- The item display name
                page = 1,                    -- Set on which page this item will appear
                process = {
                    required = {
                        ['weed_leaf'] = 10,
                        ['pooch_bag'] = 1,
                    },
                    processTime = 10000,
                    reward = 1,
                }
            },
            apple_gelato = {                    -- The item ID
                name = "Apple Gelato",          -- The item display name
                page = 1,                    -- Set on which page this item will appear
                process = {
                    required = {
                        ['weed_leaf'] = 10,
                        ['pooch_bag'] = 1,
                    },
                    processTime = 10000,
                    reward = 1,
                }
            },
            biscotti = {                    -- The item ID
                name = "Biscotti",          -- The item display name
                page = 1,                    -- Set on which page this item will appear
                process = {
                    required = {
                        ['weed_leaf'] = 10,
                        ['pooch_bag'] = 1,
                    },
                    processTime = 10000,
                    reward = 1,
                }
            },
            collins_ave = {                    -- The item ID
                name = "Collins AVE",          -- The item display name
                page = 1,                    -- Set on which page this item will appear
                process = {
                    required = {
                        ['weed_leaf'] = 10,
                        ['pooch_bag'] = 1,
                    },
                    processTime = 10000,
                    reward = 1,
                }
            },
            marathon = {                    -- The item ID
                name = "Marathon",          -- The item display name
                page = 1,                    -- Set on which page this item will appear
                process = {
                    required = {
                        ['weed_leaf'] = 10,
                        ['pooch_bag'] = 1,
                    },
                    processTime = 10000,
                    reward = 1,
                }
            },
            oreoz = {                    -- The item ID
                name = "Oreoz",          -- The item display name
                page = 1,                    -- Set on which page this item will appear
                process = {
                    required = {
                        ['weed_leaf'] = 10,
                        ['pooch_bag'] = 1,
                    },
                    processTime = 10000,
                    reward = 1,
                }
            },
            pirckly_pear = {                    -- The item ID
                name = "Pirckly Pear",          -- The item display name
                page = 1,                    -- Set on which page this item will appear
                process = {
                    required = {
                        ['weed_leaf'] = 10,
                        ['pooch_bag'] = 1,
                    },
                    processTime = 10000,
                    reward = 1,
                }
            },
            runtz_og = {                    -- The item ID
                name = "Runtz OG",          -- The item display name
                page = 1,                    -- Set on which page this item will appear
                process = {
                    required = {
                        ['weed_leaf'] = 10,
                        ['pooch_bag'] = 1,
                    },
                    processTime = 10000,
                    reward = 1,
                }
            },
            blue_tomyz = {                    -- The item ID
                name = "Blue Tomyz",          -- The item display name
                page = 1,                    -- Set on which page this item will appear
                process = {
                    required = {
                        ['weed_leaf'] = 10,
                        ['pooch_bag'] = 1,
                    },
                    processTime = 10000,
                    reward = 1,
                }
            },
            ether = {                    -- The item ID
                name = "Ether",          -- The item display name
                page = 1,                    -- Set on which page this item will appear
                process = {
                    required = {
                        ['weed_leaf'] = 10,
                        ['pooch_bag'] = 1,
                    },
                    processTime = 10000,
                    reward = 1,
                }
            },
            froties = {                    -- The item ID
                name = "Froties",          -- The item display name
                page = 1,                    -- Set on which page this item will appear
                process = {
                    required = {
                        ['weed_leaf'] = 10,
                        ['pooch_bag'] = 1,
                    },
                    processTime = 10000,
                    reward = 1,
                }
            },
            gmo_cookies = {                    -- The item ID
                name = "GMO Cookies",          -- The item display name
                page = 1,                    -- Set on which page this item will appear
                process = {
                    required = {
                        ['weed_leaf'] = 10,
                        ['pooch_bag'] = 1,
                    },
                    processTime = 10000,
                    reward = 1,
                }
            },
            ice_cream_cake_pack = {                    -- The item ID
                name = "Ice Cream Cake Pack",          -- The item display name
                page = 1,                    -- Set on which page this item will appear
                process = {
                    required = {
                        ['weed_leaf'] = 10,
                        ['pooch_bag'] = 1,
                    },
                    processTime = 10000,
                    reward = 1,
                }
            },
            khalifa_kush = {                    -- The item ID
                name = "Khalifa Kush",          -- The item display name
                page = 1,                    -- Set on which page this item will appear
                process = {
                    required = {
                        ['weed_leaf'] = 10,
                        ['pooch_bag'] = 1,
                    },
                    processTime = 10000,
                    reward = 1,
                }
            },
            la_confidential = {                    -- The item ID
                name = "LA Confidential",          -- The item display name
                page = 1,                    -- Set on which page this item will appear
                process = {
                    required = {
                        ['weed_leaf'] = 10,
                        ['pooch_bag'] = 1,
                    },
                    processTime = 10000,
                    reward = 1,
                }
            },
            marshmallow_og = {                    -- The item ID
                name = "Marshmallow OG",          -- The item display name
                page = 1,                    -- Set on which page this item will appear
                process = {
                    required = {
                        ['weed_leaf'] = 10,
                        ['pooch_bag'] = 1,
                    },
                    processTime = 10000,
                    reward = 1,
                }
            },
            moon_rock = {                    -- The item ID
                name = "Moon Rock",          -- The item display name
                page = 1,                    -- Set on which page this item will appear
                process = {
                    required = {
                        ['weed_leaf'] = 10,
                        ['pooch_bag'] = 1,
                    },
                    processTime = 10000,
                    reward = 1,
                }
            },
            sour_diesel = {                    -- The item ID
                name = "Sour Diesel",          -- The item display name
                page = 1,                    -- Set on which page this item will appear
                process = {
                    required = {
                        ['weed_leaf'] = 10,
                        ['pooch_bag'] = 1,
                    },
                    processTime = 10000,
                    reward = 1,
                }
            },
            tahoe_og = {                    -- The item ID
                name = "Tahoe OG",          -- The item display name
                page = 1,                    -- Set on which page this item will appear
                process = {
                    required = {
                        ['weed_leaf'] = 10,
                        ['pooch_bag'] = 1,
                    },
                    processTime = 10000,
                    reward = 1,
                }
            },
            
            cake_mix_joint = {                    -- The item ID
                name = "Cake Mix Joint",          -- The item display name
                page = 2                    -- Set on which page this item will appear
            },
            cereal_milk_joint = {                 -- The item ID
                name = "Cereal Milk Joint",       -- The item display name
                page = 2                    -- Set on which page this item will appear
            },
            cheetah_piss_joint = {                -- The item ID
                name = "Cheetah Piss Joint",      -- The item display name
                page = 2                    -- Set on which page this item will appear
            },
            gary_payton_joint = {                 -- The item ID
                name = "Hary Payton Joint",       -- The item display name
                page = 2                    -- Set on which page this item will appear
            },
            gelatti_joint = {                     -- The item ID
                name = "Gelatti Joint",           -- The item display name
                page = 2                    -- Set on which page this item will appear
            },
            georgia_pie_joint = {                 -- The item ID
                name = "Georgia Pie Joint",       -- The item display name
                page = 2                    -- Set on which page this item will appear
            },
            jefe_joint = {                        -- The item ID
                name = "Jefe Joint",              -- The item display name
                page = 2                    -- Set on which page this item will appear
            },
            white_runtz_joint = {                 -- The item ID
                name = "White Runt Jointz",       -- The item display name
                page = 2                    -- Set on which page this item will appear
            },
            whitecherry_gelato_joint = {          -- The item ID
                name = "Whitecherry Gelato Joint",-- The item display name
                page = 2                    -- Set on which page this item will appear
            },
            blueberry_cruffin_joint = {           -- The item ID
                name = "Blueberry Cruffin Joint", -- The item display name
                page = 2                    -- Set on which page this item will appear
            },
            snow_man_joint = {                    -- The item ID
                name = "Snow Man Joint",          -- The item display name
                page = 2                    -- Set on which page this item will appear
            },
            fine_china_joint = {                    -- The item ID
                name = "Fine China Joint",          -- The item display name
                page = 2                    -- Set on which page this item will appear
            },
            pink_sandy_joint = {                    -- The item ID
                name = "Pink Sandy Joint",          -- The item display name
                page = 2                    -- Set on which page this item will appear
            },
            zushi_joint = {                    -- The item ID
                name = "Zushi Joint",          -- The item display name
                page = 2                    -- Set on which page this item will appear
            },
            apple_gelato_joint = {                    -- The item ID
                name = "Apple Gelato Joint",          -- The item display name
                page = 2                    -- Set on which page this item will appear
            },
            biscotti_joint = {                    -- The item ID
                name = "Biscotti Joint",          -- The item display name
                page = 2                    -- Set on which page this item will appear
            },
            collins_ave_joint = {                    -- The item ID
                name = "Collins AVE Joint",          -- The item display name
                page = 2                    -- Set on which page this item will appear
            },
            marathon_joint = {                    -- The item ID
                name = "Marathon Joint",          -- The item display name
                page = 2                    -- Set on which page this item will appear
            },
            oreoz_joint = {                    -- The item ID
                name = "Oreoz Joint",          -- The item display name
                page = 2                    -- Set on which page this item will appear
            },
            pirckly_pear_joint = {                    -- The item ID
                name = "Pirckly Pear Joint",          -- The item display name
                page = 2                    -- Set on which page this item will appear
            },
            runtz_og_joint = {                    -- The item ID
                name = "Runtz OG Joint",          -- The item display name
                page = 2                    -- Set on which page this item will appear
            },
            blue_tomyz_joint = {                    -- The item ID
                name = "Blue Tomyz Joint",          -- The item display name
                page = 2                    -- Set on which page this item will appear
            },
            ether_joint = {                    -- The item ID
                name = "Ether Joint",          -- The item display name
                page = 2                    -- Set on which page this item will appear
            },
            froties_joint = {                    -- The item ID
                name = "Froties Joint",          -- The item display name
                page = 2                    -- Set on which page this item will appear
            },
            gmo_cookies_joint = {                    -- The item ID
                name = "GMO Cookies Joint",          -- The item display name
                page = 2                    -- Set on which page this item will appear
            },
            ice_cream_cake_pack_joint = {                    -- The item ID
                name = "Ice Cream Cake Pack Joint",          -- The item display name
                page = 2                    -- Set on which page this item will appear
            },
            khalifa_kush_joint = {                    -- The item ID
                name = "Khalifa Kush Joint",          -- The item display name
                page = 2                    -- Set on which page this item will appear
            },
            la_confidential_joint = {                    -- The item ID
                name = "LA Confidential Joint",          -- The item display name
                page = 2                    -- Set on which page this item will appear
            },
            marshmallow_og_joint = {                    -- The item ID
                name = "Marshmallow OG Joint",          -- The item display name
                page = 2                    -- Set on which page this item will appear
            },
            moon_rock_joint = {                    -- The item ID
                name = "Moon Rock Joint",          -- The item display name
                page = 2                    -- Set on which page this item will appear
            },
            sour_diesel_joint = {                    -- The item ID
                name = "Sour Diesel Joint",          -- The item display name
                page = 2                    -- Set on which page this item will appear
            },
            tahoe_og_joint = {                    -- The item ID
                name = "Tahoe OG Joint",          -- The item display name
                page = 2                    -- Set on which page this item will appear
            },
            
            blueberry_jam_cookie = {                    -- The item ID
                name = "Blueberry Jam Cookie",          -- The item display name
                page = 3                    -- Set on which page this item will appear
            },
            butter_cookie = {                    -- The item ID
                name = "Butter Cookie",          -- The item display name
                page = 3                    -- Set on which page this item will appear
            },
            cookie_craze = {                    -- The item ID
                name = "Cookie Craze",          -- The item display name
                page = 3                    -- Set on which page this item will appear
            },
            get_figgy = {                    -- The item ID
                name = "Get Figgy",          -- The item display name
                page = 3                    -- Set on which page this item will appear
            },
            key_lime_cookie = {                    -- The item ID
                name = "Key Lime Cookie",          -- The item display name
                page = 3                    -- Set on which page this item will appear
            },
            marshmallow_crisp = {                    -- The item ID
                name = "Marshmallow Crisp",          -- The item display name
                page = 3                    -- Set on which page this item will appear
            },
            no_99 = {                    -- The item ID
                name = "NO 99",          -- The item display name
                page = 3                    -- Set on which page this item will appear
            },
            paris_fog = {                    -- The item ID
                name = "Paris Fog",          -- The item display name
                page = 3                    -- Set on which page this item will appear
            },
            pogo = {                    -- The item ID
                name = "Pogo",          -- The item display name
                page = 3                    -- Set on which page this item will appear
            },
            pumpkin_cookie = {                    -- The item ID
                name = "Pumpkin Cookie",          -- The item display name
                page = 3                    -- Set on which page this item will appear
            },
            shamrock_cookie = {                    -- The item ID
                name = "Shamrock Cookie",          -- The item display name
                page = 3                    -- Set on which page this item will appear
            },
            strawberry_jam_cookie = {                    -- The item ID
                name = "Strawberry Jam Cookie",          -- The item display name
                page = 3                    -- Set on which page this item will appear
            },
            
            lighter = {                     -- The item ID
                name = "Lighter",           -- The item display name
                page = 4                    -- Set on which page this item will appear
            },
            cheap_lighter = {               -- The item ID
                name = "Cheap Lighter",     -- The item display name
                page = 4                    -- Set on which page this item will appear
            },
            vape = {               -- The item ID
                name = "Vape",     -- The item display name
                page = 4                    -- Set on which page this item will appear
            },
            cheapvape = {               -- The item ID
                name = "Cheap Vape",     -- The item display name
                page = 4                    -- Set on which page this item will appear
            },
            premiumvape = {               -- The item ID
                name = "Premium Vape",     -- The item display name
                page = 4                    -- Set on which page this item will appear
            },
            
        },
        pagination = {                      -- Create pages to your market items (max 10 pages)
            [0] = {name = "Flavours", icon = 'fa-cookie-bite'},
            [1] = {name = "Backwoods", icon = 'fa-cookie-bite'},
            [2] = {name = "Joints", icon = 'fa-cookie-bite'},
            [3] = {name = "Vape", icon = 'fa-cookie-bite'},
            [4] = {name = "Utilities", icon = 'fa-cookie-bite'},
        },
    }
}
```

{% endcode %}

{% code title="config-farming.lua" lineNumbers="true" fullWidth="true" %}

```
Config.FarmLocation = vector3(-287.8372, -1391.5770, 25.5145) -- change this only if needed or u don't wanna use our mlo
Config.FarmRadius = 100.0   -- don't change it if u don't know what u doing

Config.FarmGetItem = {
    name = 'weed_leaf',             -- item that you will get after harvest
    max = 5,                        -- maximum per harvest * 5
    min = 1,                        -- minimum per harvest * 5
}

Config.FarmingFertilize = {         
    item = 'weed_fertilizer',       -- item required to fertilize the plant
    quantity = 1,                   -- quantity that required to fertilize
    damageChance = 10,              -- 10% chance will require fertilizer
}

Config.FarmingSpray = {
    item = 'weed_spray',            -- item required to spray the plant
    quantity = 1,                   -- quantity that required to fertilize
    damageChance = 10,              -- 10% chance will require spray
}

Config.FarmingRequired = {          --  required items to plant a new pot
    [1] = {
        item = 'weed_fertilizer',   -- item name
        quantity = 1,               -- item quantity
    },
    [2] = {
        item = 'weed_pot',          -- item name
        quantity = 1,               -- item quantity
    },
    [3] = {
        item = 'seed_weed',         -- item name
        quantity = 1,               -- item quantity
    },
}

Config.FarmingMultiItems = {
    [1] = {
        pos = vector3(-309.7330, -1385.4664, 31.5041),
        items = {
            ['lighter'] = {
                name = 'Lighter',                      -- item name
                price = 10,                                     -- price of the item. set it 0 if you don't want to buy with society money
                slots = 40,                                     -- container size
                available = 20,                                 -- available in stock
                regeneration = 60,                              -- in second
            },
            ['cheap_lighter'] = {
                name = 'Cheap Lighter',                      -- item name
                price = 10,                                     -- price of the item. set it 0 if you don't want to buy with society money
                slots = 40,                                     -- container size
                available = 20,                                 -- available in stock
                regeneration = 60,                              -- in second
            },
            ['grabba_leaf'] = {
                name = 'Grabba Leaf',                      -- item name
                price = 10,                                     -- price of the item. set it 0 if you don't want to buy with society money
                slots = 40,                                     -- container size
                available = 20,                                 -- available in stock
                regeneration = 60,                              -- in second
            },
            ['backwoods_honey'] = {
                name = 'Backwoods Honey',                      -- item name
                price = 10,                                     -- price of the item. set it 0 if you don't want to buy with society money
                slots = 40,                                     -- container size
                available = 20,                                 -- available in stock
                regeneration = 60,                              -- in second
            },
            ['backwoods_grape'] = {
                name = 'Backwoods Grape',                      -- item name
                price = 10,                                     -- price of the item. set it 0 if you don't want to buy with society money
                slots = 40,                                     -- container size
                available = 20,                                 -- available in stock
                regeneration = 60,                              -- in second
            },
            ['backwoods_russian_cream'] = {
                name = 'Backwoods Russian Cream',                      -- item name
                price = 10,                                     -- price of the item. set it 0 if you don't want to buy with society money
                slots = 40,                                     -- container size
                available = 20,                                 -- available in stock
                regeneration = 60,                              -- in second
            },
            ['paxton_pearl_cigars'] = {
                name = 'Paxton Pearl Cigars',                      -- item name
                price = 10,                                     -- price of the item. set it 0 if you don't want to buy with society money
                slots = 40,                                     -- container size
                available = 20,                                 -- available in stock
                regeneration = 60,                              -- in second
            },
            ['banana_backwoods'] = {
                name = 'Banana Backwoods',                      -- item name
                price = 10,                                     -- price of the item. set it 0 if you don't want to buy with society money
                slots = 40,                                     -- container size
                available = 20,                                 -- available in stock
                regeneration = 60,                              -- in second
            },
            ['raw_cone_king'] = {
                name = 'Raw Cone King',                      -- item name
                price = 10,                                     -- price of the item. set it 0 if you don't want to buy with society money
                slots = 40,                                     -- container size
                available = 20,                                 -- available in stock
                regeneration = 60,                              -- in second
            },
            ['blueberry_jam_cookie'] = {
                name = 'Blueberry Jam Cookie',                      -- item name
                price = 10,                                     -- price of the item. set it 0 if you don't want to buy with society money
                slots = 40,                                     -- container size
                available = 20,                                 -- available in stock
                regeneration = 60,                              -- in second
            },
            ['butter_cookie'] = {
                name = 'Butter Cookie',                      -- item name
                price = 10,                                     -- price of the item. set it 0 if you don't want to buy with society money
                slots = 40,                                     -- container size
                available = 20,                                 -- available in stock
                regeneration = 60,                              -- in second
            },
            ['cookie_craze'] = {
                name = 'Cookie Craze',                      -- item name
                price = 10,                                     -- price of the item. set it 0 if you don't want to buy with society money
                slots = 40,                                     -- container size
                available = 20,                                 -- available in stock
                regeneration = 60,                              -- in second
            },
            ['get_figgy'] = {
                name = 'Get Figgy',                      -- item name
                price = 10,                                     -- price of the item. set it 0 if you don't want to buy with society money
                slots = 40,                                     -- container size
                available = 20,                                 -- available in stock
                regeneration = 60,                              -- in second
            },
            ['key_lime_cookie'] = {
                name = 'Key Lime Cookie',                      -- item name
                price = 10,                                     -- price of the item. set it 0 if you don't want to buy with society money
                slots = 40,                                     -- container size
                available = 20,                                 -- available in stock
                regeneration = 60,                              -- in second
            },
            ['marshmallow_crisp'] = {
                name = 'Marshmallow Crisp',                      -- item name
                price = 10,                                     -- price of the item. set it 0 if you don't want to buy with society money
                slots = 40,                                     -- container size
                available = 20,                                 -- available in stock
                regeneration = 60,                              -- in second
            },
            ['no_99'] = {
                name = 'NO 99',                      -- item name
                price = 10,                                     -- price of the item. set it 0 if you don't want to buy with society money
                slots = 40,                                     -- container size
                available = 20,                                 -- available in stock
                regeneration = 60,                              -- in second
            },
            ['paris_fog'] = {
                name = 'Paris Fog',                      -- item name
                price = 10,                                     -- price of the item. set it 0 if you don't want to buy with society money
                slots = 40,                                     -- container size
                available = 20,                                 -- available in stock
                regeneration = 60,                              -- in second
            },
            ['pogo'] = {
                name = 'Pogo',                      -- item name
                price = 10,                                     -- price of the item. set it 0 if you don't want to buy with society money
                slots = 40,                                     -- container size
                available = 20,                                 -- available in stock
                regeneration = 60,                              -- in second
            },
            ['pumpkin_cookie'] = {
                name = 'Pumpkin Cookie',                      -- item name
                price = 10,                                     -- price of the item. set it 0 if you don't want to buy with society money
                slots = 40,                                     -- container size
                available = 20,                                 -- available in stock
                regeneration = 60,                              -- in second
            },
            ['shamrock_cookie'] = {
                name = 'Shamrock Cookie',                      -- item name
                price = 10,                                     -- price of the item. set it 0 if you don't want to buy with society money
                slots = 40,                                     -- container size
                available = 20,                                 -- available in stock
                regeneration = 60,                              -- in second
            },
            ['strawberry_jam_cookie'] = {
                name = 'Strawberry Jam Cookie',                      -- item name
                price = 10,                                     -- price of the item. set it 0 if you don't want to buy with society money
                slots = 40,                                     -- container size
                available = 20,                                 -- available in stock
                regeneration = 60,                              -- in second
            },
            ['vape'] = {
                name = 'Vape',                      -- item name
                price = 10,                                     -- price of the item. set it 0 if you don't want to buy with society money
                slots = 40,                                     -- container size
                available = 20,                                 -- available in stock
                regeneration = 60,                              -- in second
            },
            ['cheapvape'] = {
                name = 'Cheap Vape',                      -- item name
                price = 10,                                     -- price of the item. set it 0 if you don't want to buy with society money
                slots = 40,                                     -- container size
                available = 20,                                 -- available in stock
                regeneration = 60,                              -- in second
            },
            ['premiumvape'] = {
                name = 'Premium Vape',                      -- item name
                price = 10,                                     -- price of the item. set it 0 if you don't want to buy with society money
                slots = 40,                                     -- container size
                available = 20,                                 -- available in stock
                regeneration = 60,                              -- in second
            },
            
        }
    }
}

Config.FarmingItems = {
    [1] = {
        pos = vector3(-298.7548, -1387.8096, 26),  
        item = 'weed_fertilizer',                       -- item name
        price = 10,                                     -- price of the item. set it 0 if you don't want to buy with society money
        slots = 40,                                     -- container size
        available = 10,                                 -- available in stock
        regeneration = 60,                              -- in second
        msg = 'Press ~g~[E]~s~ to get ~b~Fertilizer~s~',
         
    },
    [2] = {
        pos = vector3(-305.2441, -1382.7513, 26), 
        item = 'weed_fertilizer',                       -- item name
        price = 10,                                     -- price of the item. set it 0 if you don't want to buy with society money
        slots = 40,                                     -- container size
        available = 0,                                  -- available in stock
        regeneration = 60,                              -- in second
        msg = 'Press ~g~[E]~s~ to get ~b~Fertilizer~s~',
        
    },
    [3] = {
        pos = vector3(-302.3104, -1383.1439, 25.6), 
        item = 'weed_pot',                              -- item name
        price = 10,                                     -- price of the item. set it 0 if you don't want to buy with society money
        slots = 40,                                     -- container size
        available = 10,                                 -- available in stock
        regeneration = 60,                              -- in second
        msg = 'Press ~g~[E]~s~ to get ~b~Weed Pot~s~',
        
    },
    [4] = {
        pos = vector3(-307.1557, -1386.4711, 25.7), 
        item = 'seed_weed',                             -- item name
        price = 10,                                     -- price of the item. set it 0 if you don't want to buy with society money
        slots = 40,                                     -- container size
        available = 10,                                 -- available in stock
        regeneration = 30,                              -- in second
        msg = 'Press ~g~[E]~s~ to get ~b~Weed Seed~s~',
         
    },
    [5] = {
        pos = vector3(-304.7994, -1386.8832, 26.15), 
        item = 'weed_spray',                            -- item name
        price = 10,                                     -- price of the item. set it 0 if you don't want to buy with society money
        slots = 40,                                     -- container size
        available = 10,                                 -- available in stock
        regeneration = 30,                              -- in second
        msg = 'Press ~g~[E]~s~ to get ~b~Weed Spray~s~',
        
    },
    [6] = {
        pos = vector3(-303.5630, -1386.9708, 26.15), 
        item = 'pooch_bag',                             -- item name
        price = 10,                                     -- price of the item. set it 0 if you don't want to buy with society money
        slots = 40,                                     -- container size
        available = 10,                                 -- available in stock
        regeneration = 30,                              -- in second
        msg = 'Press ~g~[E]~s~ to get ~b~Pooch Bag~s~',
        
    },
}

Config.ProcessLocation = {
    pos = vector3(-306.5929, -1384.4114, 25.8),
    heading = 90.8711,
}

Config.Objects = {
    [1] = "bkr_prop_weed_01_small_01c",
    [2] = "bkr_prop_weed_01_small_01b",
    [3] = "bkr_prop_weed_01_small_01a",
    [4] = "bkr_prop_weed_med_01a",
    [5] = "bkr_prop_weed_med_01b",
    [6] = "bkr_prop_weed_lrg_01a",
    [7] = "bkr_prop_weed_lrg_01b",
    --There is no stage 8. So don't add any prop here
}

Config.SageTimer = {
    [1] = 1, --got to next stage in minute
    [2] = 1, --got to next stage in minute
    [3] = 1, --got to next stage in minute
    [4] = 1, --got to next stage in minute
    [5] = 1, --got to next stage in minute
    [6] = 1, --got to next stage in minute
    [7] = 1, --got to next stage in minute
    --There is no stage 8. So don't add any stage here
}

Config.Plants = {
	vec3(-287.151581, -1397.049805, 24.572695),
    vec3(-285.955017, -1397.088501, 24.572695),
    vec3(-287.232666, -1398.461914, 24.572695),
    vec3(-287.050812, -1395.829590, 24.572695),
    vec3(-285.969330, -1398.474976, 24.572695),
    vec3(-285.942017, -1395.823120, 24.572695),
    vec3(-288.100555, -1395.806030, 24.572695),
    vec3(-290.084930, -1398.492065, 24.627434),
    vec3(-290.057007, -1395.785767, 24.627434),
    vec3(-291.665375, -1395.769043, 24.627434),
    vec3(-284.324951, -1392.581909, 24.655195),
    vec3(-282.964355, -1392.645142, 24.614044),
    vec3(-281.375336, -1392.821533, 24.614044),
    vec3(-284.297485, -1389.921021, 24.614044),
    vec3(-282.831177, -1390.035767, 24.614040),
    vec3(-281.312042, -1390.130493, 24.614040),
    vec3(-278.215057, -1391.772339, 24.673050),
    vec3(-278.144257, -1390.137817, 24.673050),
    vec3(-281.008728, -1386.713013, 24.632225),
    vec3(-279.966064, -1386.723755, 24.632225),
    vec3(-278.769196, -1386.736206, 24.632225),
    vec3(-277.652863, -1386.747681, 24.632225),
    vec3(-276.648895, -1386.758057, 24.632225),
    vec3(-280.979248, -1383.857178, 24.632225),
    vec3(-279.864868, -1383.868652, 24.632225),
    vec3(-278.730377, -1383.880371, 24.632225),
    vec3(-277.504700, -1383.893066, 24.632225),
    vec3(-276.413940, -1383.904297, 24.632225),
    vec3(-278.303711, -1393.625488, 24.614044),
    vec3(-275.524719, -1390.164917, 24.673050),
    vec3(-275.543915, -1392.023315, 24.673050),
    vec3(-275.562805, -1393.858643, 24.673050),
    vec3(-294.827393, -1395.630249, 24.627434),
    vec3(-293.875916, -1395.640015, 24.627434),
    vec3(-292.775757, -1395.757690, 24.627434),
    vec3(-290.946960, -1398.483276, 24.627434),
    vec3(-292.091644, -1398.362915, 24.627434),
    vec3(-293.043854, -1398.353149, 24.627434),
    vec3(-294.058014, -1398.342651, 24.627434),
    vec3(-291.700073, -1393.520996, 24.559731),
    vec3(-292.522034, -1393.512573, 24.559731),
    vec3(-293.354279, -1393.503906, 24.559731),
    vec3(-292.268524, -1391.043091, 24.559731),
    vec3(-294.212036, -1393.495117, 24.559731),
    vec3(-294.199341, -1392.263550, 24.559731),
    vec3(-293.236389, -1391.033081, 24.559731),
    vec3(-294.186615, -1391.023315, 24.559731),
    vec3(-288.027710, -1386.833984, 24.559587),
    vec3(-290.448425, -1386.972168, 24.559587),
    vec3(-288.016449, -1385.739502, 24.559587),
    vec3(-289.207336, -1385.898438, 24.559587),
    vec3(-290.497253, -1385.820190, 24.559587),
    vec3(-288.005463, -1384.679321, 24.559587),
    vec3(-289.212799, -1384.666870, 24.559587),
    vec3(-290.471069, -1384.653809, 24.559587),
    vec3(-285.999969, -1387.003784, 24.559587),
    vec3(-284.606232, -1387.018066, 24.559587),
    vec3(-283.526947, -1386.918701, 24.559587),
    vec3(-284.593048, -1385.747559, 24.559587),
    vec3(-283.516205, -1385.880981, 24.559587),
    vec3(-286.106598, -1384.533203, 24.559587),
    vec3(-284.751129, -1384.547363, 24.559587),
    vec3(-283.502625, -1384.560181, 24.559587),
    vec3(-283.902374, -1397.430786, 24.572702),
    vec3(-283.856140, -1395.949707, 24.572702),
    vec3(-283.882294, -1398.711426, 24.572714),
    vec3(-282.621124, -1397.711304, 24.572702),
    vec3(-282.603088, -1395.962524, 24.572702),
}
```

{% endcode %}
