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
# Integrations

## <mark style="color:green;">Server Side: {QBCORE Only}</mark>

### Unlocked File Path:

<mark style="color:yellow;">fs\_clothingitem/server/unlocked.lua</mark>

<pre class="language-lua" data-title="unlocked.lua" data-line-numbers data-full-width="false"><code class="lang-lua"><strong>-- you can change ur banking system functions too
</strong><strong>function addSocietyMoney(job, money)
</strong>    exports['qb-banking']:AddMoney(job,tonumber(money),'Business Transctions')
end

function getSocietyMoney(job)
    return exports['qb-banking']:GetAccountBalance(job)
end

function removeSocietyMoney(job, money)
    exports['qb-banking']:RemoveMoney(job,tonumber(money),'Business Transctions')
end
</code></pre>
