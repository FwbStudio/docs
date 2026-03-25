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
# Exports (Optional)

## Exports for Runtime Blacklisting Vehicle Plates

this is optional and for dev to blacklist vehicles from spawners of police etc so that people not be able to chop shop pd or ems spawned vehicles or admin vehicles&#x20;

{% tabs %}
{% tab title="Client Side" %}
&#x20;\
->  exports\['fs\_chopshop']:addplateblacklist(plate)\
\
\--for example if in case u have vehicle in you can get plate like this\
\
\- exports\['fs\_chopshop']:addplateblacklist(GetVehiclePlateType(vehicle))
{% endtab %}

{% tab title="Server Side" %}
&#x20;\
->  exports\['fs\_chopshop']:addplateblacklist(plate)\
\
\--for example if in case u have vehicle in you can get plate like this\
\
\- exports\['fs\_chopshop']:addplateblacklist(GetVehiclePlateType(vehicle))
{% endtab %}
{% endtabs %}
