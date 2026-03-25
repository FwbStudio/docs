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
Config.target = false -- if this enable then please use config/config_target.lua file for zone changes

Config.format = {
	currency = 'USD', -- This is the format of the currency, so that your currency sign appears correctly
	location = 'en-US' -- This is the location of your country, to format the decimal places according to your standard
}

Config.Bill = {
	enable = true,
	keybind = 'F6'
}

Config.AdminCommand = { -- /burgershop is command to open admin menu to refill
	admingroups = {
		['admin'] = true
	},
	aces = {
		--add this in server cfg
		--add_ace license:1c17a180cdad995771fea75248f0ed95569b9e6a "burgershop" allow #Capy
		['burgershop'] = true,

	},
	identifiers = {
		['license:wdwdwdw66916161w6d1w64d98w4d'] = true,
		['discord:wdwdwdw66916161w6d1w64d98w4d'] = true,
	},
	characters = {
		['char1:wdwdwdw66916161w6d1w64d98w4d'] = true,
		['char2:wdwdwdw66916161w6d1w64d98w4d'] = true,
	},
}

Config.Default = {
	stock = 300,
	price = 500
}

Config.Progbar_circle = false             -- if this is true then it will show circle progress bar else it will show line progress bar
Config.Progbar_circle_position = 'bottom' -- if you want to show circle progress bar then you can set position of it. middle, bottom

Config.Notification = { title = 'Burger Shop', duration = 5000, icon = 'fa-solid fa-burger', iconColor = nil }
Config.TextUi_Options = { -- you can make it nil if you don't want to pass anyu options with textui
	position = 'right',
	icon = 'fa-solid fa-burger',
	style = {
		borderRadius = 10,
		backgroundColor = "rgba(80, 230, 230, 0.589)",
		color = 'white',
	}
}

Config.AutoRefill = {
	enable = false, -- if this is true then it will refill stock automatically
	interval = 5, -- each 5 mint will refill
	stock = 4,   -- how many stock will refill according to upper time
	max_stock = 300 -- max stock refill limit
}

Config.Markers = { -- only work when config.target = false
	['boss_action'] = {
		enable = true, -- make it true or false to enable or disable marker preview
		marker_id = 22,
		marker_color = { r = 255, g = 0, b = 0, a = 100 },
		marker_draw_distance = 4.0,
		marker_access_distance = 1.0
	},
	['management'] = {
		enable = true, -- make it true or false to enable or disable marker preview
		marker_id = 20,
		marker_color = { r = 255, g = 0, b = 0, a = 100 },
		marker_draw_distance = 4.0,
		marker_access_distance = 1.0
	},
	['crafting'] = {
		enable = true, -- make it true or false to enable or disable marker preview
		marker_id = 24,
		marker_color = { r = 0, g = 255, b = 0, a = 255 },
		marker_draw_distance = 4.0,
		marker_access_distance = 1.0
	},
	['storage'] = {
		enable = true, -- make it true or false to enable or disable marker preview
		marker_id = 20,
		marker_color = { r = 255, g = 0, b = 0, a = 100 },
		marker_draw_distance = 4.0,
		marker_access_distance = 1.0
	},
	['sell_coords'] = {
		enable = true, -- make it true or false to enable or disable marker preview
		marker_id = 21,
		marker_color = { r = 255, g = 0, b = 0, a = 100 },
		marker_draw_distance = 4.0,
		marker_access_distance = 1.0
	},
	['delivery'] = {
		enable = true, -- make it true or false to enable or disable marker preview
		marker_id = 21,
		marker_color = { r = 255, g = 0, b = 0, a = 100 },
		marker_draw_distance = 10.0,
		marker_access_distance = 1.0
	},
	['outfit'] = {
		enable = true, -- make it true or false to enable or disable marker preview
		marker_id = 21,
		marker_color = { r = 255, g = 0, b = 0, a = 100 },
		marker_draw_distance = 10.0,
		marker_access_distance = 1.0
	}
}

