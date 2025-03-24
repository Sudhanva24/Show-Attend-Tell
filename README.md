# Show-Attend-Tell

This Project is inspired from the Research paper Show, Attend and Tell written which applies Attention Mechanism to Image captioning task. To know more about this research paper and the concept of hard attention and soft attention check out my blog 
in the link given below

https://medium.com/@sudhanvaiitr/show-attend-and-tell-c0c7dc5467ed

## Data Set
- We have used the Flickr8k dataset.
- 5600 images were part of the training data
- 1200 validation and 1200 as test data
- Mini batch gradient descent of size 32 was used

## Framework and Resources
1. Python
2. Pytorch
3. 2x T4 GPU in Kaggle Notebook

## Model

<img width="467" alt="Screenshot 2024-12-27 at 8 58 56 PM" src="https://github.com/user-attachments/assets/bd24b043-dfdc-41a6-b6a1-715ef1ee55e6" />

### Encoder

- Oxford VGGnet was used as an encoder
- Features were extracted from the 4th layers to obtain 196 feature vectors each of dimension 512

### Decoder

- LSTM was used as the decoder
- It used the previous hidden, cell state and concatenation of embedding of the caption and the context vector.
- The context vector is calculated using the weighted sum of region vectors obtained from the encoder
- The weights are obtained by passing the previous hidden state and the region vectors via a fully connected neural network to obtain scores which are then softmaxed to obtain weights umming to 1.
- The inital hidden and cell state are initialized by passing the average of the region vectors across 2 different fully connected layer


## Hyperparameters

-Epochs: 10
- Embed_size=256
- Attention_dim=256
- Encoder_dim=512
- Decoder_dim=512
- Learning_rate = 3e-4

## Optimizer and Loss Function

- Adam optimizer
- Cross Entropy Loss

## Training Summary


 ![image](https://github.com/user-attachments/assets/61c2c92d-ded6-48cd-808f-a2f24d064aea)

 
 ![image](https://github.com/user-attachments/assets/b22b9077-b80d-42f3-8e21-c6415157e98f)


## Result:
Meteor on Test data: 0.223
- A decent Score considering we ran it for 10 epochs and trained it only for 5600 samples

## Demo

**Example 1:**

![image](https://github.com/user-attachments/assets/8bc9c690-1d9f-4aa2-ad76-6e095e0f4a87)

![image](https://github.com/user-attachments/assets/a09fe2a7-ce65-4d0e-b1db-56dcee10c603)



**Example 2:**

![image](https://github.com/user-attachments/assets/f85d853b-37bf-439f-bf50-19dda7ab73e4)

![image](https://github.com/user-attachments/assets/5890641b-f8b3-4448-8831-7d7f0234b882)




**Example 3:**

![image](https://github.com/user-attachments/assets/ffdaf72e-a3f3-44c7-b8e2-11cb18f6d747)

![image](https://github.com/user-attachments/assets/6b89c6fe-b7ec-466a-94cb-329c93794624)









 


