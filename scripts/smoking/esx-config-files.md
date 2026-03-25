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
# \[ESX] Config Files

{% code title="ESX Config" lineNumbers="true" fullWidth="true" %}

```lua
Config = {}

local seconds = 1000 -- don't touch it

Config.ImagePath = "ox_inventory/web/images/"

Config.Vape = {
    Smoke_Size = {mouth = 2.5},
    Item = {
        vape = { max_size = 5, remove_size = 1, mouth_smoke = 2.0, model = "ba_prop_battle_vape_01", bone = 18905, pos = vec3(0.14, -0.02, 0.05), rot = vec3(164, -80, 10) },
        cheapvape = { max_size = 5, remove_size = 1, mouth_smoke = 2.0, model = "fs_prop_cookies_vape_cheap", bone = 18905, pos = vec3(0.14, -0.03, 0.05), rot = vec3(-100, -30, 0) },
        premiumvape = { max_size = 10, remove_size = 2, mouth_smoke = 2.0, model = "fs_prop_cookies_vape_premium", bone = 18905, pos = vec3(0.14, -0.02, 0.05), rot = vec3(-100, 10, -20) }
    },
    Flavours = {
        blueberry_jam_cookie = { label = "Blueberry Jam Cookie", liquid_size = 6 },
        butter_cookie = { label = "Butter Cookie", liquid_size = 6 },
        cookie_craze = { label = "Cookie Craze", liquid_size = 6 },
        get_figgy = { label = "Get Figgy", liquid_size = 6 },
        key_lime_cookie = { label = "Key Lime Cookie", liquid_size = 6 },
        marshmallow_crisp = { label = "Marshmallow Crisp", liquid_size = 6 },
        no_99 = { label = "NO 99", liquid_size = 6 },
        paris_fog = { label = "Paris Fog", liquid_size = 6 },
        pogo = { label = "Pogo", liquid_size = 6 },
        pumpkin_cookie = { label = "Pumpkin Cookie", liquid_size = 6 },
        shamrock_cookie = { label = "Shamrock Cookie", liquid_size = 6 },
        strawberry_jam_cookie = { label = "Strawberry Jam Cookie", liquid_size = 6 }
    }
}


Config.Joint = {
    Smoke_Size = {prop = 0.7, mouth = 2.0},
    ExaleTime = {min = 1, max = 3},
    AutoRemove = { time = 120 * seconds, inhale = 13 },
    CraftingDelay = 15 * seconds,
    lighter = {
        needed = true,
        items = { 
            { label = 'Lighter'      , name = 'lighter'      , count = 1},
            { label = 'Cheap Lighter', name = 'cheap_lighter', count = 1},
        }
    },
    UseableJoints = {
        "cake_mix_joint",
        "cereal_milk_joint",
        "cheetah_piss_joint",
        "gary_payton_joint",
        "gelatti_joint",
        "georgia_pie_joint",
        "jefe_joint",
        "white_runtz_joint",
        "snow_man_joint",
        "whitecherry_gelato_joint",
        "blueberry_cruffin_joint",
        "fine_china_joint",
        "pink_sandy_joint",
        "zushi_joint",
        "apple_gelato_joint",
        "biscotti_joint",
        "collins_ave_joint",
        "marathon_joint",
        "oreoz_joint",
        "pirckly_pear_joint",
        "runtz_og_joint",
        "blue_tomyz_joint",
        "ether_joint",
        "froties_joint",
        "gmo_cookies_joint",
        "ice_cream_cake_pack_joint",
        "khalifa_kush_joint",
        "la_confidential_joint",
        "marshmallow_og_joint",
        "moon_rock_joint",
        "sour_diesel_joint",
        "tahoe_og_joint",
    },
    Joints_Crafting = {
        ['cake_mix'] = {
            required_one_of_this = {
                ['backwoods_grape'] = 1,
                ['backwoods_honey'] = 1,
                ['backwoods_russian_cream'] = 1,
                ['grabba_leaf'] = 1,
                ['paxton_pearl_cigars'] = 1,
                ['banana_backwoods'] = 1,
                ['raw_cone_king'] = 1
            },
            rewards = {['cake_mix_joint'] = 5}
        },
        ['cereal_milk'] = {
            required_one_of_this = {
                ['backwoods_grape'] = 1,
                ['backwoods_honey'] = 1,
                ['backwoods_russian_cream'] = 1,
                ['grabba_leaf'] = 1,
                ['paxton_pearl_cigars'] = 1,
                ['banana_backwoods'] = 1,
                ['raw_cone_king'] = 1
            },
            rewards = {['cereal_milk_joint'] = 5}
        },
        ['cheetah_piss'] = {
            required_one_of_this = {
                ['backwoods_grape'] = 1,
                ['backwoods_honey'] = 1,
                ['backwoods_russian_cream'] = 1,
                ['grabba_leaf'] = 1,
                ['paxton_pearl_cigars'] = 1,
                ['banana_backwoods'] = 1,
                ['raw_cone_king'] = 1
            },
            rewards = {['cheetah_piss_joint'] = 5}
        },
        ['gary_payton'] = {
            required_one_of_this = {
                ['backwoods_grape'] = 1,
                ['backwoods_honey'] = 1,
                ['backwoods_russian_cream'] = 1,
                ['grabba_leaf'] = 1,
                ['paxton_pearl_cigars'] = 1,
                ['banana_backwoods'] = 1,
                ['raw_cone_king'] = 1
            },
            rewards = {['gary_payton_joint'] = 5}
        },
        ['gelatti'] = {
            required_one_of_this = {
                ['backwoods_grape'] = 1,
                ['backwoods_honey'] = 1,
                ['backwoods_russian_cream'] = 1,
                ['grabba_leaf'] = 1,
                ['paxton_pearl_cigars'] = 1,
                ['banana_backwoods'] = 1,
                ['raw_cone_king'] = 1
            },
            rewards = {['gelatti_joint'] = 5}
        },
        ['georgia_pie'] = {
            required_one_of_this = {
                ['backwoods_grape'] = 1,
                ['backwoods_honey'] = 1,
                ['backwoods_russian_cream'] = 1,
                ['grabba_leaf'] = 1,
                ['paxton_pearl_cigars'] = 1,
                ['banana_backwoods'] = 1,
                ['raw_cone_king'] = 1
            },
            rewards = {['georgia_pie_joint'] = 5}
        },
        ['jefe'] = {
            required_one_of_this = {
                ['backwoods_grape'] = 1,
                ['backwoods_honey'] = 1,
                ['backwoods_russian_cream'] = 1,
                ['grabba_leaf'] = 1,
                ['paxton_pearl_cigars'] = 1,
                ['banana_backwoods'] = 1,
                ['raw_cone_king'] = 1
            },
            rewards = {['jefe_joint'] = 5}
        },
        ['white_runtz'] = {
            required_one_of_this = {
                ['backwoods_grape'] = 1,
                ['backwoods_honey'] = 1,
                ['backwoods_russian_cream'] = 1,
                ['grabba_leaf'] = 1,
                ['paxton_pearl_cigars'] = 1,
                ['banana_backwoods'] = 1,
                ['raw_cone_king'] = 1
            },
            rewards = {['white_runtz_joint'] = 5}
        },
        ['snow_man'] = {
            required_one_of_this = {
                ['backwoods_grape'] = 1,
                ['backwoods_honey'] = 1,
                ['backwoods_russian_cream'] = 1,
                ['grabba_leaf'] = 1,
                ['paxton_pearl_cigars'] = 1,
                ['banana_backwoods'] = 1,
                ['raw_cone_king'] = 1
            },

            rewards = {['snow_man_joint'] = 5}
        },
        ['whitecherry_gelato'] = {
            required_one_of_this = {
                ['backwoods_grape'] = 1,
                ['backwoods_honey'] = 1,
                ['backwoods_russian_cream'] = 1,
                ['grabba_leaf'] = 1,
                ['paxton_pearl_cigars'] = 1,
                ['banana_backwoods'] = 1,
                ['raw_cone_king'] = 1
            },

            rewards = {['whitecherry_gelato_joint'] = 5}
        },
        ['blueberry_cruffin'] = {
            required_one_of_this = {
                ['backwoods_grape'] = 1,
                ['backwoods_honey'] = 1,
                ['backwoods_russian_cream'] = 1,
                ['grabba_leaf'] = 1,
                ['paxton_pearl_cigars'] = 1,
                ['banana_backwoods'] = 1,
                ['raw_cone_king'] = 1
            },

            rewards = {['blueberry_cruffin_joint'] = 5}
        },
        ['fine_china'] = {
            required_one_of_this = {
                ['backwoods_grape'] = 1,
                ['backwoods_honey'] = 1,
                ['backwoods_russian_cream'] = 1,
                ['grabba_leaf'] = 1,
                ['paxton_pearl_cigars'] = 1,
                ['banana_backwoods'] = 1,
                ['raw_cone_king'] = 1
            },

            rewards = {['fine_china_joint'] = 5}
        },
        ['pink_sandy'] = {
            required_one_of_this = {
                ['backwoods_grape'] = 1,
                ['backwoods_honey'] = 1,
                ['backwoods_russian_cream'] = 1,
                ['grabba_leaf'] = 1,
                ['paxton_pearl_cigars'] = 1,
                ['banana_backwoods'] = 1,
                ['raw_cone_king'] = 1
            },

            rewards = {['pink_sandy_joint'] = 5}
        },
        ['zushi'] = {
            required_one_of_this = {
                ['backwoods_grape'] = 1,
                ['backwoods_honey'] = 1,
                ['backwoods_russian_cream'] = 1,
                ['grabba_leaf'] = 1,
                ['paxton_pearl_cigars'] = 1,
                ['banana_backwoods'] = 1,
                ['raw_cone_king'] = 1
            },

            rewards = {['zushi_joint'] = 5}
        },
        ['apple_gelato'] = {
            required_one_of_this = {
                ['backwoods_grape'] = 1,
                ['backwoods_honey'] = 1,
                ['backwoods_russian_cream'] = 1,
                ['grabba_leaf'] = 1,
                ['paxton_pearl_cigars'] = 1,
                ['banana_backwoods'] = 1,
                ['raw_cone_king'] = 1
            },

            rewards = {['apple_gelato_joint'] = 5}
        },
        ['biscotti'] = {
            required_one_of_this = {
                ['backwoods_grape'] = 1,
                ['backwoods_honey'] = 1,
                ['backwoods_russian_cream'] = 1,
                ['grabba_leaf'] = 1,
                ['paxton_pearl_cigars'] = 1,
                ['banana_backwoods'] = 1,
                ['raw_cone_king'] = 1
            },

            rewards = {['biscotti_joint'] = 5}
        },
        ['collins_ave'] = {
            required_one_of_this = {
                ['backwoods_grape'] = 1,
                ['backwoods_honey'] = 1,
                ['backwoods_russian_cream'] = 1,
                ['grabba_leaf'] = 1,
                ['paxton_pearl_cigars'] = 1,
                ['banana_backwoods'] = 1,
                ['raw_cone_king'] = 1
            },

            rewards = {['collins_ave_joint'] = 5}
        },
        ['marathon'] = {
            required_one_of_this = {
                ['backwoods_grape'] = 1,
                ['backwoods_honey'] = 1,
                ['backwoods_russian_cream'] = 1,
                ['grabba_leaf'] = 1,
                ['paxton_pearl_cigars'] = 1,
                ['banana_backwoods'] = 1,
                ['raw_cone_king'] = 1
            },

            rewards = {['marathon_joint'] = 5}
        },
        ['oreoz'] = {
            required_one_of_this = {
                ['backwoods_grape'] = 1,
                ['backwoods_honey'] = 1,
                ['backwoods_russian_cream'] = 1,
                ['grabba_leaf'] = 1,
                ['paxton_pearl_cigars'] = 1,
                ['banana_backwoods'] = 1,
                ['raw_cone_king'] = 1
            },

            rewards = {['oreoz_joint'] = 5}
        },
        ['pirckly_pear'] = {
            required_one_of_this = {
                ['backwoods_grape'] = 1,
                ['backwoods_honey'] = 1,
                ['backwoods_russian_cream'] = 1,
                ['grabba_leaf'] = 1,
                ['paxton_pearl_cigars'] = 1,
                ['banana_backwoods'] = 1,
                ['raw_cone_king'] = 1
            },

            rewards = {['pirckly_pear_joint'] = 5}
        },
        ['runtz_og'] = {
            required_one_of_this = {
                ['backwoods_grape'] = 1,
                ['backwoods_honey'] = 1,
                ['backwoods_russian_cream'] = 1,
                ['grabba_leaf'] = 1,
                ['paxton_pearl_cigars'] = 1,
                ['banana_backwoods'] = 1,
                ['raw_cone_king'] = 1
            },

            rewards = {['runtz_og_joint'] = 5}
        },
        ['blue_tomyz'] = {
            required_one_of_this = {
                ['backwoods_grape'] = 1,
                ['backwoods_honey'] = 1,
                ['backwoods_russian_cream'] = 1,
                ['grabba_leaf'] = 1,
                ['paxton_pearl_cigars'] = 1,
                ['banana_backwoods'] = 1,
                ['raw_cone_king'] = 1
            },

            rewards = {['blue_tomyz_joint'] = 5}
        },
        ['ether'] = {
            required_one_of_this = {
                ['backwoods_grape'] = 1,
                ['backwoods_honey'] = 1,
                ['backwoods_russian_cream'] = 1,
                ['grabba_leaf'] = 1,
                ['paxton_pearl_cigars'] = 1,
                ['banana_backwoods'] = 1,
                ['raw_cone_king'] = 1
            },

            rewards = {['ether_joint'] = 5}
        },
        ['froties'] = {
            required_one_of_this = {
                ['backwoods_grape'] = 1,
                ['backwoods_honey'] = 1,
                ['backwoods_russian_cream'] = 1,
                ['grabba_leaf'] = 1,
                ['paxton_pearl_cigars'] = 1,
                ['banana_backwoods'] = 1,
                ['raw_cone_king'] = 1
            },

            rewards = {['froties_joint'] = 5}
        },
        ['gmo_cookies'] = {
            required_one_of_this = {
                ['backwoods_grape'] = 1,
                ['backwoods_honey'] = 1,
                ['backwoods_russian_cream'] = 1,
                ['grabba_leaf'] = 1,
                ['paxton_pearl_cigars'] = 1,
                ['banana_backwoods'] = 1,
                ['raw_cone_king'] = 1
            },

            rewards = {['gmo_cookies_joint'] = 5}
        },
        ['ice_cream_cake_pack'] = {
            required_one_of_this = {
                ['backwoods_grape'] = 1,
                ['backwoods_honey'] = 1,
                ['backwoods_russian_cream'] = 1,
                ['grabba_leaf'] = 1,
                ['paxton_pearl_cigars'] = 1,
                ['banana_backwoods'] = 1,
                ['raw_cone_king'] = 1
            },

            rewards = {['ice_cream_cake_pack_joint'] = 5}
        },
        ['khalifa_kush'] = {
            required_one_of_this = {
                ['backwoods_grape'] = 1,
                ['backwoods_honey'] = 1,
                ['backwoods_russian_cream'] = 1,
                ['grabba_leaf'] = 1,
                ['paxton_pearl_cigars'] = 1,
                ['banana_backwoods'] = 1,
                ['raw_cone_king'] = 1
            },

            rewards = {['khalifa_kush_joint'] = 5}
        },
        ['la_confidential'] = {
            required_one_of_this = {
                ['backwoods_grape'] = 1,
                ['backwoods_honey'] = 1,
                ['backwoods_russian_cream'] = 1,
                ['grabba_leaf'] = 1,
                ['paxton_pearl_cigars'] = 1,
                ['banana_backwoods'] = 1,
                ['raw_cone_king'] = 1
            },

            rewards = {['la_confidential_joint'] = 5}
        },
        ['marshmallow_og'] = {
            required_one_of_this = {
                ['backwoods_grape'] = 1,
                ['backwoods_honey'] = 1,
                ['backwoods_russian_cream'] = 1,
                ['grabba_leaf'] = 1,
                ['paxton_pearl_cigars'] = 1,
                ['banana_backwoods'] = 1,
                ['raw_cone_king'] = 1
            },

            rewards = {['marshmallow_og_joint'] = 5}
        },
        ['moon_rock'] = {
            required_one_of_this = {
                ['backwoods_grape'] = 1,
                ['backwoods_honey'] = 1,
                ['backwoods_russian_cream'] = 1,
                ['grabba_leaf'] = 1,
                ['paxton_pearl_cigars'] = 1,
                ['banana_backwoods'] = 1,
                ['raw_cone_king'] = 1
            },

            rewards = {['moon_rock_joint'] = 5}
        },
        ['sour_diesel'] = {
            required_one_of_this = {
                ['backwoods_grape'] = 1,
                ['backwoods_honey'] = 1,
                ['backwoods_russian_cream'] = 1,
                ['grabba_leaf'] = 1,
                ['paxton_pearl_cigars'] = 1,
                ['banana_backwoods'] = 1,
                ['raw_cone_king'] = 1
            },

            rewards = {['sour_diesel_joint'] = 5}
        },
        ['tahoe_og'] = {
            required_one_of_this = {
                ['backwoods_grape'] = 1,
                ['backwoods_honey'] = 1,
                ['backwoods_russian_cream'] = 1,
                ['grabba_leaf'] = 1,
                ['paxton_pearl_cigars'] = 1,
                ['banana_backwoods'] = 1,
                ['raw_cone_king'] = 1
            },

            rewards = {['tahoe_og_joint'] = 5}
        }
     
    }
}


 
```

{% endcode %}
