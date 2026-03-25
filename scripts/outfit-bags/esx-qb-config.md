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
# \[ESX/QB] Config

### Config.lua

{% code fullWidth="true" %}

```lua
--[[

    FwB Studio Outfit Bag Config File

]]

-- unique_bags = true then if player saved outfit in small bag will not gonna get old stored outfits in new small bag
-- unique_bags = false then if player saved outfit in small bag will get old stored outfits in new small bag
config.unique_bags = false -- {if using command or non_item then this setting will be ignored}

-- {clothing item compatiblity will be avilable in next update}
config.clotingitem = false --  make it true if your using fs_clothingitem script to avoid saving outifts that are items in clothingitem script

config.onlyonebag = true   -- if true player can only place 1 bag on ground at a time {not effected on unique bags enabled}

--[[

    NAKED CHARACTER CONFIG

]]

config.character = {
    models = {
        [`mp_m_freemode_01`] = 'M', -- change only if you know what you are doing
        [`mp_f_freemode_01`] = 'F'  -- change only if you know what you are doing
    },
    naked = {
        ----------------------------<Naked Male>----------------------------
        [`mp_m_freemode_01`] = {

            mask_1 = { drawable = 0, texture = 0, palette = 0 },       -- mask
            helmet_1 = { drawable = -1, texture = 0, palette = 0 },    -- helmet
            glasses_1 = { drawable = -1, texture = 0, palette = 0 },   -- gl
            ears_1 = { drawable = -1, texture = 0, palette = 0 },      -- ears_1
            tshirt_1 = { drawable = 15, texture = 0, palette = 0 },    -- t shirt
            torso_1 = { drawable = 15, texture = 0, palette = 0 },     -- torso
            decals_1 = { drawable = 0, texture = 0, palette = 0 },     -- decals
            bproof_1 = { drawable = 0, texture = 0, palette = 0 },     -- bulletproof vest
            arms = { drawable = 15, texture = 0, palette = 0 },        -- arms
            watches_1 = { drawable = -1, texture = 0, palette = 0 },   -- watches
            bracelets_1 = { drawable = -1, texture = 0, palette = 0 }, -- bracelets
            bags_1 = { drawable = 0, texture = 0, palette = 0 },       -- bag
            pants_1 = { drawable = 61, texture = 0, palette = 0 },     -- pants
            shoes_1 = { drawable = 34, texture = 0, palette = 0 },     -- shoes
        },
        ----------------------------<Naked Female>----------------------------
        [`mp_f_freemode_01`] = {

            mask_1 = { drawable = 0, texture = 0, palette = 0 },       -- mask
            helmet_1 = { drawable = -1, texture = 0, palette = 0 },    -- helmet
            glasses_1 = { drawable = -1, texture = 0, palette = 0 },   -- gl
            ears_1 = { drawable = -1, texture = 0, palette = 0 },      -- ears_1
            tshirt_1 = { drawable = 15, texture = 0, palette = 0 },    -- t shirt
            torso_1 = { drawable = 15, texture = 0, palette = 0 },     -- torso
            decals_1 = { drawable = 0, texture = 0, palette = 0 },     -- decals
            bproof_1 = { drawable = 0, texture = 0, palette = 0 },     -- bulletproof vest
            arms = { drawable = 15, texture = 0, palette = 0 },        -- arms
            watches_1 = { drawable = -1, texture = 0, palette = 0 },   -- watches
            bracelets_1 = { drawable = -1, texture = 0, palette = 0 }, -- bracelets
            bags_1 = { drawable = 0, texture = 0, palette = 0 },       -- bag
            pants_1 = { drawable = 61, texture = 0, palette = 0 },     -- pants
            shoes_1 = { drawable = 34, texture = 0, palette = 0 },     -- shoes
        }
        ----------------------------<Naked Config Ended>----------------------------
    }
}

--[[

    PUBLIC BAGS CONFIG {COMMANDS}

]]

config.non_item = { -- if u wanna use bag as command
    enable = true,  -- enable or disable commands
    commands = {
        [1] = {
            command = 'outfitbag', -- command to open outfit bag
            bag = 'fs_small_bag'   -- copy bag name from config.public_bags
        },
        [2] = {
            command = 'ob',      -- command to open outfit bag
            bag = 'fs_small_bag' -- copy bag name from config.public_bags
        },
        -- you can add more command here
        --[[
        [3] = {
            command = 'largebag',
            bag = 'fs_large_bag'
        },
        ]]



    }
}

--[[

    PUBLIC BAGS CONFIG {ITEMS/BAGS Types}

]]
--{don't touch if you don't know what your are doing}
config.bag_timeout = 10 -- in minutes if bag is public and not picked up after placing it will get deleted after this time


config.public_bags = {
    enable = false, -- if enable then item useable will work else u can use these bags into command also without enable item
    items = {
        ['fs_small_bag'] = {
            label = 'Small Outfit Bag',
            slots = 2,                             -- outfit slots
            model = 'reh_prop_reh_bag_outfit_01a', -- optional custom model
        },

        ['fs_medium_bag'] = {
            label = 'Medium Outfit Bag',
            slots = 20,                    -- outfit slots
            model = 'prop_ld_suitcase_01', -- optional custom model
        },
        ['fs_large_bag'] = {
            label = 'Large Outfit Bag',
            slots = 30,                    -- outfit slots
            model = 'prop_ld_suitcase_01', -- optional custom model
        },

        -- you can add your custom bag under here
    }
}


--[[

    WHITELIST BAGS CONFIG / JOB BAGS CONFIG

]]

config.command = { -- get outfit code for config file
    -- enable it only when are making bags for jobs this will help you to copy outfit code
    enable = false,
    -- command to get outift code on your mouse curose and paste it anywhere you want can be used to get outfit code for ur currently weared clothes
    -- once you get code you can paste into bottom outfits part
    command = 'getoutfit',
}


config.whitelist_bags = {
    enable = true,
    Bags = {


        ----------------------------<Police Outfit Bag Start>----------------------------


        ['police_bag'] = {                                        -- bag name
            label = 'Police Outfit Bag',
            model = 'reh_prop_reh_bag_outfit_01a',                -- make sure don't copy public bags models
            points = {                                            -- points where you want bags to be placed for jobs locations
                --
                vector4(253.1481, -1486.2019, 29.3761, 256.5067), -- example point for police station
            },
            whitelist = {                                         -- who can open bag
                enable = false,                                   -- no whitelist mean anyone can open bag
                permissions = {
                    admingroups = {
                        --        ['admin'] = true
                    },
                    jobgroups = {
                        --      ['police'] = 0
                    },
                    aces = {
                        --         ['whitewidow'] = true,
                    },
                    identifiers = {
                        --         ['license:1c17a180cdad995771fea75248f0ed95569b9e6a'] = true,
                        --
                    },
                    characters = {
                        --         ['char1:1c17a180cdad995771fea75248f0ed95569b9e6a'] = true,

                    }
                },
            },
            outfits = {
                [1] = {
                    title = 'Duty Outfit',
                    playermodel = `mp_m_freemode_01`, -- male = `mp_m_freemode_01`, female = `mp_f_freemode_01`
                    whitelist = {                     -- only these job or grade will able to see this
                        ['police'] = { 0, 1, 2, 3 },  -- who ever will see this outfit in bag
                    },
                    outfit = {
                        mask_1 = { drawable = 0, texture = 0, palette = 0 },     -- mask
                        helmet_1 = { drawable = -1, texture = 0, palette = 0 },  -- helmet
                        glasses_1 = { drawable = -1, texture = 0, palette = 0 }, -- gl
                        ears_1 = { drawable = -1, texture = 0, palette = 0 },    -- ears_1

                        -- shirt
                        tshirt_1 = { drawable = 15, texture = 0, palette = 0 },    -- t shirt
                        torso_1 = { drawable = 15, texture = 0, palette = 0 },     -- torso
                        decals_1 = { drawable = 0, texture = 0, palette = 0 },     -- decals
                        bproof_1 = { drawable = 0, texture = 0, palette = 0 },     -- bulletproof vest
                        arms = { drawable = 15, texture = 0, palette = 0 },        -- arms
                        watches_1 = { drawable = -1, texture = 0, palette = 0 },   -- watches
                        bracelets_1 = { drawable = -1, texture = 0, palette = 0 }, -- bracelets
                        bags_1 = { drawable = 0, texture = 0, palette = 0 },       -- bag

                        -- pants
                        pants_1 = { drawable = 61, texture = 0, palette = 0 }, -- pants
                        -- shoes
                        shoes_1 = { drawable = 34, texture = 0, palette = 0 }, -- shoes
                    }
                },
                [2] = {
                    title = 'Undercover Outfit',
                    playermodel = `mp_m_freemode_01`, -- male = `mp_m_freemode_01`, female = `mp_f_freemode_01`
                    whitelist = {
                        ['police'] = { 0, 1, 2, 3 },  -- who ever will see this outfit in bag
                    },
                    outfit = {
                        mask_1 = { drawable = 0, texture = 0, palette = 0 },     -- mask
                        helmet_1 = { drawable = -1, texture = 0, palette = 0 },  -- helmet
                        glasses_1 = { drawable = -1, texture = 0, palette = 0 }, -- gl
                        ears_1 = { drawable = -1, texture = 0, palette = 0 },    -- ears_1

                        -- shirt
                        tshirt_1 = { drawable = 15, texture = 0, palette = 0 },    -- t shirt
                        torso_1 = { drawable = 15, texture = 0, palette = 0 },     -- torso
                        decals_1 = { drawable = 0, texture = 0, palette = 0 },     -- decals
                        bproof_1 = { drawable = 0, texture = 0, palette = 0 },     -- bulletproof vest
                        arms = { drawable = 15, texture = 0, palette = 0 },        -- arms
                        watches_1 = { drawable = -1, texture = 0, palette = 0 },   -- watches
                        bracelets_1 = { drawable = -1, texture = 0, palette = 0 }, -- bracelets
                        bags_1 = { drawable = 0, texture = 0, palette = 0 },       -- bag

                        -- pants
                        pants_1 = { drawable = 61, texture = 0, palette = 0 }, -- pants
                        -- shoes
                        shoes_1 = { drawable = 34, texture = 0, palette = 0 }, -- shoes
                    }
                },
                [3] = {
                    title = 'SWAT Outfit',
                    playermodel = `mp_m_freemode_01`,
                    -- no whitelist means anyone who can open bag will able to see it
                    outfit = {
                        mask_1 = { drawable = 5, texture = 0, palette = 2 },
                        helmet_1 = { drawable = -1, texture = -1, palette = 0 },
                        glasses_1 = { drawable = -1, texture = -1, palette = 0 },
                        ears_1 = { drawable = -1, texture = -1, palette = 0 },
                        tshirt_1 = { drawable = 17, texture = 0, palette = 2 },
                        torso_1 = { drawable = 19, texture = 0, palette = 2 },
                        decals_1 = { drawable = 0, texture = 0, palette = 2 },
                        bproof_1 = { drawable = 0, texture = 0, palette = 0 },
                        arms = { drawable = 15, texture = 0, palette = 2 },
                        watches_1 = { drawable = -1, texture = -1, palette = 0 },
                        bracelets_1 = { drawable = -1, texture = -1, palette = 0 },
                        bags_1 = { drawable = 14, texture = 0, palette = 2 },
                        pants_1 = { drawable = 63, texture = 0, palette = 2 },
                        shoes_1 = { drawable = 34, texture = 0, palette = 2 },
                    },
                }
            }
        },

        ----------------------------<Police Outfit Bag END>----------------------------

        ----------------------------<EMS Outfit Bag Start>----------------------------
        ['ems_bag'] = {                                           -- bag name
            label = 'EMS Outfit Bag',
            model = 'reh_prop_reh_bag_outfit_01a',                -- make sure don't copy public bags models
            points = {                                            -- points where you want bags to be placed for jobs locations
                --
                vector4(253.1481, -1486.2019, 29.3761, 256.5067), -- example point for police station
            },
            whitelist = {                                         -- who can open bag
                enable = false,
                permissions = {
                    admingroups = {
                        --        ['admin'] = true
                    },
                    jobgroups = {
                        --      ['police'] = 0
                    },
                    aces = {
                        --         ['whitewidow'] = true,
                    },
                    identifiers = {
                        --         ['license:1c17a180cdad995771fea75248f0ed95569b9e6a'] = true,
                        --
                    },
                    characters = {
                        --         ['char1:1c17a180cdad995771fea75248f0ed95569b9e6a'] = true,

                    }
                },
            },
            outfits = {
                [1] = {
                    title = 'Duty Outfit',
                    playermodel = `mp_m_freemode_01`, -- male = `mp_m_freemode_01`, female = `mp_f_freemode_01`
                    whitelist = {                     -- only these job or grade will able to see this
                        ['police'] = { 0, 1, 2, 3 },
                        ['ambulance'] = { 0, 1, 2, 3 },
                    },
                    outfit = {
                        mask_1 = { drawable = 0, texture = 0, palette = 0 },     -- mask
                        helmet_1 = { drawable = -1, texture = 0, palette = 0 },  -- helmet
                        glasses_1 = { drawable = -1, texture = 0, palette = 0 }, -- gl
                        ears_1 = { drawable = -1, texture = 0, palette = 0 },    -- ears_1

                        -- shirt
                        tshirt_1 = { drawable = 15, texture = 0, palette = 0 },    -- t shirt
                        torso_1 = { drawable = 15, texture = 0, palette = 0 },     -- torso
                        decals_1 = { drawable = 0, texture = 0, palette = 0 },     -- decals
                        bproof_1 = { drawable = 0, texture = 0, palette = 0 },     -- bulletproof vest
                        arms = { drawable = 15, texture = 0, palette = 0 },        -- arms
                        watches_1 = { drawable = -1, texture = 0, palette = 0 },   -- watches
                        bracelets_1 = { drawable = -1, texture = 0, palette = 0 }, -- bracelets
                        bags_1 = { drawable = 0, texture = 0, palette = 0 },       -- bag

                        -- pants
                        pants_1 = { drawable = 61, texture = 0, palette = 0 }, -- pants
                        -- shoes
                        shoes_1 = { drawable = 34, texture = 0, palette = 0 }, -- shoes
                    }
                },
                [2] = {
                    title = 'Undercover Outfit',
                    playermodel = `mp_m_freemode_01`, -- male = `mp_m_freemode_01`, female = `mp_f_freemode_01`
                    whitelist = {
                        ['police'] = { 0, 1, 2, 3 },
                        ['ambulance'] = { 0, 1, 2, 3 },
                    },
                    outfit = {
                        mask_1 = { drawable = 0, texture = 0, palette = 0 },     -- mask
                        helmet_1 = { drawable = -1, texture = 0, palette = 0 },  -- helmet
                        glasses_1 = { drawable = -1, texture = 0, palette = 0 }, -- gl
                        ears_1 = { drawable = -1, texture = 0, palette = 0 },    -- ears_1

                        -- shirt
                        tshirt_1 = { drawable = 15, texture = 0, palette = 0 },    -- t shirt
                        torso_1 = { drawable = 15, texture = 0, palette = 0 },     -- torso
                        decals_1 = { drawable = 0, texture = 0, palette = 0 },     -- decals
                        bproof_1 = { drawable = 0, texture = 0, palette = 0 },     -- bulletproof vest
                        arms = { drawable = 15, texture = 0, palette = 0 },        -- arms
                        watches_1 = { drawable = -1, texture = 0, palette = 0 },   -- watches
                        bracelets_1 = { drawable = -1, texture = 0, palette = 0 }, -- bracelets
                        bags_1 = { drawable = 0, texture = 0, palette = 0 },       -- bag

                        -- pants
                        pants_1 = { drawable = 61, texture = 0, palette = 0 }, -- pants
                        -- shoes
                        shoes_1 = { drawable = 34, texture = 0, palette = 0 }, -- shoes
                    }
                },
                [3] = {
                    title = 'SWAT Outfit',
                    playermodel = `mp_m_freemode_01`,
                    outfit = {
                        mask_1 = { drawable = 5, texture = 0, palette = 2 },
                        helmet_1 = { drawable = -1, texture = -1, palette = 0 },
                        glasses_1 = { drawable = -1, texture = -1, palette = 0 },
                        ears_1 = { drawable = -1, texture = -1, palette = 0 },
                        tshirt_1 = { drawable = 17, texture = 0, palette = 2 },
                        torso_1 = { drawable = 19, texture = 0, palette = 2 },
                        decals_1 = { drawable = 0, texture = 0, palette = 2 },
                        bproof_1 = { drawable = 0, texture = 0, palette = 0 },
                        arms = { drawable = 15, texture = 0, palette = 2 },
                        watches_1 = { drawable = -1, texture = -1, palette = 0 },
                        bracelets_1 = { drawable = -1, texture = -1, palette = 0 },
                        bags_1 = { drawable = 14, texture = 0, palette = 2 },
                        pants_1 = { drawable = 63, texture = 0, palette = 2 },
                        shoes_1 = { drawable = 34, texture = 0, palette = 2 },
                    },
                }
            }
        },
        ----------------------------<EMS Outfit Bag END>----------------------------
    }
}

config.preview = true

config.animations = {
    onplace = { enable = true, dict = 'amb@medic@standing@tendtodead@idle_a', anim = 'idle_a' },
    onopen = { enable = true, dict = 'amb@medic@standing@tendtodead@idle_a', anim = 'idle_a' },
    onpickup = { enable = true, dict = 'amb@medic@standing@tendtodead@idle_a', anim = 'idle_a' },
    onchange = {
        mask = { duration = 2000, dict = 'mp_cp_stolen_tut', anim = 'b_think' },
        shirt = { duration = 4000, dict = 'mp_safehouseshower@male@', anim = 'male_shower_towel_dry_to_get_dressed' },
        pant = { duration = 4000, dict = 'mp_safehouseshower@male@', anim = 'male_shower_towel_dry_to_get_dressed' },
        shoes = { duration = 4000, dict = 'clothingshoes', anim = 'try_shoes_positive_d' },
    },
    onpreview = {
        enable = true,
        animations = {
            { dict = 'clothingshirt',        anim = 'check_out_c' },
            { dict = 'clothingshirt',        anim = 'try_shirt_positive_a' },
            { dict = 'random@getawaydriver', anim = 'gesture_nod_yes_soft' },
            { dict = 'clothingshirt',        anim = 'try_shirt_neutral_a' },
            { dict = 'clothingshoes',        anim = 'try_shoes_positive_d' },
            { dict = 'clothingshirt',        anim = 'try_shirt_neutral_b' },
        },
    }
}

config.notification = {
    title = 'Outfit Bag',
    duration = 5000
}

```

{% endcode %}
