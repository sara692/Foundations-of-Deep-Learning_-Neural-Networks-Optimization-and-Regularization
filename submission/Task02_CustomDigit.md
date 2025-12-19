# Task 2 — Custom Image Generalization Test

Create a handwritten digit using a drawing tool and load it into the model. After preprocessing (grayscale conversion, resizing to 28×28, and normalization), run the prediction and analyze the results.

### Questions and Analysis

**Did the model correctly classify the digit?**  
Yes.

**If not, why?**  
N/A for this example. In general, misclassification could occur due to **distribution shift**, **noise**, or **lack of data augmentation** during training.

**How does this relate to representation learning in neural networks?**  
The model learned to recognize patterns in the MNIST dataset, including **edges, shapes, and relative positions** of digits. It uses this learned representation to **map a new input image to the corresponding class**, demonstrating the network's ability to generalize beyond the training examples.

