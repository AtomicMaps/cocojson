# COCOJSON Extension Specification

- **Title:** COCOJSON
- **Identifier:** <https://stac-extensions.github.io/cocojson/v1.0.0/schema.json>
- **Field Name Prefix:** coco
- **Scope:** Item
- **Extension [Maturity Classification](https://github.com/radiantearth/stac-spec/tree/master/extensions/README.md#extension-maturity):** Proposal
- **Owner**: @jamesfisher-geo

This document explains the COCOJSON Extension to the [SpatioTemporal Asset Catalog](https://github.com/radiantearth/stac-spec) (STAC) specification.

The COCOJSON format (Common Objects in Context JSON) is a standardized format used to represent object annotations along with metadata including 
segmentations masks, pixel bounding boxes, and annotation categories commonly used in computer vision. This extension integrates the standarized 
COCOJSON fields into the STAC Item spec, enabling a practitioner to embed COCOJSON annotations within STAC Items.

- Examples:
  - [Item example](examples/item.json): Shows the basic usage of the extension in a STAC Item
  - [Collection example](examples/collection.json): Shows the basic usage of the extension in a STAC Collection
- [JSON Schema](json-schema/schema.json)
- [Changelog](./CHANGELOG.md)

## Fields

The fields in the table below can be used in these parts of STAC documents:

- [ ] Catalogs
- [ ] Collections
- [x] Item Properties (incl. Summaries in Collections)
- [ ] Assets (for both Collections and Items, incl. Item Asset Definitions in Collections)
- [ ] Links

| Field Name           | Type                      | Description                                  |
| -------------------- | ------------------------- | -------------------------------------------- |
| coco:licenses     | \[[License Object](#license-object)\]         | **REQUIRED**. Describe the required field... |
| coco:categories         | \[[Category Object](#category-object)\] | Describe the field...                        |
| coco:annotations | \[[Annotation Object](#annotation-object)\]    | Describe the field...                        |

### Additional Field Information

#### template:new_field

This is a much more detailed description of the field `template:new_field`...

### License Object

This is the introduction for the purpose and the content of the XYZ Object...

| Field Name | Type   | Description                                  |
| ---------- | ------ | -------------------------------------------- |
| `id`          | number | **REQUIRED**. Integer ID of the license |
| `name`          | string | **REQUIRED**. License name |
| `url`          | string | **REQUIRED**. URL to the license text |

### Category Object

This is the introduction for the purpose and the content of the XYZ Object...

| Field Name | Type   | Description                                  |
| ---------- | ------ | -------------------------------------------- |
| `id`          | number | **REQUIRED**. Integer ID of the category |
| `name`          | string | **REQUIRED**. Name of the category (e.g. 'cat') |
| `supercategory`          | string | **REQUIRED**. General category (e.g. 'animal') |
<!-- | `keypoints`          | /[string/] | List of names which keypoint coordinates represent |
| `skeleton`          | /[/[number, number/]/] | **REQUIRED**. Describe the required field... | -->

### Annotation Object

This is the introduction for the purpose and the content of the XYZ Object...

| Field Name | Type   | Description                                  |
| ---------- | ------ | -------------------------------------------- |
| `id `         | number | **REQUIRED**. Integer ID of the annotation |
| `image_id`          | number | **REQUIRED**. Integer ID of the associated images from the 'coco:images' field |
| `category_id`          | number | **REQUIRED**. Integer ID of the associated category from the 'coco:categories' field |
| `bbox`          | /[number/] | **REQUIRED**. Bounding box of the annotation in pixel coordinates |
| `segmentation`          | /[/[number, number/]/] | Segmentation mask of the annotation as a list of image coordinates |
| `area`          | number | The area of the segmentation mask in pixels |
| `iscrowd`          | bool | Tag indicating if the segmentation mask is of a single object or many objects in an image |
| `score`          | number | Score 0 - 1.0 indicating the annotation confidence level |



## Contributing

All contributions are subject to the
[STAC Specification Code of Conduct](https://github.com/radiantearth/stac-spec/blob/master/CODE_OF_CONDUCT.md).
For contributions, please follow the
[STAC specification contributing guide](https://github.com/radiantearth/stac-spec/blob/master/CONTRIBUTING.md) Instructions
for running tests are copied here for convenience.

### Running tests

The same checks that run as checks on PR's are part of the repository and can be run locally to verify that changes are valid. 
To run tests locally, you'll need `npm`, which is a standard part of any [node.js installation](https://nodejs.org/en/download/).

First you'll need to install everything with npm once. Just navigate to the root of this repository and on 
your command line run:
```bash
npm install
```

Then to check markdown formatting and test the examples against the JSON schema, you can run:
```bash
npm test
```

This will spit out the same texts that you see online, and you can then go and fix your markdown or examples.

If the tests reveal formatting problems with the examples, you can fix them with:
```bash
npm run format-examples
```