Config.Shop = {
	blip = { enable = true, name = 'Burger Shop', sprite = 106, color = 5, size = 1.0, radius = 0.0, radius_color = 4 },
	boss_action = vector3(-814.8870, -811.4341, 19.8723),
	management = vector3(-826.7899, -804.1658, 19.8710),
	managementRankFor = {
		price = 2,
		stock = 2,
	},
	crafting = {
		menu = vector3(-816.6198, -802.9443, 19.8720),
		data = {

			['fs_b_bacon_double_cheeseburger'] = { -- reward item name
				reward = 1,     -- reward item amount
				required = {    -- required items for crafting
					{item = 'fs_b_cheese', quantity = 1, willremove = true},
					{item = 'fs_b_burger_buns', quantity = 1, willremove = true},
					{item = 'fs_b_vegetables', quantity = 1, willremove = true},
					{item = 'fs_b_sauce', quantity = 1, willremove = true},
					{item = 'fs_b_bacon', quantity = 1, willremove = true},
				},
				steps = {
					-- botom commented lines are example of if you want to override animation or scenario
					-- {pos = vector4(-785.6154, -613.6817, 30.2791, 94.3735),  delay = 10, msg = 'Working...', anim = { dict = 'timetable@tracy@ig_5@idle_a', clip = 'idle_a' }},	-- x, y, z, heading, second, message
					-- {pos = vector4(-783.9978, -611.5065, 30.2791, 317.2552), delay = 10, msg = 'Working...', anim = {dict = 'random@shop_tattoo', clip = '_idle_a'}},	-- x, y, z, heading, second, message
					{ pos = vector4(-819.1113, -805.2896, 19.8717, 179.0076), delay = 10, msg = 'Working...', anim = { scenario = 'prop_human_bbq' } }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_bacon_ham_sausage'] = { -- reward item name
				reward = 1,        -- reward item amount
				required = {       -- required items for crafting
				{item = 'fs_b_cheese', quantity = 1, willremove = true},
				{item = 'fs_b_burger_buns', quantity = 1, willremove = true},
				{item = 'fs_b_vegetables', quantity = 1, willremove = true},
				{item = 'fs_b_sauce', quantity = 1, willremove = true},
				{item = 'fs_b_bacon', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-819.1113, -805.2896, 19.8717, 179.0076), delay = 10, msg = 'Working...', anim = { scenario = 'prop_human_bbq' } }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_bacon_king'] = { -- reward item name
				reward = 1,     -- reward item amount
				required = {    -- required items for crafting
				{item = 'fs_b_cheese', quantity = 1, willremove = true},
				{item = 'fs_b_burger_buns', quantity = 1, willremove = true},
				{item = 'fs_b_vegetables', quantity = 1, willremove = true},
				{item = 'fs_b_sauce', quantity = 1, willremove = true},
				{item = 'fs_b_bacon', quantity = 2, willremove = true},
				},
				steps = {
					{ pos = vector4(-819.1113, -805.2896, 19.8717, 179.0076), delay = 10, msg = 'Working...', anim = { scenario = 'prop_human_bbq' } }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_barqs_diet_beer'] = { -- reward item name
				reward = 1,       -- reward item amount
				required = {      -- required items for crafting
					{item = 'fs_b_carbonated_water', quantity = 1, willremove = true},
					{item = 'fs_b_flavor', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-822.4120, -799.2883, 19.8711, 354.0674), delay = 10, msg = 'Working...' }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_big_fish'] = { -- reward item name
				reward = 1, -- reward item amount
				required = { -- required items for crafting
					{item = 'fs_b_cheese', quantity = 1, willremove = true},
					{item = 'fs_b_burger_buns', quantity = 1, willremove = true},
					{item = 'fs_b_vegetables', quantity = 1, willremove = true},
					{item = 'fs_b_sauce', quantity = 1, willremove = true},
					{item = 'fs_b_fried_fish', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-819.1113, -805.2896, 19.8717, 179.0076), delay = 10, msg = 'Working...', anim = { scenario = 'prop_human_bbq' } }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_barqs_beer'] = { -- reward item name
				reward = 1,         -- reward item amount
				required = {        -- required items for crafting
					{item = 'fs_b_carbonated_water', quantity = 1, willremove = true},
					{item = 'fs_b_flavor', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-822.4120, -799.2883, 19.8711, 354.0674), delay = 10, msg = 'Working...' }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_cafe_decaf'] = { -- reward item name
				reward = 1,    -- reward item amount
				required = {   -- required items for crafting
					{item = 'fs_b_raw_coffee', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-822.4120, -799.2883, 19.8711, 354.0674), delay = 10, msg = 'Working...' }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_chicken_jr'] = { -- reward item name
				reward = 1,         -- reward item amount
				required = {        -- required items for crafting
				{item = 'fs_b_cheese', quantity = 1, willremove = true},
				{item = 'fs_b_burger_buns', quantity = 1, willremove = true},
				{item = 'fs_b_vegetables', quantity = 1, willremove = true},
				{item = 'fs_b_sauce', quantity = 1, willremove = true},
				{item = 'fs_b_chicken', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-819.1113, -805.2896, 19.8717, 179.0076), delay = 10, msg = 'Working...', anim = { scenario = 'prop_human_bbq' } }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_coca_cola'] = { -- reward item name
				reward = 1,  -- reward item amount
				required = { -- required items for crafting
					{item = 'fs_b_carbonated_water', quantity = 1, willremove = true},
					{item = 'fs_b_flavor', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-822.4120, -799.2883, 19.8711, 354.0674), delay = 10, msg = 'Working...' }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_diet_coke'] = { -- reward item name
				reward = 1,  -- reward item amount
				required = { -- required items for crafting
					{item = 'fs_b_carbonated_water', quantity = 1, willremove = true},
					{item = 'fs_b_flavor', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-822.4120, -799.2883, 19.8711, 354.0674), delay = 10, msg = 'Working...' }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_dr_pepper'] = { -- reward item name
				reward = 1,        -- reward item amount
				required = {       -- required items for crafting
					{item = 'fs_b_carbonated_water', quantity = 1, willremove = true},
					{item = 'fs_b_flavor', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-822.4120, -799.2883, 19.8711, 354.0674), delay = 10, msg = 'Working...' }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_fanta_orange'] = { -- reward item name
				reward = 1,      -- reward item amount
				required = {     -- required items for crafting
					{item = 'fs_b_carbonated_water', quantity = 1, willremove = true},
					{item = 'fs_b_flavor', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-822.4120, -799.2883, 19.8711, 354.0674), delay = 10, msg = 'Working...' }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_fruit_punch'] = { -- reward item name
				reward = 1,         -- reward item amount
				required = {     -- required items for crafting
					{item = 'fs_b_carbonated_water', quantity = 1, willremove = true},
					{item = 'fs_b_flavor', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-822.4120, -799.2883, 19.8711, 354.0674), delay = 10, msg = 'Working...' }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_hamburger'] = { -- reward item name
				reward = 1,  -- reward item amount
				required = {     -- required items for crafting
				{item = 'fs_b_cheese', quantity = 1, willremove = true},
				{item = 'fs_b_burger_buns', quantity = 1, willremove = true},
				{item = 'fs_b_vegetables', quantity = 1, willremove = true},
				{item = 'fs_b_sauce', quantity = 1, willremove = true},
				{item = 'fs_b_chicken', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-819.1113, -805.2896, 19.8717, 179.0076), delay = 10, msg = 'Working...', anim = { scenario = 'prop_human_bbq' } }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_iced_tea'] = { -- reward item name
				reward = 1,      -- reward item amount
				required = {     -- required items for crafting
					{item = 'fs_b_raw_tea', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-822.4120, -799.2883, 19.8711, 354.0674), delay = 10, msg = 'Working...' }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_mozzarella_sticks'] = { -- reward item name
				reward = 1,      -- reward item amount
				required = {     -- required items for crafting
					
					{item = 'fs_d_cheese', quantity = 1, willremove = true},
					{item = 'fs_b_bread_crumbs', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-819.1113, -805.2896, 19.8717, 179.0076), delay = 10, msg = 'Working...', anim = { scenario = 'prop_human_bbq' } }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_sprite'] = { -- reward item name
				reward = 1,          -- reward item amount
				required = {     -- required items for crafting
					{item = 'fs_b_carbonated_water', quantity = 1, willremove = true},
					{item = 'fs_b_flavor', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-822.4120, -799.2883, 19.8711, 354.0674), delay = 10, msg = 'Working...' }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_sprite_zero'] = { -- reward item name
				reward = 1,            -- reward item amount
				required = {     -- required items for crafting
					{item = 'fs_b_carbonated_water', quantity = 1, willremove = true},
					{item = 'fs_b_flavor', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-822.4120, -799.2883, 19.8711, 354.0674), delay = 10, msg = 'Working...' }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_yello_mello'] = { -- reward item name
				reward = 1,       -- reward item amount
				required = {     -- required items for crafting
					{item = 'fs_b_carbonated_water', quantity = 1, willremove = true},
					{item = 'fs_b_flavor', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-822.4120, -799.2883, 19.8711, 354.0674), delay = 10, msg = 'Working...' }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_cheesy_tots'] = { -- reward item name
				reward = 1,              -- reward item amount
				required = {     -- required items for crafting
					{item = 'fs_d_cheese', quantity = 1, willremove = true},
					{item = 'fs_b_bread_crumbs', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-819.1113, -805.2896, 19.8717, 179.0076), delay = 10, msg = 'Working...', anim = { scenario = 'prop_human_bbq' } }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_chicken_fries'] = { -- reward item name
				reward = 1,       -- reward item amount
				required = {     -- required items for crafting
					{item = 'fs_b_chicken', quantity = 1, willremove = true},
					{item = 'fs_b_bread_crumbs', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-819.1113, -805.2896, 19.8717, 179.0076), delay = 10, msg = 'Working...', anim = { scenario = 'prop_human_bbq' } }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_chicken_nuggets'] = { -- reward item name
				reward = 1,     -- reward item amount
				required = {     -- required items for crafting
					{item = 'fs_b_chicken', quantity = 1, willremove = true},
					{item = 'fs_b_bread_crumbs', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-819.1113, -805.2896, 19.8717, 179.0076), delay = 10, msg = 'Working...', anim = { scenario = 'prop_human_bbq' } }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_chocolate_cookie_shake'] = { -- reward item name
				reward = 1, -- reward item amount
				required = { -- required items for crafting
					  {item = 'fs_b_milk', quantity = 1, willremove = true},
					  {item = 'fs_d_flavor', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-822.4120, -799.2883, 19.8711, 354.0674), delay = 10, msg = 'Working...' }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_chocolate_shake'] = { -- reward item name
				reward = 1, -- reward item amount
				required = { -- required items for crafting
					  {item = 'fs_b_milk', quantity = 1, willremove = true},
					  {item = 'fs_d_flavor', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-822.4120, -799.2883, 19.8711, 354.0674), delay = 10, msg = 'Working...' }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_cookie_shake'] = { -- reward item name
				reward = 1,  -- reward item amount
				required = { -- required items for crafting
					  {item = 'fs_b_milk', quantity = 1, willremove = true},
					  {item = 'fs_d_flavor', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-822.4120, -799.2883, 19.8711, 354.0674), delay = 10, msg = 'Working...' }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_double_cheeseburger'] = { -- reward item name
				reward = 1, -- reward item amount
				required = { -- required items for crafting
				{item = 'fs_b_cheese', quantity = 2, willremove = true},
				{item = 'fs_b_burger_buns', quantity = 1, willremove = true},
				{item = 'fs_b_vegetables', quantity = 1, willremove = true},
				{item = 'fs_b_sauce', quantity = 1, willremove = true},
				{item = 'fs_b_chicken', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-819.1113, -805.2896, 19.8717, 179.0076), delay = 10, msg = 'Working...', anim = { scenario = 'prop_human_bbq' } }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_double_sausage_biscuit'] = { -- reward item name
				reward = 1, -- reward item amount
				required = { -- required items for crafting
				{item = 'fs_b_cheese', quantity = 1, willremove = true},
				{item = 'fs_b_burger_buns', quantity = 1, willremove = true},
				{item = 'fs_b_vegetables', quantity = 1, willremove = true},
				{item = 'fs_b_sauce', quantity = 1, willremove = true},
				{item = 'fs_b_chicken', quantity = 2, willremove = true},
				},
				steps = {
					{ pos = vector4(-819.1113, -805.2896, 19.8717, 179.0076), delay = 10, msg = 'Working...', anim = { scenario = 'prop_human_bbq' } }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_egg_normous_burrito'] = { -- reward item name
				reward = 1, -- reward item amount
				required = { -- required items for crafting
				{item = 'fs_b_cheese', quantity = 1, willremove = true},
				{item = 'fs_b_flour', quantity = 1, willremove = true},
				{item = 'fs_b_vegetables', quantity = 1, willremove = true},
				{item = 'fs_b_sauce', quantity = 1, willremove = true},
				{item = 'fs_b_chicken', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-819.1113, -805.2896, 19.8717, 179.0076), delay = 10, msg = 'Working...', anim = { scenario = 'prop_human_bbq' } }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_family_bundle_classic'] = { -- reward item name
				reward = 1, -- reward item amount
				required = { -- required items for crafting
				{item = 'fs_b_cheese', quantity = 4, willremove = true},
				{item = 'fs_b_burger_buns', quantity = 4, willremove = true},
				{item = 'fs_b_vegetables', quantity = 1, willremove = true},
				{item = 'fs_b_sauce', quantity = 1, willremove = true},
				{item = 'fs_b_chicken', quantity = 2, willremove = true},
				{item = 'fs_b_potato', quantity = 2, willremove = true},
				{item = 'fs_b_carbonated_water', quantity = 2, willremove = true},
				},
				steps = {
					{ pos = vector4(-819.1113, -805.2896, 19.8717, 179.0076), delay = 10, msg = 'Working...', anim = { scenario = 'prop_human_bbq' } }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_jalapeno_cheddar_bites'] = { -- reward item name
				reward = 1, -- reward item amount
				required = { -- required items for crafting
					  {item = 'fs_b_cheese', quantity = 1, willremove = true},
					  {item = 'fs_b_bread_crumbs', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-819.1113, -805.2896, 19.8717, 179.0076), delay = 10, msg = 'Working...', anim = { scenario = 'prop_human_bbq' } }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_original_chicken_sandwich'] = { -- reward item name
				reward = 1, -- reward item amount
				required = { -- required items for crafting
					{item = 'fs_b_cheese', quantity = 1, willremove = true},
					{item = 'fs_b_burger_buns', quantity = 1, willremove = true},
					{item = 'fs_b_vegetables', quantity = 1, willremove = true},
					{item = 'fs_b_sauce', quantity = 1, willremove = true},
					{item = 'fs_b_chicken', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-819.1113, -805.2896, 19.8717, 179.0076), delay = 10, msg = 'Working...', anim = { scenario = 'prop_human_bbq' } }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_pancake_sausage_platter'] = { -- reward item name
				reward = 1, -- reward item amount
				required = { -- required items for crafting
					  {item = 'fs_b_milk', quantity = 1, willremove = true},
					  {item = 'fs_d_flavor', quantity = 1, willremove = true},
					  {item = 'fs_b_flour', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-819.1113, -805.2896, 19.8717, 179.0076), delay = 10, msg = 'Working...', anim = { scenario = 'prop_human_bbq' } }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_pink_lemonade'] = { -- reward item name
				reward = 1, -- reward item amount
				required = { -- required items for crafting
					  {item = 'fs_d_carbonated_water', quantity = 1, willremove = true},
					  {item = 'fs_d_flavor', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-822.4120, -799.2883, 19.8711, 354.0674), delay = 10, msg = 'Working...' }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_plain_iced_coffee'] = { -- reward item name
				reward = 1, -- reward item amount
				required = { -- required items for crafting
					  {item = 'fs_b_raw_coffee', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-822.4120, -799.2883, 19.8711, 354.0674), delay = 10, msg = 'Working...' }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_rodeo_burger'] = { -- reward item name
				reward = 1, -- reward item amount
				required = { -- required items for crafting
				{item = 'fs_b_potato', quantity = 1, willremove = true},
				{item = 'fs_b_burger_buns', quantity = 1, willremove = true},
				{item = 'fs_b_bread_crumbs', quantity = 1, willremove = true},
				{item = 'fs_b_sauce', quantity = 1, willremove = true},
				{item = 'fs_b_chicken', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-819.1113, -805.2896, 19.8717, 179.0076), delay = 10, msg = 'Working...', anim = { scenario = 'prop_human_bbq' } }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_small_classic_fries'] = { -- reward item name
				reward = 1, -- reward item amount
				required = { -- required items for crafting
					  {item = 'fs_b_potato', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-819.1113, -805.2896, 19.8717, 179.0076), delay = 10, msg = 'Working...', anim = { scenario = 'prop_human_bbq' } }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_small_hash_browns'] = { -- reward item name
				reward = 1, -- reward item amount
				required = { -- required items for crafting
					  {item = 'fs_b_potato', quantity = 1, willremove = true},
					  {item = 'fs_b_bread_crumbs', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-819.1113, -805.2896, 19.8717, 179.0076), delay = 10, msg = 'Working...', anim = { scenario = 'prop_human_bbq' } }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_soft_serve_cone'] = { -- reward item name
				reward = 1, -- reward item amount
				required = { -- required items for crafting
					  {item = 'fs_b_milk', quantity = 1, willremove = true},
					  {item = 'fs_d_flavor', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-822.4120, -799.2883, 19.8711, 354.0674), delay = 10, msg = 'Working...' }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_soft_serve_cup'] = { -- reward item name
				reward = 1, -- reward item amount
				required = { -- required items for crafting
					  {item = 'fs_b_milk', quantity = 1, willremove = true},
					  {item = 'fs_d_flavor', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-822.4120, -799.2883, 19.8711, 354.0674), delay = 10, msg = 'Working...' }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_spicy_deluxe_sandwich'] = { -- reward item name
				reward = 1, -- reward item amount
				required = { -- required items for crafting
				{item = 'fs_b_cheese', quantity = 1, willremove = true},
				{item = 'fs_b_burger_buns', quantity = 1, willremove = true},
				{item = 'fs_b_vegetables', quantity = 1, willremove = true},
				{item = 'fs_b_sauce', quantity = 1, willremove = true},
				{item = 'fs_b_chicken', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-819.1113, -805.2896, 19.8717, 179.0076), delay = 10, msg = 'Working...', anim = { scenario = 'prop_human_bbq' } }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_strawberry_shake'] = { -- reward item name
				reward = 1, -- reward item amount
				required = { -- required items for crafting
					  {item = 'fs_b_milk', quantity = 1, willremove = true},
					  {item = 'fs_d_flavor', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-822.4120, -799.2883, 19.8711, 354.0674), delay = 10, msg = 'Working...' }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_sundae_pie'] = { -- reward item name
				reward = 1, -- reward item amount
				required = { -- required items for crafting
					  {item = 'fs_b_flour', quantity = 1, willremove = true},
					  {item = 'fs_d_flavor', quantity = 1, willremove = true},
					  {item = 'fs_b_milk', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-819.1113, -805.2896, 19.8717, 179.0076), delay = 10, msg = 'Working...' }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_texas_double_whopper'] = { -- reward item name
				reward = 1, -- reward item amount
				required = { -- required items for crafting
				{item = 'fs_b_cheese', quantity = 1, willremove = true},
				{item = 'fs_b_burger_buns', quantity = 1, willremove = true},
				{item = 'fs_b_vegetables', quantity = 1, willremove = true},
				{item = 'fs_b_sauce', quantity = 1, willremove = true},
				{item = 'fs_b_chicken', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-819.1113, -805.2896, 19.8717, 179.0076), delay = 10, msg = 'Working...', anim = { scenario = 'prop_human_bbq' } }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_vanilla_shake'] = { -- reward item name
				reward = 1, -- reward item amount
				required = { -- required items for crafting
					  {item = 'fs_b_milk', quantity = 1, willremove = true},
					  {item = 'fs_d_flavor', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-822.4120, -799.2883, 19.8711, 354.0674), delay = 10, msg = 'Working...' }, -- x, y, z, heading, second, message
				}
			},
			['fs_b_whopper_with_cheese'] = { -- reward item name
				reward = 1, -- reward item amount
				required = { -- required items for crafting
				{item = 'fs_b_cheese', quantity = 1, willremove = true},
				{item = 'fs_b_burger_buns', quantity = 1, willremove = true},
				{item = 'fs_b_vegetables', quantity = 1, willremove = true},
				{item = 'fs_b_sauce', quantity = 1, willremove = true},
				{item = 'fs_b_chicken', quantity = 1, willremove = true},
				},
				steps = {
					{ pos = vector4(-819.1113, -805.2896, 19.8717, 179.0076), delay = 10, msg = 'Working...', anim = { scenario = 'prop_human_bbq' } }, -- x, y, z, heading, second, message
				}
			},
		 
		}
	},
	storage = {
		pos = vector4(-813.5227, -803.0497, 19.8725, 0.0), -- x, y, z, heading
		prop = nil,                                        --"prop_paints_can07", -- prop spawn name
		items = {
			fs_b_cheese = {
			    name = 'Cheese',                        		-- item name
			    price = 0,                                     -- price of the item. set it 0 if you don't want to buy with society money
			    slots = 20,                                     -- container size
			    available = 20,                                 -- available in stock
			    regeneration = 1,                              -- in minute
			},
			fs_b_burger_buns = {
			    name = 'Burger Buns',                        		-- item name
			    price = 0,                                     -- price of the item. set it 0 if you don't want to buy with society money
			    slots = 20,                                     -- container size
			    available = 20,                                 -- available in stock
			    regeneration = 1,                              -- in minute
			},
			fs_b_vegetables = {
			    name = 'Vegetables',                        		-- item name
			    price = 0,                                     -- price of the item. set it 0 if you don't want to buy with society money
			    slots = 20,                                     -- container size
			    available = 20,                                 -- available in stock
			    regeneration = 1,                              -- in minute
			},
			fs_b_chicken = {
			    name = 'Chicken',                        		-- item name
			    price = 0,                                     -- price of the item. set it 0 if you don't want to buy with society money
			    slots = 20,                                     -- container size
			    available = 20,                                 -- available in stock
			    regeneration = 1,                              -- in minute
			},
			fs_b_sauce = {
			    name = 'Sauce',                        		-- item name
			    price = 0,                                     -- price of the item. set it 0 if you don't want to buy with society money
			    slots = 20,                                     -- container size
			    available = 20,                                 -- available in stock
			    regeneration = 1,                              -- in minute
			},
			fs_b_bacon = {
			    name = 'Bacon',                        		-- item name
			    price = 0,                                     -- price of the item. set it 0 if you don't want to buy with society money
			    slots = 20,                                     -- container size
			    available = 20,                                 -- available in stock
			    regeneration = 1,                              -- in minute
			},
			fs_b_flavor = {
			    name = 'Flavor',                        		-- item name
			    price = 0,                                     -- price of the item. set it 0 if you don't want to buy with society money
			    slots = 20,                                     -- container size
			    available = 20,                                 -- available in stock
			    regeneration = 1,                              -- in minute
			},
			fs_b_carbonated_water = {
			    name = 'Carbonated Water',                        		-- item name
			    price = 0,                                     -- price of the item. set it 0 if you don't want to buy with society money
			    slots = 20,                                     -- container size
			    available = 20,                                 -- available in stock
			    regeneration = 1,                              -- in minute
			},
			fs_b_milk = {
			    name = 'Milk',                        		-- item name
			    price = 0,                                     -- price of the item. set it 0 if you don't want to buy with society money
			    slots = 20,                                     -- container size
			    available = 20,                                 -- available in stock
			    regeneration = 1,                              -- in minute
			},
			fs_b_bread_crumbs = {
			    name = 'Bread Crumbs',                        		-- item name
			    price = 0,                                     -- price of the item. set it 0 if you don't want to buy with society money
			    slots = 20,                                     -- container size
			    available = 20,                                 -- available in stock
			    regeneration = 1,                              -- in minute
			},
			fs_b_flour = {
			    name = 'Flour',                        		-- item name
			    price = 0,                                     -- price of the item. set it 0 if you don't want to buy with society money
			    slots = 20,                                     -- container size
			    available = 20,                                 -- available in stock
			    regeneration = 1,                              -- in minute
			},
			fs_b_fried_fish = {
			    name = 'Fried Fish',                        		-- item name
			    price = 0,                                     -- price of the item. set it 0 if you don't want to buy with society money
			    slots = 20,                                     -- container size
			    available = 20,                                 -- available in stock
			    regeneration = 1,                              -- in minute
			},
			fs_b_raw_coffee = {
			    name = 'Raw Coffee',                        		-- item name
			    price = 0,                                     -- price of the item. set it 0 if you don't want to buy with society money
			    slots = 20,                                     -- container size
			    available = 20,                                 -- available in stock
			    regeneration = 1,                              -- in minute
			},
			fs_b_raw_tea = {
			    name = 'Raw Tea',                        		-- item name
			    price = 0,                                     -- price of the item. set it 0 if you don't want to buy with society money
			    slots = 20,                                     -- container size
			    available = 20,                                 -- available in stock
			    regeneration = 1,                              -- in minute
			},
			fs_b_potato = {
			    name = 'Potato',                        		-- item name
			    price = 0,                                     -- price of the item. set it 0 if you don't want to buy with society money
			    slots = 20,                                     -- container size
			    available = 20,                                 -- available in stock
			    regeneration = 1,                              -- in minute
			},
			


		}
	},
	sell_coords = { -- The coordinates where customes will buy things on this store (coordinates composed of x, y, z)
		vector3(-829.0488, -804.7988, 19.8709),
		vector3(-829.1146, -801.0811, 19.8709),
		vector3(-829.1124, -799.1459, 19.8709),
	},
	data = {
		market_items = {        -- Here you configure the items definitions
			['fs_b_bacon_double_cheeseburger'] = { -- The item ID
				name = "Double Cheese Burger", -- The item display name
				page = 0,       -- Set on which page this item will appear
				process = true,
			},
			['fs_b_bacon_ham_sausage'] = { -- The item ID
				name = "Ham Sausage", -- The item display name
				page = 0,          -- Set on which page this item will appear
				process = true,
			},
			['fs_b_bacon_king'] = { -- The item ID
				name = "Bacon King", -- The item display name
				page = 0,       -- Set on which page this item will appear
				process = true,
			},
			['fs_b_barqs_diet_beer'] = { -- The item ID
				name = "Barqs Diet Beer", -- The item display name
				page = 1,         -- Set on which page this item will appear
				process = true,
			},
			['fs_b_big_fish'] = { -- The item ID
				name = "Big Fish", -- The item display name
				page = 0, -- Set on which page this item will appear
				process = true,
			},
			['fs_b_barqs_beer'] = { -- The item ID
				name = "Barqs Beer", -- The item display name
				page = 1,           -- Set on which page this item will appear
				process = true,
			},
			['fs_b_cafe_decaf'] = { -- The item ID
				name = "Cafe Decaf", -- The item display name
				page = 1,      -- Set on which page this item will appear
				process = true,
			},
			['fs_b_chicken_jr'] = { -- The item ID
				name = "Chicken Jr", -- The item display name
				page = 0,           -- Set on which page this item will appear
				process = true,
			},
			['fs_b_coca_cola'] = { -- The item ID
				name = "Coca Cola", -- The item display name
				page = 1,    -- Set on which page this item will appear
				process = true,
			},
			['fs_b_diet_coke'] = { -- The item ID
				name = "Diet Coke", -- The item display name
				page = 1,    -- Set on which page this item will appear
				process = true,
			},
			['fs_b_dr_pepper'] = { -- The item ID
				name = "Dr Pepper", -- The item display name
				page = 1,          -- Set on which page this item will appear
				process = true,
			},
			['fs_b_fanta_orange'] = { -- The item ID
				name = "Fanta Orange", -- The item display name
				page = 1,        -- Set on which page this item will appear
				process = true,
			},
			['fs_b_fruit_punch'] = { -- The item ID
				name = "Fruit Punch", -- The item display name
				page = 1,           -- Set on which page this item will appear
				process = true,
			},
			['fs_b_hamburger'] = { -- The item ID
				name = "Hamburger", -- The item display name
				page = 0,        -- Set on which page this item will appear
				process = true,
			},
			['fs_b_iced_tea'] = { -- The item ID
				name = "Iced Tea", -- The item display name
				page = 1,    -- Set on which page this item will appear
				process = true,
			},
			['fs_b_mozzarella_sticks'] = { -- The item ID
				name = "Mozzarella Sticks", -- The item display name
				page = 2,        -- Set on which page this item will appear
				process = true,
			},
			['fs_b_sprite'] = { -- The item ID
				name = "Sprite", -- The item display name
				page = 1,            -- Set on which page this item will appear
				process = true,
			},
			['fs_b_sprite_zero'] = { -- The item ID
				name = "Sprite Zero", -- The item display name
				page = 1,              -- Set on which page this item will appear
				process = true,
			},
			['fs_b_yello_mello'] = { -- The item ID
				name = "Yello Mello", -- The item display name
				page = 1,         -- Set on which page this item will appear
				process = true,
			},
			['fs_b_cheesy_tots'] = { -- The item ID
				name = "Cheesy tots", -- The item display name
				page = 2,         -- Set on which page this item will appear
				process = true,
			},
			['fs_b_chicken_fries'] = { -- The item ID
				name = "Chicken Fries", -- The item display name
				page = 2,       -- Set on which page this item will appear
				process = true,
			},
			['fs_b_chicken_nuggets'] = { -- The item ID
				name = "Chicken Nuggets", -- The item display name
				page = 2, -- Set on which page this item will appear
				process = true,
			},
			['fs_b_chocolate_cookie_shake'] = { -- The item ID
				name = "Chocolate Cookie Shake", -- The item display name
				page = 1, -- Set on which page this item will appear
				process = true,
			},
			['fs_b_chocolate_shake'] = { -- The item ID
				name = "Chocolate Shake", -- The item display name
				page = 1,    -- Set on which page this item will appear
				process = true,
			},
			['fs_b_cookie_shake'] = { -- The item ID
				name = "Cookie Shake", -- The item display name
				page = 1,   -- Set on which page this item will appear
				process = true,
			},
			['fs_b_double_cheeseburger'] = { -- The item ID
				name = "Double Cheeseburger", -- The item display name
				page = 0, -- Set on which page this item will appear
				process = true,
			},
			['fs_b_double_sausage_biscuit'] = { -- The item ID
				name = "Double Sausage Biscuit", -- The item display name
				page = 0, -- Set on which page this item will appear
				process = true,
			},
			['fs_b_egg_normous_burrito'] = { -- The item ID
				name = "Normous Burrito", -- The item display name
				page = 2, -- Set on which page this item will appear
				process = true,
			},
			['fs_b_family_bundle_classic'] = { -- The item ID
				name = "Family Bundle", -- The item display name
				page = 2, -- Set on which page this item will appear
				process = true,
			},
			['fs_b_jalapeno_cheddar_bites'] = { -- The item ID
				name = "Jalapeno Cheddar Bites", -- The item display name
				page = 2, -- Set on which page this item will appear
				process = true,
			},
			['fs_b_original_chicken_sandwich'] = { -- The item ID
				name = "Original Chicken Sandwich", -- The item display name
				page = 0, -- Set on which page this item will appear
				process = true,
			},
			['fs_b_pancake_sausage_platter'] = { -- The item ID
				name = "Pancake Sausage Platter", -- The item display name
				page = 2, -- Set on which page this item will appear
				process = true,
			},
			['fs_b_pink_lemonade'] = { -- The item ID
				name = "Pink Lemonade", -- The item display name
				page = 1, -- Set on which page this item will appear
				process = true,
			},
			['fs_b_plain_iced_coffee'] = { -- The item ID
				name = "Plain Iced Coffee", -- The item display name
				page = 1, -- Set on which page this item will appear
				process = true,
			},
			['fs_b_rodeo_burger'] = { -- The item ID
				name = "Rodeo Burger", -- The item display name
				page = 0, -- Set on which page this item will appear
				process = true,
			},
			 
			['fs_b_small_classic_fries'] = { -- The item ID
				name = "Small Classic Fries", -- The item display name
				page = 2, -- Set on which page this item will appear
				process = true,
			},
			['fs_b_small_hash_browns'] = { -- The item ID
				name = "Small Hash Browns", -- The item display name
				page = 2, -- Set on which page this item will appear
				process = true,
			},
			['fs_b_soft_serve_cone'] = { -- The item ID
				name = "Soft Serve Cone", -- The item display name
				page = 2, -- Set on which page this item will appear
				process = true,
			},
			['fs_b_soft_serve_cup'] = { -- The item ID
				name = "Soft Serve Cup", -- The item display name
				page = 2, -- Set on which page this item will appear
				process = true,
			},
			['fs_b_spicy_deluxe_sandwich'] = { -- The item ID
				name = "Spicy Deluxe Sandwich", -- The item display name
				page = 0, -- Set on which page this item will appear
				process = true,
			},
			['fs_b_strawberry_shake'] = { -- The item ID
				name = "Strawberry Shake", -- The item display name
				page = 1, -- Set on which page this item will appear
				process = true,
			},
			['fs_b_sundae_pie'] = { -- The item ID
				name = "Sundae Pie", -- The item display name
				page = 2, -- Set on which page this item will appear
				process = true,
			},
			['fs_b_texas_double_whopper'] = { -- The item ID
				name = "Texas Double Whopper", -- The item display name
				page = 0, -- Set on which page this item will appear
				process = true,
			},
			['fs_b_vanilla_shake'] = { -- The item ID
				name = "Vanilla Shake", -- The item display name
				page = 1, -- Set on which page this item will appear
				process = true,
			},
			['fs_b_whopper_with_cheese'] = { -- The item ID
				name = "Cheese Whopper", -- The item display name
				page = 0, -- Set on which page this item will appear
				process = true,
			},
			
		},
		pagination = { -- Create pages to your market items (max 10 pages)
			[0] = { name = "Burger", icon = "fa-solid fa-burger" },
			[1] = { name = "Drinks", icon = "fa-solid fa-glass-water" },
			[2] = { name = "Extra", icon = "fa-solid fa-utensils" },
			
		},
	}
}

Config.OutfitsMenu = {
	-- context_menu = true, -- if you want to use ox_lib context menu to open outfits menu
	-- context_menu = false -- if you want to use ox_lib mobile menu to open outfits menu
	context_menu = false,
	position = 'bottom-right', --only if context_menu = false
	coords = vec3(-1380.1437, -917.4319, 11.2487)
}
Config.Outfits = { -- Only for dev modification if your not a dev don't touch it and contact ur dev please
	{
		label = 'Employee Outfit', --label of outfit for menu
		ranks = {0,1,2}, -- number like 1 or table of numbers like  {1,2,3}
		uniform = {
			male = {
				torso = { drawable = 10, texture = 1 },
				pant = { drawable = 10, texture = 1 },
				tshirt = { drawable = 10, texture = 1 },
				mask = { drawable = 10, texture = 1 },
				bag = { drawable = 10, texture = 1 },
				shoes = { drawable = 10, texture = 1 },
				vest = { drawable = 10, texture = 1 },
				decal = { drawable = 10, texture = 1 },
				hat = { drawable = 10, texture = 1 },
				glass = { drawable = 10, texture = 1 },
				earing = { drawable = 10, texture = 1 },
				watch = { drawable = 10, texture = 1 },
				bracelet = { drawable = 10, texture = 1 },
			},
			female = {
				mask = { drawable = 1, texture = 1 },
				torso = { drawable = 1, texture = 1 },
				pant = { drawable = 1, texture = 1 },
				bag = { drawable = 1, texture = 1 },
				shoes = { drawable = 1, texture = 1 },
				tshirt = { drawable = 1, texture = 1 },
				vest = { drawable = 1, texture = 1 },
				decal = { drawable = 1, texture = 1 },
				hat = { drawable = 1, texture = 1 },
				glass = { drawable = 1, texture = 1 },
				earing = { drawable = 1, texture = 1 },
				watch = { drawable = 1, texture = 1 },
				bracelet = { drawable = 1, texture = 1 },
			}
		}
	},
	{
		label = 'Boss Outfit', --label of outfit for menuj
		ranks = 3,  -- number like 1 or table of numbers like  {1,2,3}
		uniform = {
			male = {
				torso = { drawable = 1, texture = 1 },
				pant = { drawable = 1, texture = 1 },
				tshirt = { drawable = 1, texture = 1 },
				mask = { drawable = 1, texture = 1 },
				bag = { drawable = 1, texture = 1 },
				--shoes = { drawable = 1, texture = 1 },
				--vest = { drawable = 1, texture = 1 },
				--decal = { drawable = 1, texture = 1 },
				--hat = { drawable = 1, texture = 1 },
				--glass = { drawable = 1, texture = 1 },
				--earing = { drawable = 1, texture = 1 },
				--watch = { drawable = 1, texture = 1 },
				--bracelet = { drawable = 1, texture = 1 },
			},
			female = {
				mask = { drawable = 1, texture = 1 },
				torso = { drawable = 1, texture = 1 },
				pant = { drawable = 1, texture = 1 },
				bag = { drawable = 1, texture = 1 },
				shoes = { drawable = 1, texture = 1 },
				tshirt = { drawable = 1, texture = 1 },
				vest = { drawable = 1, texture = 1 },
				decal = { drawable = 1, texture = 1 },
				hat = { drawable = 1, texture = 1 },
				glass = { drawable = 1, texture = 1 },
				earing = { drawable = 1, texture = 1 },
				watch = { drawable = 1, texture = 1 },
				bracelet = { drawable = 1, texture = 1 },
			}
		}
	},

}
```

{% endcode %}

### Config\_Delivery.lua

{% code fullWidth="true" %}

```lua
Config.delivery = {
    start = {
        coords = vec3(-826.4030, -798.6533, 19.8709),        -- this use for marker only or target check config_target.lua
        label = 'Delivery',
        get_delivery_call_timer = { min = 0, max = 0 },      -- time in seconds after which the phone will start rung for player near to phone
        phone_ringtone = 'https://youtu.be/9IEiziJ3JZ81212', -- u need xsound for this
    },
    details = {                                              -- don't change untill u know what ur doing
        ['ready'] = { Status = 'Ready', description = 'Waiting for order', icon = "fa-solid fa-signal" },
        ['inprogress'] = { Status = 'In Porgess', description = 'Player Delivering Order', icon = "fa-solid fa-truck" },
        ['offline'] = { Status = 'Offline', description = 'Phone is not used yet', icon = "fa-solid fa-phone-volume" },
    },
}

Config.DeliveryProgressbar = { dict = 'misscarsteal4@actor', clip = 'actor_berating_loop', time = 5000 }

Config.KeyBind_VehicleDoorLock = { -- script has its own vehicle doorlock feature
    enable = true,                 -- script buildin doorlock for vehicle
    key = 'U',
    range = 20.0,                  -- 20.0 meters range vehicle will intract with keybind
}

Config.garage = {
    menu_coords = {
        coords = vector4(-839.3102, -814.6177, 18.4227, 172.4324),
        ped = 'a_m_y_vindouche_01',
        access_distance = 2.0,
    },
    spawn_coords = vector4(-834.9464, -817.1415, 19.3905, 265.1719),
    vehicles = {
        offsets = {       -- use for marker
            ['taco2'] = { -- make sure it exists for food trucks models what ever ur using bottom
                ['sidebar'] = vector3(1.5, 1.0, 0.0),
                ['backdoors'] = vector3(0.0, -5.0, 0.0),
                ['stash'] = vector3(0.0, 0.100, 0.0),
                ['crafting'] = vector3(0.0, -2.5, 0.0),
            },

        },
        bones = {         -- use for target
            ['taco2'] = { -- make sure it exists for food trucks models what ever ur using bottom
                ['sidebar'] = { 'boot', 5 },
                ['backdoors'] = { 'seat_dside_r', 'door_pside_r', 'seat_pside_r', 2, 3 },
                ['stash'] = { 'overheat' }, -- this also  contain outfitmenu target in it
                ['crafting'] = { 'boot' },
            },

        },
        food_trucks = { -- each vehicle has its own unique stash and its presistent
            {
                label = 'Food Truck 1',
                spawn_name = 'taco2',
                plate = 'Taco 1',
                min_grade = 0,                      -- this grade and 2 to onward grades will able to access spawn vehicle
                livery = 1,
                stash = { slots = 50, weight = 20 } -- weight in KG

            },
            { -- each vehicle can be spawned once at a time and after spawn have to either put it back or wait for restart to spawn it again this is for makeing sure stash will stay for a vehicle
                label = 'Food Truck 2',
                spawn_name = 'taco2',
                plate = 'Taco 2',
                min_grade = 0,                      -- this grade and 2 to onward grades will able to access spawn vehicle
                livery = 1,
                stash = { slots = 50, weight = 10 } -- weight in KG
            },
            {                                       -- each vehicle can be spawned once at a time and after spawn have to either put it back or wait for restart to spawn it again this is for makeing sure stash will stay for a vehicle
                label = 'Food Truck 3',
                spawn_name = 'taco2',
                plate = 'Taco 3',
                min_grade = 0,                      -- this grade and 2 to onward grades will able to access spawn vehicle
                livery = 1,
                stash = { slots = 50, weight = 10 } -- weight in KG
            },
            {
                label = 'Food Truck 4',
                spawn_name = 'taco2',
                plate = 'Taco 4',
                min_grade = 0,                      -- this grade and 2 to onward grades will able to access spawn vehicle
                livery = 1,
                stash = { slots = 50, weight = 10 } -- weight in KG
            },

        },
        delivery_trucks = {

            { label = 'Delivery Van 1', spawn_name = 'tabac',    plate = 'TacoDel1', min_grade = 0, livery = 1 },
            { label = 'Delivery Van 2', spawn_name = 'tabac',    plate = 'TacoDel2', min_grade = 0, livery = 1 },
            { label = 'FS Food Bike 1', spawn_name = 'foodbike', plate = 'TacoDel3', min_grade = 0, livery = 1 },
            { label = 'FS Food Bike 2', spawn_name = 'foodbike', plate = 'TacoDel4', min_grade = 0, livery = 1 },
        }
    }

}

Config.DeliveryItems = { -- make sure here you can only write the items which exists in crafting
    { name = "fs_b_hamburger",                 price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_chicken_jr",                price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_texas_double_whopper",      price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_small_hash_browns",         price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_family_bundle_classic",     price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_chicken_fries",             price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_iced_tea",                  price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_chicken",                   price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_sprite",                    price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_cookie_shake",              price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_pink_lemonade",             price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_bacon_double_cheeseburger", price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_jalapeno_cheddar_bites",    price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_bacon_king",                price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_plain_iced_coffee",         price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_dr_pepper",                 price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_fruit_punch",               price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_double_cheeseburger",       price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_whopper_with_cheese",       price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_coca_cola",                 price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_vanilla_shake",             price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_soft_serve_cup",            price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_strawberry_shake",          price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_barqs_diet_beer",           price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_yello_mello",               price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_egg_normous_burrito",       price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_double_sausage_biscuit",    price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_sundae_pie",                price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_spicy_deluxe_sandwich",     price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_cafe_decaf",                price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_soft_serve_cone",           price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_chocolate_shake",           price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_big_fish",                  price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_sprite_zero",               price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_original_chicken_sandwich", price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_small_classic_fries",       price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_chocolate_cookie_shake",    price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_cheesy_tots",               price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_fanta_orange",              price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_pancake_sausage_platter",   price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_mozzarella_sticks",         price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_rodeo_burger",              price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_barqs_beer",                price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_diet_coke",                 price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
    { name = "fs_b_bacon_ham_sausage",         price = { min = 10, max = 20 }, quantity = { min = 1, max = 3 } },
}


Config.deliverypeds = {
    'a_m_m_afriamer_01',
    'u_m_m_aldinapoli',
    's_m_y_ammucity_01',
    's_m_m_ammucountry',
    'u_m_y_antonb',
    'csb_anton',
    'g_m_m_armboss_01',
    'g_m_m_armgoon_01',
    'g_m_y_armgoon_02',
    'g_m_m_armlieut_01',
    'ig_ashley',
    'cs_ashley',
    's_m_y_autopsy_01',
    's_m_m_autoshop_01',
    's_m_m_autoshop_02',
    'ig_money',
    'csb_money',
    'g_m_y_azteca_01',
    'u_m_y_babyd',
    'g_m_y_ballaeast_01',
    'g_m_y_ballaorig_01',
    'g_f_y_ballas_01',
    'ig_ballasog',
    'csb_ballasog',
    'g_m_y_ballasout_01',
    's_m_y_barman_01',
    's_f_y_bartender_01',
    'u_m_y_baygor',
    's_f_y_baywatch_01',
    's_m_y_baywatch_01',
    'a_f_m_beach_01',
    'a_f_y_beach_01',
    'a_m_m_beach_01',
    'a_m_o_beach_01',
    'a_m_y_beach_01',
    'a_m_m_beach_02',
    'a_m_y_beach_02',
    'a_m_y_beach_03',
    'a_m_y_beachvesp_01',
    'a_m_y_beachvesp_02',
    'ig_benny',
    'ig_beverly',
    'cs_beverly',
    'a_f_m_bevhills_01',
    'a_f_y_bevhills_01',
    'a_m_m_bevhills_01',
    'a_m_y_bevhills_01',
    'a_f_m_bevhills_02',
    'a_f_y_bevhills_02',
    'a_m_m_bevhills_02',
    'a_m_y_bevhills_02',
    'a_f_y_bevhills_03',
    'a_f_y_bevhills_04',
    'u_m_m_bikehire_01',
    'u_f_y_bikerchic',
    'a_m_y_breakdance_01',
    'u_m_y_burgerdrug_01',
    'csb_burgerdrug',
    's_m_y_busboy_01',
    'u_m_m_rivalpap',
    'a_m_y_roadcyc_01',
    's_m_y_robber_01',
    'ig_roccopelosi',
    'csb_roccopelosi',
    'a_f_y_runner_01',
    'a_m_y_runner_01',
    'a_m_y_runner_02',
    'a_f_y_rurmeth_01',
    'a_m_m_rurmeth_01',
    'ig_russiandrunk',
    'cs_russiandrunk',
    'a_f_m_salton_01',
    'a_f_o_salton_01',
    'a_m_m_salton_01',
    'a_m_o_salton_01',
    'a_m_y_salton_01',
    'a_m_m_salton_02',
    'a_m_m_salton_03',
    'a_m_m_salton_04',
    'g_m_y_salvaboss_01',
    'g_m_y_salvagoon_01',
    'g_m_y_salvagoon_02',
    'g_m_y_salvagoon_03',
    'a_m_y_vinewood_04',
}


Config.locations = {
    vec4(330.66, -2072.25, 19.05, 131.29),
    vec4(6.54, -705.56, 44.97, 192.69),
    vec4(105.73, -742.6, 44.75, 103.61),
    vec4(169.69, -567.41, 42.87, 82.13),
    vec4(236.33, -408.71, 46.92, 348.09),
    vec4(311.85, -202.71, 53.22, 236.48),
    vec4(-203.38, -43.88, 49.57, 181.01),
    vec4(-766.74, -23.18, 40.08, 206.03),
    vec4(-633.43, -126.15, 38.23, 80.67),
    vec4(-444.26, -358.28, 33.5, 164.78),
    vec4(-1075.52, -1027.14, 3.55, 299.76),
    vec4(-1127.9, -1081.3, 3.22, 121.72),
    vec4(-1253.36, -1140.85, 7.57, 279.53),
    vec4(-943.12, -1075.7, 1.75, 210.54),
    vec4(-1118.03, -1488.38, 3.73, 36.21),
    vec4(-1149.78, -1522.38, 9.63, 235.24),
    vec4(-1015.6, -1514.93, 5.51, 122.35),
    vec4(-970.15, -1431.46, 6.68, 128.09),
    vec4(-1528.03, -344.09, 44.39, 135.95),
    vec4(-1596.4, -352.43, 44.98, 228.1),
    vec4(-1790.15, -369.27, 44.11, 326.3),
    vec4(-1970.18, -501.86, 10.88, 310.11),
    vec4(-1918.21, -542.57, 10.83, 323.81),
    vec4(-1883.17, -578.75, 10.82, 323.81),
    vec4(-933.25, 694.81, 151.71, 0.03),
    vec4(-127.46, 590.37, 203.52, 0.03),
    vec4(-848.27, 104.41, 52.18, 92.33),
    vec4(-882.75, 21.04, 44.43, 152.23),
    vec4(-889.31, 7.63, 43.64, 359.65),
    vec4(-1097.4, -324.7, 36.82, 19.97),
    vec4(-660.92, -219.94, 36.73, 122.84),
    vec4(-262.66, -903.38, 31.31, 335.21),
    vec4(315.42, -1098.68, 28.4, 88.12),
    vec4(-167.53, -1534.98, 37.33, 146.34),
    vec4(-120.37, -1574.48, 36.41, 137.06),
    vec4(-13.45, -1442.35, 30.1, 160.4),
    vec4(128.28, -1855.98, 23.89, 132.97),
    vec4(113.08, -1959.08, 19.91, 30.09),
    vec4(-33.27, -1847.07, 25.19, 282.45),
    vec4(-129.2, -2183.72, 9.39, 52.74),
}
```

{% endcode %}

### Config\_target.lua

{% code fullWidth="true" %}

```lua
Config.targetsections = { -- use circle zone for qb and sphare zone for ox
    ['storage'] = {       --if no prop created for storage then this zone will work
        debug = false,
        label = 'Storage',
        icon = 'fa-solid fa-shop',
        coords = vec3(-812.8727, -802.9158, 20.1138),
        radius = 1.1,
        draw_distance = 5.0,
        access_distance = 1.5,
    },
    ['sellshop'] = { -- selling shop points
        [1] = {
            debug = false,
            label = 'Shop',
            icon = 'fa-solid fa-shop',
            coords = vec3(-827.9890, -799.0943, 20.0515 ),
            radius = 0.6,
            draw_distance = 5.0,
            access_distance = 1.5,
        },
        [2] = {
            debug = false,
            label = 'Open Shop',
            icon = 'fa-solid fa-shop',
            coords = vec3(-828.0204, -800.8701, 20.0515 ),
            radius = 0.6,
            draw_distance = 5.0,
            access_distance = 1.5,
        },
        [3] = {
            debug = false,
            label = 'Shop',
            icon = 'fa-solid fa-shop',
            coords = vec3(-827.9696, -804.7337, 20.0515 ),
            radius = 0.6,
            draw_distance = 5.0,
            access_distance = 1.5,
        },
         
         
        -- you can add more
    },
    ['shopmanagement'] = {
        debug = false,
        label = 'Management',
        icon = 'fa-solid fa-list-check',
        coords = vec3(-820.2355, -806.2944, 20.0),
        radius = 0.8,
        draw_distance = 5.0,
        access_distance = 1.5,
    },
    ['deliveries'] = {
        debug = false,
        label = 'Delivery',
        icon = 'fa-solid fa-truck',
        coords = vec3(-826.3655, -798.0455, 19.8),
        radius = 0.3,
        draw_distance = 5.0,
        access_distance = 1.5,
    },
    ['outfitroom'] = { -- not implemeneted yet
        debug = false,
        label = 'CloakRoom',
        icon = 'fa-solid fa-shirt',
        coords = vec3(-1379.3424, -911.7220, 0.5455),
        radius = 0.5,
        draw_distance = 5.0,
        access_distance = 1.5,
    },
    ['boss_action'] = {
        debug = false,
        label = 'Boss Menu',
        icon = "fa-solid fa-person",
        coords = vec3(-815.9052, -810.3477, 20.0),
        radius = 1.5,
        draw_distance = 5.0,
        access_distance = 1.5,
    },
    ['crafting'] = { -- crafting points
        crafting_menu = {
            debug = false,
            label = 'Crafting',
            icon = "fa-solid fa-utensils",
            coords = vec3(-821.1711, -802.2960, 20.1491),
            radius = 1.5,
            draw_distance = 5.0,
            access_distance = 1.5,
        },
        default_steps = { -- if any item not found in override_steps then this default_steps will work but if you add any item in override_steps then custom steps will work for that specific item
            {
                debug = false,
                coords = vector3(-818.1530, -802.0505, 20.0),
                radius = 0.7,
                draw_distance = 5.0,
                access_distance = 1.5,
                prog = { label = 'Preparing Order....', time = 10 }, -- time is in seconds
                anim = { scenario = 'prop_human_bbq'},
            },
            {
                debug = false,
                coords = vector3(-815.6114, -806.3712, 20.5),
                radius = 1.0,
                draw_distance = 5.0,
                access_distance = 1.5,
                prog = { label = 'Preparing Order....', time = 5 }, -- time is in seconds
                anim = { dict = 'random@shop_tattoo', clip = '_idle_a' },
            },
             
        },
        override_steps = {
            ['fs_b_barqs_diet_beer'] = {
                {
                    debug = false,
                    coords = vector3(-821.8554, -798.3240, 20.5),
                    radius = 1.0,
                    draw_distance = 5.0,
                    access_distance = 1.5,
                    prog = { label = 'Preparing Order....', time = 5 }, -- time is in seconds
                    anim = { dict = 'random@shop_tattoo', clip = '_idle_a' },
                },
            },
            ['fs_b_barqs_beer'] = {
                {
                    debug = false,
                    coords = vector3(-821.8554, -798.3240, 20.5),
                    radius = 1.0,
                    draw_distance = 5.0,
                    access_distance = 1.5,
                    prog = { label = 'Preparing Order....', time = 5 }, -- time is in seconds
                    anim = { dict = 'random@shop_tattoo', clip = '_idle_a' },
                },
            },
            ['fs_b_cafe_decaf'] = {
                {
                    debug = false,
                    coords = vector3(-821.8554, -798.3240, 20.5),
                    radius = 1.0,
                    draw_distance = 5.0,
                    access_distance = 1.5,
                    prog = { label = 'Preparing Order....', time = 5 }, -- time is in seconds
                    anim = { dict = 'random@shop_tattoo', clip = '_idle_a' },
                },
            },
            ['fs_b_coca_cola'] = {
                {
                    debug = false,
                    coords = vector3(-821.8554, -798.3240, 20.5),
                    radius = 1.0,
                    draw_distance = 5.0,
                    access_distance = 1.5,
                    prog = { label = 'Preparing Order....', time = 5 }, -- time is in seconds
                    anim = { dict = 'random@shop_tattoo', clip = '_idle_a' },
                },
            },
            ['fs_b_diet_coke'] = {
                {
                    debug = false,
                    coords = vector3(-821.8554, -798.3240, 20.5),
                    radius = 1.0,
                    draw_distance = 5.0,
                    access_distance = 1.5,
                    prog = { label = 'Preparing Order....', time = 5 }, -- time is in seconds
                    anim = { dict = 'random@shop_tattoo', clip = '_idle_a' },
                },
            },
            ['fs_b_dr_pepper'] = {
                {
                    debug = false,
                    coords = vector3(-821.8554, -798.3240, 20.5),
                    radius = 1.0,
                    draw_distance = 5.0,
                    access_distance = 1.5,
                    prog = { label = 'Preparing Order....', time = 5 }, -- time is in seconds
                    anim = { dict = 'random@shop_tattoo', clip = '_idle_a' },
                },
            },
            ['fs_b_fanta_orange'] = {
                {
                    debug = false,
                    coords = vector3(-821.8554, -798.3240, 20.5),
                    radius = 1.0,
                    draw_distance = 5.0,
                    access_distance = 1.5,
                    prog = { label = 'Preparing Order....', time = 5 }, -- time is in seconds
                    anim = { dict = 'random@shop_tattoo', clip = '_idle_a' },
                },
            },
            ['fs_b_fruit_punch'] = {
                {
                    debug = false,
                    coords = vector3(-821.8554, -798.3240, 20.5),
                    radius = 1.0,
                    draw_distance = 5.0,
                    access_distance = 1.5,
                    prog = { label = 'Preparing Order....', time = 5 }, -- time is in seconds
                    anim = { dict = 'random@shop_tattoo', clip = '_idle_a' },
                },
            },
            ['fs_b_iced_tea'] = {
                {
                    debug = false,
                    coords = vector3(-821.8554, -798.3240, 20.5),
                    radius = 1.0,
                    draw_distance = 5.0,
                    access_distance = 1.5,
                    prog = { label = 'Preparing Order....', time = 5 }, -- time is in seconds
                    anim = { dict = 'random@shop_tattoo', clip = '_idle_a' },
                },
            },
            ['fs_b_sprite'] = {
                {
                    debug = false,
                    coords = vector3(-821.8554, -798.3240, 20.5),
                    radius = 1.0,
                    draw_distance = 5.0,
                    access_distance = 1.5,
                    prog = { label = 'Preparing Order....', time = 5 }, -- time is in seconds
                    anim = { dict = 'random@shop_tattoo', clip = '_idle_a' },
                },
            },
            ['fs_b_yello_mello'] = {
                {
                    debug = false,
                    coords = vector3(-821.8554, -798.3240, 20.5),
                    radius = 1.0,
                    draw_distance = 5.0,
                    access_distance = 1.5,
                    prog = { label = 'Preparing Order....', time = 5 }, -- time is in seconds
                    anim = { dict = 'random@shop_tattoo', clip = '_idle_a' },
                },
            },
            ['fs_b_chocolate_cookie_shake'] = {
                {
                    debug = false,
                    coords = vector3(-821.8554, -798.3240, 20.5),
                    radius = 1.0,
                    draw_distance = 5.0,
                    access_distance = 1.5,
                    prog = { label = 'Preparing Order....', time = 5 }, -- time is in seconds
                    anim = { dict = 'random@shop_tattoo', clip = '_idle_a' },
                },
            },
            ['fs_b_chocolate_shake'] = {
                {
                    debug = false,
                    coords = vector3(-821.8554, -798.3240, 20.5),
                    radius = 1.0,
                    draw_distance = 5.0,
                    access_distance = 1.5,
                    prog = { label = 'Preparing Order....', time = 5 }, -- time is in seconds
                    anim = { dict = 'random@shop_tattoo', clip = '_idle_a' },
                },
            },
            ['fs_b_cookie_shake'] = {
                {
                    debug = false,
                    coords = vector3(-821.8554, -798.3240, 20.5),
                    radius = 1.0,
                    draw_distance = 5.0,
                    access_distance = 1.5,
                    prog = { label = 'Preparing Order....', time = 5 }, -- time is in seconds
                    anim = { dict = 'random@shop_tattoo', clip = '_idle_a' },
                },
            },
            ['fs_b_pink_lemonade'] = {
                {
                    debug = false,
                    coords = vector3(-821.8554, -798.3240, 20.5),
                    radius = 1.0,
                    draw_distance = 5.0,
                    access_distance = 1.5,
                    prog = { label = 'Preparing Order....', time = 5 }, -- time is in seconds
                    anim = { dict = 'random@shop_tattoo', clip = '_idle_a' },
                },
            },
            ['fs_b_plain_iced_coffee'] = {
                {
                    debug = false,
                    coords = vector3(-821.8554, -798.3240, 20.5),
                    radius = 1.0,
                    draw_distance = 5.0,
                    access_distance = 1.5,
                    prog = { label = 'Preparing Order....', time = 5 }, -- time is in seconds
                    anim = { dict = 'random@shop_tattoo', clip = '_idle_a' },
                },
            },
            ['fs_b_strawberry_shake'] = {
                {
                    debug = false,
                    coords = vector3(-821.8554, -798.3240, 20.5),
                    radius = 1.0,
                    draw_distance = 5.0,
                    access_distance = 1.5,
                    prog = { label = 'Preparing Order....', time = 5 }, -- time is in seconds
                    anim = { dict = 'random@shop_tattoo', clip = '_idle_a' },
                },
            },
            ['fs_b_vanilla_shake'] = {
                {
                    debug = false,
                    coords = vector3(-821.8554, -798.3240, 20.5),
                    radius = 1.0,
                    draw_distance = 5.0,
                    access_distance = 1.5,
                    prog = { label = 'Preparing Order....', time = 5 }, -- time is in seconds
                    anim = { dict = 'random@shop_tattoo', clip = '_idle_a' },
                },
            },
            
        },
    },
}
```

{% endcode %}
