# Tile Package Specification

A tile package is a compressed file with ".tpkx" extension. It has a simplified structure, containing image tiles stored in Compact Cache V2 storage format and tiling scheme and other metadata stored in a JSON file. This storage format provides better performance to retrieve tiles when accessed over network file shares and cloud storage.
 
These tile package files are supported in ArcGIS Online, ArcGIS Desktop and ArcGIS Enterprise 10.7 or later, ArcGIS Pro 2.3 or later and applications built with ArcGIS Runtime SDK 100.5 or later for Android, Java, iOS, .NET, and Qt

_Note:_ Tile packages with ".tpk" extension, use compact storage V1 format for cache tiles. The spec for this package type is not available and use of tpkx is recommended.

## Folder structure
The folder structure with in the compressed Tile Package (.tpkx) is  illustrated below  in Figure 1. It consists of [iteminfo.json](docs/iteminfo.md), [root.json](docs/root.md), a thumbnail image and a folder named "tile" containing .bundle files, where tiles are stored in [Compact V2 storage format](https://github.com/Esri/raster-tiles-compactcache) for each level of detail. 
  
   ![Figure 1. Tpkx folder structure](TPKX.png)

### [iteminfo.json](docs/iteminfo.md)
The ItemInfo.json contains metadata to describe various properties needed to identify and preview the item without loading all the content.

### [root.json](docs/root.md)
It describes various properties needed to visualize the cache content and includes tiling scheme, tile image format, tile size, and layer information objects.

### thumbnail
A thumbnail 24-bit png, typically 200 pixels and 133 pixels.

### tile
The "tile" folder contains the cache tiles in ".bundle" format grouped inside folders representing each level of details of the cache tiling schema. The ".bundle" format uses [Compact Cache V2 storage format](https://github.com/Esri/raster-tiles-compactcache) for storing tiles. 

## Issues

Find a bug or want to request a new feature?  Please let us know by submitting an issue.

## Contributing

Esri welcomes contributions from anyone and everyone. Please see our [guidelines for contributing](https://github.com/esri/contributing).

## Licensing
Copyright 2016 Esri

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

A copy of the license is available in the repository's [license.txt]( https://raw.github.com/Esri/quickstart-map-js/master/license.txt) file.
