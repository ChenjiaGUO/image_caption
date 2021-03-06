# Image Caption

## Description
Image caption referes to the process of describing an image using a sentence. By asking computers to generate captions based on input image, we may find ways to improve life quality for those with visual impairment. In addition, with image caption we could also build and optimize the search engine for image content. <br><br>

For our final project for DL Summer '22, we build and use a CNN-RNN model to automatically generate descriptions.<br>

> CNN-RNN model: The image is encoded into a context vector by a CNN which can then be passed to a RNN decoder [^1]
![This is an image](https://miro.medium.com/max/1400/0*Z0KrVxXpDqTacrsF.)
Here, we use the resnet18 model for our CNN encoder part. <br>
[^1]: [Image reference](https://blog.mlreview.com/multi-modal-methods-image-captioning-from-translation-to-attention-895b6444256e)
## Data
We used the [Flickr Image dataset](https://www.kaggle.com/datasets/srbhshinde/flickr8k-sau) from Kaggle, with a total of 8k images and corresponding human annotated captions.
## Model and Notebook
We followed these steps to create our final model: <br>
1. Tokenizing the captions. We used spacy here.
2. Image Augmentation
3. Processed Image as input for CNN (Resnet-18)
4. CNN -> LSTM
5. Use output from LSTM to generate result captions<br>

Link to the notebook [here](https://github.com/ChenjiaGUO/image_caption/blob/main/DL_Final.ipynb).
Link to the [helper](https://github.com/ChenjiaGUO/image_caption/blob/main/helper.py) functions and [model](https://github.com/ChenjiaGUO/image_caption/blob/main/model.py) files.
## Result
<img width="415" alt="result" src="https://user-images.githubusercontent.com/86633319/176597505-51d736b5-db9e-48c7-a112-710e64f5d18f.png"> <br>
> Average Log Loss: 3.3332 after a few epochs
## Summary
### Issues
- Model can only use words in the vocab it trains on
- Loss function only penalize for getting the words wrong. There is no meaning retention
- Can not work with grammar
- Need more epochs (Research groups norally take days to train their models)
### Future Steps
- Increase LSTM layering
- Add in attention
- Use subwords tokenizers
- Train for more epochs
- Use different loss function, for example BLEU, or embedding comparisons
## Discussions
Some other implementions using captions could be:<br>
- Given a sentence/query, find out the matching images.
- Object detection
## Slides
Our [Slides](https://github.com/ChenjiaGUO/image_caption/blob/main/DL-Final%20presentation.pdf) for the final presentation

## Requirements
Python==3.7.13  
jupyter==1.0.0  
matplotlib==3.2.2  
numpy==1.21.6  
pandas==1.3.5  
Pillow==7.1.2  
spacy==3.3.1  
torch @ https://download.pytorch.org/whl/cu113/torch-1.11.0%2Bcu113-cp37-cp37m-linux_x86_64.whl  
torchaudio @ https://download.pytorch.org/whl/cu113/torchaudio-0.11.0%2Bcu113-cp37-cp37m-  
tqdm==4.64.0  
