# iteminfo.json

The iteminfo.json contains metadata to describe various properties needed to identify and preview the item without loading all the content.

| Element | Description |
| --- | --- |
| name | The name of the tile package. This should be the same as the name defined in root.json |
| guid | The unique ID for this item |
| version | The version of specification which the tile package follows. Current version is 1.0 |
| created | Date when the item was created, shown in UNIX time in milliseconds |
| snippet | A short summary description of the item |
| description | Item description |
| summary | Summary of package |
| title | The title of the item. This is the name that's displayed to users and by which they refer to the item |
| tags | An array of user defined tags that describe the item |
| type | *Compact Tile Package*|
| typekeywords |  An array of keywords that further describes the type of this item. Each item is tagged with a set of type keywords that are derived based on its primary type. For a Compact Tile Package this must contain the following:*"Compact Tile Package", "Tile Package", "tpkx"* in addition to any other type keywords.|
| thumbnail | The URL to the thumbnail used for the item |
| extent | An array that defines the bounding rectangle of the item |
| spatialreference | The coordinate system of the item |
