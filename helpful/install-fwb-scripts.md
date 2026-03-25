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
# Install FwB Scripts

## ESX/QB Installation

### Step 1

Its just drag and drop resources and make sure to keep all our `mlo` / `bridge` / every kind of script in the same folder so it works properly.

### Step 2

Make a folder in your resources folder with the name `[fs]`.

<figure><img src="https://1183961505-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FwD85x8fSbgbLtvzWMHv7%2Fuploads%2FlThsBFxxJLrjvexZHY8v%2Fimage.png?alt=media&#x26;token=e2cab21b-dc26-4925-a923-1a00d5f61163" alt=""><figcaption></figcaption></figure>

### Step 3

Then simply ensure `[fs]` in your `server.cfg` under the rest of your resources.

<figure><img src="https://1183961505-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FwD85x8fSbgbLtvzWMHv7%2Fuploads%2FhfzwIIiakqtrC04wauOQ%2Fimage%20(1).png?alt=media&#x26;token=b6ea87f2-cc04-47dd-a0b2-f5c6c4de1e41" alt=""><figcaption></figcaption></figure>

### Step 4

Make sure to add all scripts into that `[fs]` folder. You do not need to ensure every other script separately or in a different order. Just drag and drop them there, and the scripts will wait for Bridge to load properly.

Make sure you also install the latest version of `ox_lib`.