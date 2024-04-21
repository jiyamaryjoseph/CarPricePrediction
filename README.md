# OnHEncoding-CarPrice /House price prediction
Here I am using onehotencoding method  for the prediction of used cars and House price prediction.
# Types-of-Loss-function

### ‘Loss’ helps us to understand how much the predicted value differ from actual value
###  Function used to calculate the loss is called as “Loss function”
#### cost function and loss function are synonymous and used interchangeably but they are “different”. A loss function/error function is for a single training example/input. A cost function, on the other hand, is the average loss over the entire training dataset.
### The optimization strategies aim at “minimizing the cost function”.


 ##### Regression Loss Function
 ###### Regression Loss is used when we are predicting continuous values like the price of a house or sales of a company. 
1.   Mean Squared Error: 
        It is the mean of squared differences between the actual and predicted value. If the difference is large the model will penalize it as we are computing the squared difference.
   adv: 1. This is in the form of qudratic equation.(when we plot quadratic eqution we get gradient descend with only globalminima.we dnot get any localminima.)
        2. MSE loss penalizes the model for making large error by squring them.
   disadv: 1.This loss not robust to outliers.
2.  Mean Squared Logarithmic Error Loss:
        Suppose we want to reduce the difference between the actual and predicted variable we can take the natural logarithm of the predicted variable then take the mean squared error. This will overcome the problem possessed by the Mean Square Error Method. The model will now penalize less in comparison to the earlier method.

3.   Mean Absolute Error Loss:
        Sometimes there may be some data points which far away from rest of the points i.e outliers, in case of cases Mean Absolute Error Loss will be appropriate to use as it calculates the average of the absolute difference between the actual and predicted values.
   adv. 1. MAE is robust to outliers as compaired to MSE.
   disadv.1.computation is very difficult.bz we are using mode of operand.(I I)
          2.It may have local minima.
  
4.    Huber Loss:
        This is the combination of  Mean Squared Error and Mean Absolute Error Loss.
        
##### Binary Classification Loss Function
###### Suppose we are dealing with a Yes/No situation like “a person has diabetes or not”, in this kind of scenario Binary Classification Loss Function is used.

1.   Binary Cross Entropy Loss:
         It gives the probability value between 0 and 1 for a classification task. Cross-Entropy calculates the average difference between the predicted and actual probabilities.i.e. loss=-ylogy-(1-y)log(1-y).
         -ylog(1-y) if y=0;
         -(1-y)log(1-y) if y=1.
         ('y_predict' is depends on sigmoid function.)
         
##### Multi-Class Classification Loss Function
###### If we take a dataset like Iris where we need to predict the three-class labels: Setosa, Versicolor and Virginia, in such cases where the target variable has more than two classes Multi-Class Classification Loss function is used.
   

1.    Cross Entropy:is the default loss function to use for multi-class classification problems.

In this case, it is intended for use with multi-class classification where the target values are in the set {0, 1, 3, …, n}, where each class is assigned a unique integer value.

Mathematically, it is the preferred loss function under the inference framework of maximum likelihood. It is the loss function to be evaluated first and only changed if you have a good reason.

Cross-entropy will calculate a score that summarizes the average difference between the actual and predicted probability distributions for all classes in the problem. The score is minimized and a perfect cross-entropy value is 0.Cross-entropy can be specified as the loss function in Keras by specifying ‘categorical_crossentropy‘ when compiling the model.The function requires that the output layer is configured with an n nodes (one for each class), in this case three nodes, and a ‘softmax‘ activation in order to predict the probability for each class.
                
                
                model.add(Dense(3, activation='softmax')
 
This is to ensure that each example has an expected probability of 1.0 for the actual class value and an expected probability of 0.0 for all other class values. This can be achieved using the to_categorical() Keras function.
                  
                  # one hot encode output variable
                  y = to_categorical(y)
For example, three class labels will be integer encoded as 0, 1, and 2. Then encoded to vectors as follows:

Class 0: [1, 0, 0]
Class 1: [0, 1, 0]
Class 2: [0, 0, 1]
This is called a one-hot encoding.

----------------------------------------------------------------------------------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------------------------------------------------------------------------------\
#### Available losses
Note that all losses are available both via a class handle and via a function handle. The class handles enable you to pass configuration arguments to the constructor (e.g. loss_fn = CategoricalCrossentropy(from_logits=True)), and they perform reduction by default when used in a standalone way (see details below).
##### Probabilistic losses
- BinaryCrossentropy class......> for binary output

- CategoricalCrossentropy class........>here internly doing one hot encodng for classificatioon output like iris,rating ....>output like{.22,.31,.68}and which is having high probability will take as its output

- SparseCategoricalCrossentropy class---------->here we will get out maximum probabilty index{0,1,2}i.e y_predict=2
Poisson class

- binary_crossentropy function
- categorical_crossentropy function
- sparse_categorical_crossentropy function
- poisson function
- KLDivergence class
- kl_divergence function

##### Regression losses
- MeanSquaredError class
- MeanAbsoluteError class
- MeanAbsolutePercentageError class
- MeanSquaredLogarithmicError class
- CosineSimilarity class
- mean_squared_error function
- mean_absolute_error function
- mean_absolute_percentage_error function
- mean_squared_logarithmic_error function
- cosine_similarity function
- Huber class
- huber function
- LogCosh class
- log_cosh function

#### losses are diffrent for regression problem as well as classification problem 
