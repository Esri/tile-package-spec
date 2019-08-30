# root.json

It describes various properties needed to visualize the cache content and includes tiling scheme, tile image format, tile size, and layer information objects.  

| Element | Description |
| --- | --- |
| name | The name of the tile package |
| version | The version of specification which the tile package follows. Current version is 1.0 |
| serviceDescription | A detailed description about the service and the data associated with it |
| tileBundlesPath | Path to the location/directory where cache tiles are located. |
| minLOD | The minimum level of detail at which the cache tiles are available in the tile package tiling scheme. The minLOD should always be lesser than the maxLOD |
| maxLOD | The maximum level of detail at which the cache tiles are available in the tile package tiling scheme. The maxLOD should always be greater than the minLOD |
| minScale | The minimum scale (most zoomed out) at which the tiles should be visible. A value of 0 means the layer does not have a minimum scale. The minScale value should always be greater than the maxScale value |
| maxScale | The maximum scale (most zoomed in) at which the tiles should be visible.  A value of 0 means the layer does not have a maximum scale. The maxScale value should always be lesser than the minScale value |
| resampling | *true/false* Boolean value indicating whether the tiles should be resampled when the tiles at a given level of detail are missing. When true, clients can resample the tiles avaialble at nearest level of detail|
| initialExtent | Default initial extent for displaying the tiles |
| fullExtent | Full extent of the tiles |
| tileInfo | Object that describes the tiling scheme |
| storageInfo | Object that describes the storage format and and other bundle related properties |
| tileImageInfo |Object that describes properties of the image format |
| layers (optional) | An array of layer objects describing the properties like styling that are used to render the tiles along with their legends |
| spatialReference | Object that describes the coordinate system of the tiles |

## spatialReference
A object describing the coordinate system and other spatial properties for the tiles. A spatial reference can be defined using a well-known ID (WKID) or well-known text (WKT). The default tolerance and resolution values for the associated coordinate system are used.

| Element | Description |
| --- | --- |
| wkid | The well-known ID (WKID) of the coordinate system |
| LatestWkid | (Optional) Identifies the current wkid value associated with the same spatial reference. For example a WKID of '102100' (Web Mercator) has a latestWKid of '3857' |

## tileInfo
An object describing the properties of the tiles.

| Element | Description |
| --- | --- |
| row | Tile width in pixels. The default tile width and height is *256* pixels. It's recommended that you use 256 or 512. If you're building a cache that will overlay another cache, be sure to use the same tile width and height for both caches. Choosing a smaller tile width and height may improve performance of the application requesting tiles from the cache, as smaller tile size/ data will need to be transferred, but it will also increase the number of tiles needed to draw an extent |
| cols | Tile height in pixels. The default tile width and height is *256* pixels. Should be same as Tile width |
| dpi | Dots per inch (DPI) refers to the resolution of the cache tiles that were created. The default value of *96 * which is almost always sufficient unless you are working primarily on a network where the majority of client machines have a different DPI. Note: adjusting the DPI affects the scale of the tiles |
| origin | The tiling scheme origin is the upper left corner of the tiling scheme grid. The origin does not necessarily represent the point at which tiles begin to be created; that happens when the full extent of the map or area of interest feature class is reached. Using a common tiling scheme origin for your caches ensures that they can overlay each other in web apps.  If no coordinate reference is defined in the map document, the upper left of the two times the maximum of the union of extents of all the layers in the map is used |
| spatialReference | An object used to specify the spatial reference |
| lods |An array of objects each describing the level of detail level |

### lod
An object describing properties of level of detail.

| Element | Description |
| --- | --- |
| level | Numeric value assigned to the resolution of the cache tiles. The value 0 is assigned to the coarsest resolution of the cache tiling scheme |
| resolution | Resolution provides the accurate conversion between a pixel location and map coordinates. The Resolution value should agree with the dpi and the scale, which are advisory only and might not provide full accuracy. The dpi value may be used to scale the cache tiles to the actual screen resolution to ensure readability of labels and other features |

## tileImageInfo
An object describing properties of the image format for the tiles.

| Element | Description |
| --- | --- |
| format | *PNG/PNG8/PNG24/PNG32/JPEG/MIXED* This setting determines the image format used for the tiles. The image format is important while creating the cache tiles because it determines the size on disk of the tiles, the image quality, and the ability to make the tile background transparent |
| compression | *0* for PNG/LERC, *0-100* for JPEG. Compression refers to the amount of JPEG compression that was used when tiles were created using JPEG or mixed image format. Higher values signify higher JPEG quality and therefore less compression. For imagery, values of 55 to 75 are usually sufficient without causing any visible loss of quality. For vectors and other sharply defined features or regions, a higher quality of 90 is recommended as a starting point |

## storageInfo
An object that describes the storage information of the tiles. 

| Element | Description |
| --- | --- |
| storageformat | *esriMapCacheStorageModeCompactV2* This value is fixed and represents the storage format supported by tile package (tpkx). Its specification is available [here](https://github.com/Esri/raster-tiles-compactcache). Tile packages with ".tpk" extension, use compact v1 storage format for cache tiles. The spec for this package type is not available 
| packetsize | *128* The number of tiles stored in a bundle. 128 indicates each bundle covers 128 by 128 tiles.

## layer 
An object describes a layer that is rendered in the tiles including the legend and other information clients can use to show in the table of contents.

| Element | Description |
| --- | --- |
| id | A string indicating the index position of the layer in the map service or feature collection |
| name | The name of the layer |
| parentLayerId | Layer id of the parent that contains this layer |
| defaultvisibility | Indicates whether the layer is visibile |
| subLayerIds | If the layer is a parent layer, it will have one or more sub layers included in an array |
| minScale | The minimum scale (most zoomed out) at which the layer is visible when rendered in the tiles |
| maxScale | The maximum scale (most zoomed in) at which the layer is visible when rendered in the tiles |
| legend (optional) | An object that  describes legend for the layer. |

### legend 
Each layer's legend information includes the symbol images and labels for each symbol. 
The legend symbols include the base64 encoded imageData as well as a url that could be used to retrieve the image from the server.

| Element | Description |
| --- | --- |
| label | Optional descriptive text that describes a legend|
| imageData | base64EncodedImageData |
| contentType | The content type as image types. Example: (image/png, image/jpeg) |
| height | Height of the legend item |
| width | Width of the legend tem |


