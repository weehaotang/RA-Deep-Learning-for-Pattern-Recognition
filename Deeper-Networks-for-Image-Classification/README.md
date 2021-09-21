<h1>Deeper-Networks-for-Image-Classification</h1>
Comparison of three deep neural nets (VGG, GoogLeNet and ResNet) for Image Classification task on MNIST and CIFAR-10 datasets. Publicly available implementation of each method has been used (https://pytorch.org/vision/stable/models.html) and amended to work with those two datasets.

<h2>Datasets</h2>
The MNIST database (examples on the left) is a dataset of handwritten digits with 60,000 training samples and 10,000 test samples of 28x28 greyscale images in 10 classes. The CIFAR-10 database (examples on the right) is a labelled dataset of 50,000 training samples and 10,000 test samples of 32x32 colour images in 10 classes.<br>
<table>
  <tr>
    <td><img  src="https://github.com/maciejtarsa/Deeper-Networks-for-Image-Classification/blob/main/Dataset%20examples/Fig1_MNIST_example.png"></td>
    <td><img  src="https://github.com/maciejtarsa/Deeper-Networks-for-Image-Classification/blob/main/Dataset%20examples/Fig2_CIFAR10_example.png"></td>
  </tr>
 </table>
<h2> Methodology </h2>
The experiments for this project have been conducted using a Google Colab platform with Nvidia Tesla P100 GPU with 16GB. The models were trained separately on the two different datasets. First, one variant of each model with different parameters has been trained on MNIST dataset. Then, one variant of VGG, GoogLeNet and multiple variants of ResNet have been trained on CIFAR-10 dataset using different parameters.
<br>
<h2>Results</h2>
<h3>MNIST</h3>
For training on MNIST, all models start with a relatively high accuracy. VGG-16 achieves an accuracy of 98.91% in the first iteration. ResNet-18 started with the worst accuracy of 97.49% and therefore improved the most, achieving top accuracy of 99.31% in iteration 20, indicating that further iterations could have led to an even higher accuracy. ResNet-18 is also the model that exhibited the steadiest performance, slightly improving at each iteration. The top accuracy has been achieved by GoogLeNet, with 99.64% at iteration 12.<br>
<p align="center">
  <img  src="https://github.com/maciejtarsa/Deeper-Networks-for-Image-Classification/blob/main/Visualiations/Fig4_MNIST_accuracies.png">
</p>
As the results for all three models were quite similar, I also looked at how long it took to train each of the models. As the training environment wasn’t consistent – in the cloud environment I wasn’t always allocated the same resources - I trained each model between 4 and 10 times and looked at average time per iteration. This confirmed that VGG-16 was much slower than the other two models, with average execution time per iteration of 4.9 minutes, while GoogLeNet’s average execution time per iteration was 1.8 minutes and ResNet-18’s 1.5 minutes per iteration<br><br>
Overall, ResNet-18 exhibited the most stable result while also showing potential to achieve the best accuracy. It was also the model whose average execution time was the shortest of out all models trained. The fact that all three models achieved such high accuracies so quickly may be due to MNIST being a fairly simple dataset. Literature confirms that much smaller and simpler models are capable of achieving very good accuracy on MNIST. 
<h3>CIFAR-10</h3>
All three models performed well on CIFAR-10 dataset. They all achieved validation accuracy of over 80%. VGG-16 started with the best accuracy, but improved the least, while GoogLeNet achieved the lowest accuracy to start with and therefore improved the most.<br>
<p align="center">
  <img  src="https://github.com/maciejtarsa/Deeper-Networks-for-Image-Classification/blob/main/Visualiations/Fig6_CIFAR19_Accuracies.png">
</p>
ResNet-18 was the best performing model with top accuracy of 85.98%, achieved in iteration 36. GoogLeNet achieved top accuracy of 84.38% in iteration 49 and VGG-16 top accuracy of 81.46% in iteration 36. Therefore, the three models showcase relatively similar performance.<br>
Furthermore, as with MNIST, the speed of each model was different. ResNet-18 was again the fastest, taking 127 minutes to complete 50 iterations, while GoogLeNet took 132 minutes and VGG-16 took 474 minutes.<br>
<h3>CIFAR-10 Further evaluation</h3>
The accuracy of the model is based on the class with the highest percentage confidence, but the literature often reports the results as top-1 and top-5 accuracies. Figures below shows examples of correctly classified (left) and misclassified (right) objects. For correctly classified, the model is very confident about both (99.71% and 97.23% confidence). For misclassified, in the first example the model classified a picture of a bird as a ship with 38.22% confidence, with correct label in fourth place with only 0.88% confidence. In the second example, the picture was classified as a bird with 70.67% confidence, while the correct class (airplane) was third with 4.38% confidence. Potentially, looking at top-5 or even top-3 accuracies would give the model a near perfect accuracy.
<table>
  <tr>
    <td><img  src="https://github.com/maciejtarsa/Deeper-Networks-for-Image-Classification/blob/main/Visualiations/Fig12_predictions_correct/Screenshot%202021-05-06%20at%2014.49.25.png"></td>
    <td><img  src="https://github.com/maciejtarsa/Deeper-Networks-for-Image-Classification/blob/main/Visualiations/Fig13_predictions_wrong/Screenshot%202021-05-06%20at%2015.03.09.png"></td>
  </tr>
 </table>
