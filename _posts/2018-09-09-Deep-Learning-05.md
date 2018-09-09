---
layout: post
title: "Deep Learning Concept 5: channel"
---

In each one of the convolutional layer, there are input and output images. Each images will have $$W \times H$$ 2D size and a third dimension called channel. What does channel mean here?

In the simple case, we have the initial input image as RGB image. Then there are naturally 3 channels: red, green and blue. In this case, for each input image channel, you have to have a corresponding filter channel to convolve on, so the number of filter channel needs to be the same as the number of image channel. The result of this convolution is a 2D image with size of (n - f + 1) assuming strides as 1 and no padding. 
What decides output image channel? The number of filter you use. Each filter will create one output channel and you can stack all filters outputs together to generate the output volume.  

In summary, given input $$n \times n \times n_{c}$$, we use this kind of filters $$f \times f\ times n_{c}$$. The result will be $$(n-f+1) \times (n-f+1) \times n_{c}^{\prime}$$. The output channel number depend not on the input channel number, but on the number of filter we use. In the pytorch package, you can define the input channel and output channel directly in the API
```python
class torch.nn.Conv2d(in_channels, out_channels, kernel_size, stride=1, padding=0, dilation=1, groups=1, bias=True)
```
and the neural network will learn the weights by itself during training process.