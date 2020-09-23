# DATA AUGMENTATION


This Session played with various Data Augumentation techniques.**Albumentation** library was introduced. Finally Gradcam was introduced.

**Gradient-weighted Class Activation Mapping** (GradCAM) uses the gradients of any target concept (say logits for 'dog' or even a caption), flowing into the final convolutional layer to produce a coarse localization map highlighting the important regions in the image for predicting the concept

## Target
* Apply Transformation using Albumentation Library.
* Implement GradCam.
* Target Accuracy is 87%.

## Implementation
* To apply transformations dataset visualisation is important. So wrote a code to see how the differnt class , different images looks like.
* **Train Transformations used**
   * Horizontal Flip
   * Rotate((-30.0, 30.0))
   * RGBShift(r_shift_limit=50, g_shift_limit=50, b_shift_limit=50, p=0.5)
   * Normalize(mean=channel_means, std=channel_stdevs)
   * Cutout(num_holes=1, max_h_size=16,max_w_size = 16,p=1)
   * To Tensor
* **Test Transformation used**
   * Normalise
   * To Tensor
* **Code for misclassified images is also written**

  ![misclassified](Assets/misclassify.png)

* Implemented GradCam with the help of ['https://github.com/vickyliin/gradcam_plus_plus-pytorch/tree/master/gradcam'] Code and modified   the code to show the activations of all the 4 layers.

  ![Gradcam](Assets/GradCam.png)
  
## Numbers 
* Architecture Used - Resnet18
* No of Epochs - 40
* Highest Validation Accuracy - **88.73%**
* L2 (weight decay) - 0.0005
* LR - StepLr- step_size(12)
* Dropout - 0.1

![validationgraph](Assets/Test_Loss_and_Acc.png)

**In GradCam the transformations used are from torchVision, Since Albumentation was throwing error for resize and it was not conveting to 4 Channels**
