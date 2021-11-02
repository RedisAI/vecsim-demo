# Pre-Requisites
* Docker
* A Conda installation 
    * [Install Anacoda or Miniconda](https://conda.io/projects/conda/en/latest/user-guide/install/index.html)
* 3GB available in your HD


# Semantic Search and Visual Similarity Demo

In this demo, you will experiment with 2 key applications of Vector Similarity Search that are commonly found in modern e-commerce applications
* Semantic Search : You will be able to search products given a text description of a product
* Visual Search: You will be able to find products that are "visually" similar to a given image


## Redis Container with Vector Similarity

Before you start, make sure you have Docker.

Clone this repo
```
git clone https://github.com/RedisAI/vecsim-demo.git
cd vecsim-demo
```
Open 2 Terminal sessions

On the 1st Terminal session, fire up a container with Redis VecSim.
Run the following commands
```
docker pull redislabs/redisearch:feature-vecsim
docker run -it --rm -p 6379:6379 redislabs/redisearch:feature-vecsim
```
Leave that container running

## Jupyter Notebook Set Up
Go back to your 2nd Terminal session and set up your notebook environment.


You will need to set up a python 3.8 virtual environment

I will use Conda but you are free to use any tool of your choice to install a few dependencies

```
conda create --name vsim python=3.8 pip grpcio jupyterlab nb_conda numpy pandas sentence-transformers ipywidgets pytorch torchvision Pillow -c conda-forge
```
Activate your new environment
```
conda activate vsim
```
Then pip install redis-search(private-preview version) & img2vec within your new environment
```
pip3 install git+https://github.com/RediSearch/redisearch-py.git@params
pip3 install img2vec_pytorch
```
# Semantic Search 
It's time to upload vector representation of product text fields.
You will use a pre-trained Natural Language Processing (NLP) model from Huggingface


Now open a notebook illustrating how to generate vectors for the "item_keywords" field
```
jupyter lab TextEmbeddings.ipynb
```

The source code for the notebook is here["Generate Embeddings for item keyword data in 1000 products"](TextEmbeddings.ipynb). 

And here's the [same exercise with 100K products](100kTextEmbeddings.ipynb). 
This time, You will be using previously generated vectors for 100k products in the Amazon dataset.

# Visual Search

Download and uncompress the product images.
```
wget -c https://amazon-berkeley-objects.s3.amazonaws.com/archives/abo-images-small.tar
tar -xzf  abo-images-small.tar -C data/
```



Using a similar approach, you can generate vector representation of product image data!
This time, you will be using a pre-trained Vision models from torchvision wrapped by the Img2Vec python library

Here's a Notebook with step-by-step instructions

```
jupyter lab VisualSearch1k.ipynb
```




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
