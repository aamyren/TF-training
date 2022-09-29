# TF-training
#### Amy Ren ####
## TF-training ##
Some sample code I wrote while learning TensorFlow, mostly working with MNIST Dataset. Explanation of the guidelines below:

### Neural Network Forward Propogation: ###
Using Python, construct a class without importing any modules given the following guidelines:
- create a dense layer given input, weight, and bias tensors 
- recommended to make a layer class that takes in input, weight, bias, and have a forward()method to run the forward propagation algorithm

### Multi-Digit MNIST/ Multi-Digit MNIST with Shift: ###
Use a similar neural network as for single digit classification and see if it will work on images of two (or more) digits from MNIST:
- Create a function that combines two randomimages from the MNIST dataset into a single (28, 56) image along with a new label of the two-digitnumber (e.g. 05, 27, 99), then scales the image to a (28, 28).
- To expand on this task, try to randomly apply an augmentation where the digits are shiftedleft/up/right/down by several pixels on your test data only, and compare the results to the non-augmentated runs.

### Strided MNIST: ###
Create a strided classifier that can detect 28x28 handwritten digits on a larger image. 
- Run your classifier on 28x28 crops of the larger image, strided every (Sy, Sx) pixels.
- Since original model’s predictions will be based on a softmax probability distribution, it will always predict a digit, whether or not there is actually one present. To remedy this, create a second network that takes in the same input shape and predicts 2 classes: if a cropped patch is a "background" or a "digit". If a patch is a "background" then you may ignore the prediction from the digit classifier.
- This secondary network will also need to be trained. Using the real MNIST images, create some "negative" examples where the images are either completely blank or are severely cropped MNIST digits
- Create an evaluation dataset for this by generating images larger than 28x28 (e.g. 40x40), and randomly positioning a 28x28 MNIST image somewhere in that 40x40 where the entire digit fits within the boundaries. 
- Alternatively, you may use a premade datasetsuch as affNIST (https://www.cs.toronto.edu/~tijmen/affNIST/).
- To visually check if this is the right position, draw a 28x28 bounding box on the larger image, then save or show the resulting image.
- You may usecv2.rectangle() to draw the rectangle.
- If everything above works perfectly, expand the evaluation dataset by using larger images (e.g.256x256) with multiple MNIST digits then evaluate again. Your strided classifier would work onthis dataset without any changes.
