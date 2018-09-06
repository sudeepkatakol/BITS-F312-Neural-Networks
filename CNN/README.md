### FAQs

**What should be the architecture of my ConvNet?**

Gain inspirations from different types of architectures which people have designed. Read on architectures like Inception Net, ResNet, etc. Take a note of the number of parameters used by these networks. Understand the reasons expressed by the authors for choosing a particular design.

Architectures: https://www.youtube.com/watch?v=DAOcjicFr1Y

**How to choose filter size?**

Use small filters. 3 * 3 (majorly) or 5 * 5 (sometimes). You can have the receptive field of  7 * 7 filter by using two layers of 3 * 3 filters.

Advantages: No. of parameters is reduced. Increased non linearity. 

**How to choose the number of filters?**

Increase the number of channels (in powers of 2) as the depth of your ConvNet increases. 

As the depth increases, the layers capture more and more complex information. You'd want filters to capture myriad of class specific features in the deeper layers(Cat face, Dog face, Cat tail, Dog Tail etc.) But in the earlier layers you'd want it to capture only general things like Edges and curves.

**How do I understand what my ConvNet is doing?** 

Visualize: Plot images of your filters and the intermediate outputs. 

**How do I not overfit my ConvNet?**

1) Regularization: Use Dropout layers. 
2) Plot validation loss and validation accuracy. 

**What non-linearity should I use?**

Don't use sigmoids. Use ReLUs and/or Leaky-ReLUs.

**What optimizer should I use?**

Adam with default setting works most of the times.

**Tips for training:** 

Resize your images to a common height and width. Normalise your images to [-1, 1]. {image = 2 * (np.cast(image, np.float32)/255.) - 0.5)} 

Initially (for a couple of epochs), use smaller batch sizes (like 4, 8 or 16). You have noisy and inaccurate estimates of gradients but they have enough information to get you near the vicinity of minimum. 

Then use higher batch sizes (64, 128, ..). You now have better gradient estimates and your gradient update rule will help you move closer to the minimum.

For the first couple of epochs, try different initializations and check which does better. Choose the best. Then for the next few epochs you can try different learning rates. Later, you can optimize your other hyperparameters (like dropout rate). This way of training is called babysitting.

Always save and test your model after a few epochs.
