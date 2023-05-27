# ResNet
Convolutional Neural Network is a type of deep learning algorithm majorly used for analyzing visual data images and audio. The model I have built here is on ResNet (Residual Neural Network) a type of CNN architecture used to support large number of convolutional layers.

Why ResNet?
While training a neural network we generally use backpropagation to compute the gradient at each layer. the gradients are computed by propagating the error from the output layer back to the input layer. Each layer in the network contributes to the gradients by multiplying the gradients from the subsequent layers with the weights of the connections.

The gradients are multiplied in each layer and if the gradients are less than 1 they tend to shrink exponentially with each added layer and eventually they become very close to zero or VANISH. This results in the network failing to update the parameters effectively and learn to find meaningful representations in data and so the training and test error rates increase drastically.

On the other hand if the gradients are greater than 1 they again tend to grow exponentially become extremely large and eventually EXPLODE. This unstable the entire network, causes the training process to diverge and result in poor performance.

This entire problem is known as Vanishing/Exploding Gradient.
ResNet model helps us to overcome this problem by introducing skip connections or residual connections. 

ResNet addresses this issue by introducing residual connections that bypass one or more layers. ResNet allows the network to learn the residual mappings, which bridges the difference between the desired mapping and the input.

Mathematically, a residual connection involves adding the input of a layer to its output. 
So output  = input + residual
By adding the input to the output, the residual connection ensures that the gradients can flow directly from the output back to the input without significant attenuation which was the case in traditional CNN. 

These residual connections effectively create shortcut paths that allow the gradient to propagate through the network more directly. As a result, the gradients can flow more smoothly during backpropagation, reducing the chances of vanishing or exploding gradients.

ResNet architectures  typically stack residual blocks(as the name suggest), which consist of multiple layers, together to form a deep network. Each residual block contains one or more convolutional layers, batch normalization, and activation functions, along with the skip connections.

This skip connections is the reason why  ResNet have been found to be particularly effective in training very deep neural networks with hundreds or even thousands of layers.

I tried my model with ResnetVersion 1 and ResnetVersion 2. The difference is in the depth and the way they handle computation. While Resnet version 1 have depth in range 6n + 2 where n are the number or residual blocks. Resnet 2 have depth in 9n + 2.
Further in Resnet 1 we apply batchnormlization and activation function first and then we convolve in Version 2 we first convolve and then apply the functions.
We can vary the depths in both the models as per the will and check for better accuracies
In both the models we get decent accuracy with Version1 around: 


Although ResNet have found to be an extremely powerful and effective CNN model it also has a few drawbacks.
1.	Increased computational complexity: ResNet's skip connections introduce additional connections and computations compared to traditional neural networks. This can result in increased computational requirements, both in terms of memory and processing and could take a lot of time for the algorithm to run. (The model I built itself takes around 15 minutes to run)
2.	Design complexity: ResNet architectures can become quite complex due to the presence of residual connections and multiple layers. Designing and fine-tuning ResNet models may require lot of time and a lot of hyperparameter tuning.

3.	Interpretability: Due to the deep and complex nature of ResNet architectures, interpreting the learned representations and understanding the decision-making process of the model can be challenging. The high number of layers and non-linear transformations make it harder to interpret the inner workings of the network compared to other convolution architectures.
In certain complex and large cases the gradient might become extremely small and then ResNet alone would not be enough as it could result in overfitting and we would need additional adaptive gradient algorithms like gradient algorithms for efficiency.
But overall ResNet is one of the most preferred CNN model when working with large complex data.

Feel free to drop any comments if you have or even if you feel I was wrong or missed something would be more than happy to learn.
       
![image](https://github.com/harshil017/ResNet/assets/71325396/90fe651f-175a-4981-8e71-8b431f1fd629)
