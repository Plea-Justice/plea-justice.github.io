---
layout: page
title: VueX Assets
permalink: /console/docs/vuex-assets
parent: Technical Documentation
grand_parent: Researcher Console
---

# Assets

## State

| Props           | Type               | Description                                               |
| --------------- | ------------------ | --------------------------------------------------------- |
| `assets`        | `Object`           | Holds data for each asset                                 |
| `assetList`     | `Array of Ids`     | Ordered list of `assets` `id`'s (manages order of assets) |
| `allAssetTypes` | `Array of Strings` | list of possible types an asset can be categorized by     |

### Asset

An individual asset object in `assets` is composed of the following properties

| Props      | Type      | Description                                |
| ---------- | --------- | ------------------------------------------ |
| `id`       | `String`  | Corresponding asset's id                   |
| `name`     | `String`  | Asset's name                               |
| `filename` | `String`  | The name corresponding to the asset's file |
| `type`     | `String`  | The asset's type it's categorized under    |
| `readOnly` | `Boolean` | If the file can not be modified            |
| `isMine`   | `Boolean` | If the current user owns the file          |
| `owner`    | `String`  | Users name that owns the file              |
| `public`   | `Boolean` | If the file is shared between users        |
| `created`  | `String`  | When the file was created                  |
| `modified` | `String`  | When the file was last modified            |

## Actions

| Props                 | Args                         | Description                                                         |
| --------------------- | ---------------------------- | ------------------------------------------------------------------- |
| `async getAssets()`   | `None`                       | fetches asset state from backend and manages adding it to the store |
| `async addAsset()`    | `asset`: asset object to add | manages adding a new asset to the state                             |
| `async removeAsset()` | `id`: id for asset to remove | manages removing an asset from the state                            |

## Mutations

| Props           | Args                              | Description                              |
| --------------- | --------------------------------- | ---------------------------------------- |
| `setAssets()`   | `res`: data returned from backend | replace state data with new              |
| `newAsset()`    | `asset`: asset object to add      | manages adding a new asset to the state  |
| `deleteAsset()` | `id`: id for asset to remove      | manages removing an asset from the state |
