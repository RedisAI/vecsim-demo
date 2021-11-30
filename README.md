# Pre-Requisites
* Install [Git LFS](https://git-lfs.github.com/).
    * Make sure you initialize LFS by runing
    ```
    git lfs install
    ```
* Docker


# Semantic Search and Visual Similarity Demo

This demo goes along with the [Annoucement of a New Redis Vector Similarity Search](https://redis.com/blog/build-intelligent-apps-redis-vector-similarity-search/)

In this demo, you will experiment with 2 key applications of Vector Similarity Search that are commonly found in modern e-commerce applications
* Semantic Search : You will be able to search products given a text description of a product
* Visual Search: You will be able to find products that are "visually" similar to a given image

## Start the demo
Clone this repo
```
git clone https://github.com/RedisAI/vecsim-demo.git
```

Start docker-compose. Note, This will download a 3GB data set and will take around 10-15 minutes, depending on your network connection.

```
cd vecsim-demo
docker-compose up
```

Once the docker compose finishes open a web browser on the following address (or just click on the link from the docker-compose logs)
```
localhost:8888
```

# Semantic Search 
It's time to upload vector representation of product text fields.
You will use a pre-trained Natural Language Processing (NLP) model from Hugging Face


Open the `TextEmbeddings.ipynb` notebook illustrating how to generate vectors for the "item_keywords" field

The source code for the notebook is here["Generate Embeddings for item keyword data in 1,000 products"](TextEmbeddings.ipynb). 

And here's the [same exercise with 100K products](100kTextEmbeddings.ipynb). 
This time, You will be using previously generated vectors for 100k products in the Amazon dataset.

# Visual Search

Using a similar approach, you can generate vector representation of product image data!

This time, you will be using a pre-trained Vision models from torchvision wrapped by the Img2Vec python library

Open the `VisualSearch1k.ipynb` notebook and you will find the step-by-step instructions

# About the Amazon Product data
The dataset used in this demo was derived from the ["Amazon Berkeley Objects Dataset"](https://amazon-berkeley-objects.s3.amazonaws.com/index.html)

In particular, each long text field in the product_data.csv was extracted from the original JSON encoded object representing each product. 

Thanks to Amazon.com for sharing the original dataset. This includes all product data, images and 3D models under the [Creative Commons Attribution-NonCommercial 4.0 International Public License (CC BY-NC 4.0)](https://creativecommons.org/licenses/by-nc/4.0/)

Credit to the creators of the dataset: 
Matthieu Guillaumin Amazon.com 
Thomas Dideriksen Amazon.com 
Kenan Deng Amazon.com 
Himanshu Arora Amazon.com 
Arnab Dhua Amazon.com 
Xi (Brian) Zhang Amazon.com 
Tomas Yago-Vicente Amazon.com 
Jasmine Collins UC Berkeley 
Shubham Goel UC Berkeley 
Jitendra Malik UC Berkeley
