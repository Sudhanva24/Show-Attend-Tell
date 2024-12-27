# Show-Attend-Tell

This Project is inspired from the Research paper Show, Attend and Tell written which applies Attention Mechanism to Image captioning task. To know more about this research paper and the concept of hard attention and soft attention check out my blog 
in the link given below


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


 ![image](https://github.com/user-attachments/assets/e4b5bb9b-6f86-442c-990e-62d811ed410d)
 

 ![image](https://github.com/user-attachments/assets/2b2e2493-08bf-4133-b418-cfc17127eef3)

## Result:
Bleu score on Test data: 0.05
- Reason for low Bleu score: Low computation resources and we are only using 5600 examples to train

## Demo

**Example 1:**

![image](https://github.com/user-attachments/assets/4bf63ab2-0359-41f8-a096-4a8063e6c319)
![image](https://github.com/user-attachments/assets/c17935de-6364-4768-b3d4-7f0a49782da2)


**Example 2:**

![image](https://github.com/user-attachments/assets/dfcf4098-a0f0-4452-848a-b52fb811620b)
![image](https://github.com/user-attachments/assets/f02c2227-ec26-412e-8a1b-0c7465a5c30c)



**Example 3:**

![image](https://github.com/user-attachments/assets/eccb26ff-9791-4b9d-b7c7-19fe8b10c4c9)
![image](https://github.com/user-attachments/assets/40952fcc-0903-4828-afe2-f4249a3bc2ad)





**Example 4:**

![image](https://github.com/user-attachments/assets/eef52491-5267-48a7-9729-cc47dc88648f)
![image](https://github.com/user-attachments/assets/373e7bd9-21a4-4b41-a103-c76ec96406b1)





 


