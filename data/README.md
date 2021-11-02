# Amazon Berkeley Objects (c) by Amazon.com

## License

This work is licensed under the Creative Commons Attribution-NonCommercial 4.0
International Public License. To obtain a copy of the full license, see
`LICENSE-CC-BY-NC-4.0.txt`, visit
[CreativeCommons.org](https://creativecommons.org/licenses/by-nc/4.0/)
or send a letter to Creative Commons, PO Box 1866, Mountain View, CA 94042, USA.

Under the following terms:

  * Attribution — You must give appropriate credit, provide a link to the
    license, and indicate if changes were made. You may do so in any reasonable
    manner, but not in any way that suggests the licensor endorses you or your
    use.

  * NonCommercial — You may not use the material for commercial purposes.

  * No additional restrictions — You may not apply legal terms or technological
    measures that legally restrict others from doing anything the license
    permits.
    
## Attribution

Credit for the data, including all images and 3d models, must be given to:

> Amazon.com

Credit for building the dataset, archives and benchmark sets must be given to:

> Matthieu Guillaumin (Amazon.com), Thomas Dideriksen (Amazon.com),
> Kenan Deng (Amazon.com), Himanshu Arora (Amazon.com),
> Jasmine Collins (UC Berkeley) and Jitendra Malik (UC Berkeley)

## Description

Amazon Berkeley Objects is a collection of 147,702 product listings with
multilingual metadata and 398,212 unique catalog images. 8,222 listings come
with turntable photography (also referred as *spin* or *360º-View* images), as
sequences of 24 or 72 images, for a total of 586,584 images in 8,209 unique
sequences. For 7,953 products, the collection also provides high-quality 3d
models, as glTF 2.0 files.

The collection is made of the following files:

  * `README.md` - The present file.

  * `LICENSE-CC-BY-NC-4.0.txt` - The License file. You must read, agree and
    comply to the License before using the Amazon Berkeley Objects data.

  * `listings/metadata/listings_<i>.json.gz` - Product description and metadata.
    Each of the 16 files is encoded with UTF-8 and gzip-compressed. Each line of
    the decompressed files corresponds to one product as a JSON object (see
    http://ndjson.org/ or https://jsonlines.org/ ). Each product JSON object
    (a.k.a dictionary) has any number of the following keys:
    
    - `brand`
        - Content: Brand name
        - Format: `[{ "language_tag": <str>, "value": <str> }, ...]`
    - `bullet_point`
        - Content: Important features of the products
        - Format: `[{ "language_tag": <str>, "value": <str> }, ...]`
    - `color`
        - Content: Color of the product as text
        - Format: `[{"language_tag": <str>, "standardized_values": [<str>],
          "value": <str>}, ...]`
    - `color_code`
        - Content: Color of the product as HTML color code
        - Format: `[<str>, ...]`
    - `country`
        - Content: Country of the marketplace, as an
          [ISO 3166-1 alpha 2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2)
          code
        - Format: `<str>`
    - `domain_name`
        - Content: Domain name of the marketplace where the product is found.
          A product listing in this collection is uniquely identified by
          (`item_id`, `domain_name`)
        - Format: `<str>`
    - `fabric_type`
        - Content: Description of product fabric
        - Format: `[{ "language_tag": <str>, "value": <str> }, ...]`
    - `finish_type`
        - Content: Description of product finish
        - Format: `[{ "language_tag": <str>, "value": <str> }, ...]`
    - `item_dimensions`
        - Content: Dimensions of the product (height, width, length)
        - Format: `{"height": {"normalized_value": {"unit": <str>, "value":
          <float>}, "unit": <str>, "value": <float>}, "length":
          {"normalized_value": {"unit": <str>, "value": <float>}, "unit": <str>,
          "value": <float>}, "width": {"normalized_value": {"unit": <str>,
          "value": <float>}, "unit": <str>, "value": <float>}}}`
    - `item_id`
        - Content: The product reference id. A product listing in this
          collection is uniquely identified by (`item_id`, `domain_name`).
          A corresponding product page may exist at
          `https://www.<domain_name>/dp/<item_id>`
        - Format: `<str>`
    - `item_keywords`
        - Content: Keywords for the product
        - Format: `[{ "language_tag": <str>, "value": <str> }, ...]`
    - `item_name`
        - Content: The product name
        - Format: `[{ "language_tag": <str>, "value": <str> }, ...]`
    - `item_shape`
        - Content: Description of the product shape
        - Format: `[{ "language_tag": <str>, "value": <str> }, ...]`
    - `item_weight`
        - Content: The product weight
        - Format: `[{"normalized_value": {"unit": <str>, "value": <float>},
          "unit": <str>, "value": <float>}, ...]`
    - `main_image_id`
        - Content: The main product image, provided as an `image_id`. See the
          descripton of `images/metadata/images.csv.gz` below
        - Format: `<str>`
    - `marketplace`
        - Content: Retail website name (Amazon, AmazonFresh, AmazonGo, ...)
        - Format: `<str>`
    - `material`
        - Content: Description of the product material
        - Format: `[{ "language_tag": <str>, "value": <str> }, ...]`
    - `model_name`
        - Content: Model name
        - Format: `[{ "language_tag": <str>, "value": <str> }, ...]`
    - `model_number`
        - Content: Model number
        - Format: `[{ "language_tag": <str>, "value": <str> }, ...]`
    - `model_year`
        - Content: Model year
        - Format: `[{ "language_tag": <str>, "value": <int> }, ...]`
    - `node`
        - Content: Location of the product in the category tree. A node page
          may exist at `https://www.<domain_name>/b/?node=<node_id>` for
          browsing
        - Format: `[{ "node_id": <int>, "path": <str>}, ...]`
    - `other_image_id`
        - Content: Other available images for the product, provided as
          `image_id`. See the description of `images/metadata/images.csv.gz`
          below
        - Format: `[<str>, ...]`
    - `pattern`
        - Content: Product pattern
        - Format: `[{ "language_tag": <str>, "value": <int> }, ...]`
    - `product_description`
        - Content: Product description as HTML 
        - Format: `[{ "language_tag": <str>, "value": <int> }, ...]`
    - `product_type`
        - Content: Product type (category)
        - Format: `<str>`
    - `spin_id`
        - Content: Reference to the 360º View image sequence. See the
          description of `spins/metadata/spins.csv.gz` below
        - Format: `<str>`
    - `style`
        - Content: Style of the product
        - Format: `[{ "language_tag": <str>, "value": <int> }, ...]`
    - `3dmodel_id`
        - Content: Reference to the 3d model of the product. See the description
          of `3dmodels/metadata/3models.csv.gz`
        - Format: `<str>`

  * `images/metadata/images.csv.gz` - Image metadata. This file is a
    gzip-compressed comma-separated value (CSV) file with the following
    columns: `image_id`, `height`, `width`, and `path`.
    - `image_id` (string): this id uniquely refers to a product image. This id
      can be used to retrieve the image data from Amazon's Content Delivery
      Network (CDN) using the template:
      `https://m.media-amazon.com/image/I/<image_id>.<extension>` [^1],
      where `<extension>` is composed of the characters following the dot in the
      `path` field. Any value occurring in the `main_image` and `other_images`
      attributes of product metadata is an `image_id` present in this file.
    - `height` (int) and `width` (int): respectively, the height and width of
      the original image.
    - `path`: the location of the image file relative to the `images/original/`
      or `images/small/` directories. A path is composed of lowercase hex
      characters (`0-9a-f`) that also uniquely identifies images. The first two
      characters are used to build a file hierarchy and reduce the number of
      images in a single directory. The extension is `jpg` except for few `png`
      files.
    
    Below are are first 10 lines of `images/metadata/images.csv.gz`:
```
image_id,height,width,path
010-mllS7JL,106,106,14/14fe8812.jpg
01dkn0Gyx0L,122,122,da/daab0cad.jpg
01sUPg0387L,111,111,d2/d2daaae9.jpg
1168jc-5r1L,186,186,3a/3a4e88e6.jpg
11RUV5Fs65L,30,500,d9/d91ab9cf.jpg
11X4pFHqYOL,35,500,20/20098c4d.jpg
11Y+Xpt1lfL,103,196,99/9987a1c8.jpg
11rL64ZLPYL,64,500,89/89a2ff4d.jpg
11xjmNF5TAL,117,88,ee/ee239f0f.jpg
```
      
  * `images/original/<path>` - Original image data. This directory contains the
     original high-resolution version of the images. See
     `images/metadata/images.csv.gz` for details of image naming.

  * `images/small/<path>` - Downscaled image data. This directory contains the
     version of the images, where they have been downscaled such that their
     largest axis (height or width) is a maximum of 256 pixels. See
     `images/metadata/images.csv.gz` for details of image naming.

  * `spins/metadata/spins.csv.gz` - Spin / 360º-View image metadata. This file
    is a gzip-compressed comma-separated value (CSV) file with the following
    fields: `spin_id`, `azimuth`, `image_id`, `height`, `width`, and `path`.
    - `spin_id`: a unique identifier for the image sequence.
    - `azimuth`: an integer between 0 and 71, representing the index in the spin
      sequence and the azimuth of the camera (in steps of 5º).
    - `image_id`: this id uniquely refers to an image. This is can be used
      to retrieve the image data using the template:
            `https://m.media-amazon.com/image/I/<image_id>.jpg` [^1].
    - `height` and `width`: respectively, the height and width of the image.
    - `path`: the location of the image file relative to the `spins/original/`
      directory. The extension is `jpg` for all the images. The `path` is build
      from the `spin_id` and `azimuth` using the template
      `<spin_id>_<azimuth:02d>.jpg` and the first two characters of `spin_id`
      are used to build a file hierarchy and reduce the number of files in a
      single directory.

    Below are are first 10 lines of `spins/metadata/spins.csv.gz`:
```
spin_id,azimuth,image_id,height,width,path
61c91265,0,41wqHws7a6L,248,1075,61/61c91265/61c91265_00.jpg
61c91265,1,41++eZZHP9L,248,1075,61/61c91265/61c91265_01.jpg
61c91265,2,41YF86LhGDL,248,1075,61/61c91265/61c91265_02.jpg
61c91265,3,41I5Zz-kbAL,248,1075,61/61c91265/61c91265_03.jpg
61c91265,4,41lAQM2Ys5L,248,1075,61/61c91265/61c91265_04.jpg
61c91265,5,41OJT+p8JgL,248,1075,61/61c91265/61c91265_05.jpg
61c91265,6,412kYqOnqHL,248,1075,61/61c91265/61c91265_06.jpg
61c91265,7,41rgUZ0NuFL,248,1075,61/61c91265/61c91265_07.jpg
61c91265,8,41PJ4ks-cWL,248,1075,61/61c91265/61c91265_08.jpg
```

  * `spins/original/<path>` - Spin / 360º-View image files. Each file
    corresponds to one row in `spins/metadata/spins.csv.gz`, named by the value
    of the `path` column.

  * `3dmodels/metadata/3dmodels.csv.gz` - 3d model metadata. This file is a
    gzip-compressed comma-separated value (CSV) file with the following fields:
    `3dmodel_id`, `path`, `meshes`, `materials`, `textures`, `images`, 
    `image_height_max`, `image_height_min`, `image_width_max`,
    `image_width_min`, `vertices`, `faces`, `extent_x`, `extent_y`, `extent_z`.

    - `3dmodel_id`: Reference for the 3d model, as provided in the `3dmodel_id`
      field of the listings metadata
    - `path`: Location of the 3d model, relative to `3dmodels/original/`
    - `meshes`: Number of meshes in the geometry
    - `materials`: Number of materials in the 3d model
    - `textures`: Number of textures in the 3d model
    - `images`: Number of image resources in the 3d model
    - `image_{heigh,width}_{min,max}`: Minimal and maximal dimensions of the
      image resources in the 3d model
    - `vertices`: Number of vertices in the geometry
    - `faces`: Number of faces in the geometry
    - `extent_{x,y,z}`: Extent of the geometry in each dimension
    
    Below are are first 10 lines of `3dmodels/metadata/3dmodels.csv.gz`:
```
3dmodel_id,path,meshes,materials,textures,images,image_height_max,image_height_min,image_width_max,image_width_min,vertices,faces,extent_x,extent_y,extent_z
B01N2PLWIL,L/B01N2PLWIL.glb,1,1,3,3,4096,4096,4096,4096,10990,14380,0.571499943733216,0.11684001048680606,0.07111982014177629
B075QFCHM9,9/B075QFCHM9.glb,1,1,3,3,2048,2048,2048,2048,11973,19568,1.840071976184845,1.0669103860855103,2.3675915002822876
B07H469871,1/B07H469871.glb,1,1,3,3,4096,4096,4096,4096,1602,1950,1.1113524436950684,1.3880813121795654,0.39794909954071045
B07H8V49M2,2/B07H8V49M2.glb,1,1,3,3,4096,4096,4096,4096,3760,5710,1.4998703368605968,2.11988401412964,0.5897879977087402
B07DBHPK4G,G/B07DBHPK4G.glb,1,1,3,3,4096,4096,4096,4096,13704,22736,0.37921489775180817,1.6228150129318237,0.37921497225761414
B0842LM2DN,N/B0842LM2DN.glb,1,1,3,3,4096,4096,4096,4096,4078,7584,0.22779017686843872,0.2348586767911911,0.22779015451669693
B07HK6B4D7,7/B07HK6B4D7.glb,1,1,4,4,2048,2048,2048,2048,12221,19268,0.1887289583683014,0.6650936603546143,0.421692430973053
B07B4FZN9H,H/B07B4FZN9H.glb,1,1,3,3,2048,2048,2048,2048,13595,22644,3.3838289976119995,0.9963648915290833,2.048073887825012
B07B4Z9BS4,4/B07B4Z9BS4.glb,1,1,4,4,2048,2048,2048,2048,9259,16178,0.2793540060520172,0.2693932056427002,0.2793540358543396
```

  * `3dmodels/original/<path>` - 3d model files. The 3d models are provided in
    the [glTF-2.0 format](
    https://github.com/KhronosGroup/glTF/blob/master/specification/2.0/README.md
    ) (GLB/binary representation). All models adhere to the following
    conventions:
    1. Positive `Y` direction is up.
    2. Positive `Z` direction is pointing to the *natural* front-side of the
       product, wherever applicable.
    3. Products that are designed to stand on a surface (i.e. a floor) are
       centered on the origin, but translated up (towards positive `Y`) such
       that they *stand* on the `Y=0` plane.
    4. Products that are designed to hang from a surface (i.e. a ceiling) are
       centered on the origin, but translated down (towards negative `Y`) such
       that they *hang* from the `Y=0` plane.
    5. Products that are designed to hang on a wall are centered on the origin,
       but translated forward (towards positive `Z`) such that their backside
       aligns with the `Z=0` plane.

  * `archives/abo-listings.tar` - Contains all the files in `listings/` as a
    tar archive.

  * `archives/abo-images-original.tar` - Contains the metadata and original
    images from `images/original/` as a tar archive.

  * `archives/abo-images-small.tar` - Contains the metadata and downscaled
    images from `images/small/` as a tar archive.

  * `archives/abo-spins.tar` - Contains the metadata and images from `spins/`
    as a tar archive.
       
  * `archives/abo-3dmodels.tar` - Contains the metadata and images from `3dmodels/`
    as a tar archive.

## Footnotes

[^1]: Importantly, there is no guarantee that those URLs will remain unchanged
and available on the long term, we thus recommend using the images provided in this
archive instead.
