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
# Item Whitelist

## <mark style="color:green;">Clothing Item Whitelist system:</mark>

### File Path:

<mark style="color:yellow;">fs\_clothingitem/preset/</mark>

{% code title="any preset file" lineNumbers="true" fullWidth="true" %}

```lua
-- One chain example you ca  do with any cloting item pant shirt etc any
chain_dogtag = {
            male = {
                main = {
                    chain_1 = 141, chain_2 = 0, -- item slot name and id. Check skinchanger/client/main.lua to get all slot names
                },
            },
            female = {
                main = {
                    chain_1 = 141, chain_2 = 0, -- item slot name and id. Check skinchanger/client/main.lua to get all slot names
                },
            },
            whitelist = { -- if you don't want whitelist please remove whole whitelist brackets or check docs
                jobs = {
                    ['police'] = 0,

					-- you can add more here
                },
                identifier = {
                    ['discord:628640109897711636'] = true,
		    ['char1:703b1abbb142ea1702d7c7b1c6f3510e913ab4ed'] = true,
					-- you can add more here
				}
			},
        },
```

{% endcode %}
