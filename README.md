Demonstrative bundle showing how one might implement a crafting system.

## Usage

Recipes are defined in 'data/recipes.json' like so:

```js
[
  {
    // the item this recipe will generate
    "item": "limbo:potionhealth1",
    // recipe defines the resources needed and their amounts
    "recipe": {
      "plant_material": 3,
      "rose_petal": 1
    }
  }
]
```

Resources for recipes are defined next to recipes in `data/resources.json`

```js
{
  "plant_material": {
    "title": "Plant Material",
    "quality": "common"
  },
  "rose_petal": {
    "title": "Rose Petal",
    "quality": "uncommon"
  }
}
```

For a player to get resources you create an item for them to use the `gather` command on:

```yaml
- id: greenplant
  name: "Green Plant"
  type: RESOURCE
  roomDesc: "Green Plant"
  keywords: [ "green", "plant", "resource" ]
  metadata:
    noPickup: true
  behaviors:
    # configures if and what happens when this resource is gathered
    resource:
      # flavor message displayed to the user after gathering
      depletedMessage: "withers, having been stripped of usable materials."
      # which materials you get and their rannge. `gather` will pick a random
      # amount from this range
      materials:
        plant_material:
          min: 1
          max: 3
```
