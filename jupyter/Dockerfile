FROM jupyter/minimal-notebook

RUN pip install grpcio numpy pandas sentence-transformers ipywidgets torch torchvision Pillow img2vec_pytorch
RUN pip install git+https://github.com/RediSearch/redisearch-py.git@params
RUN wget -c https://amazon-berkeley-objects.s3.amazonaws.com/archives/abo-images-small.tar
RUN mkdir /home/jovyan/data
RUN tar -xf  abo-images-small.tar -C /home/jovyan/data/
