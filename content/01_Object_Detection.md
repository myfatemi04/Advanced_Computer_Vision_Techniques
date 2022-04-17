# object detection

[https://jonathan-hui.medium.com/object-detection-speed-and-accuracy-comparison-faster-r-cnn-r-fcn-ssd-and-yolo-5425656ae359](https://jonathan-hui.medium.com/object-detection-speed-and-accuracy-comparison-faster-r-cnn-r-fcn-ssd-and-yolo-5425656ae359)

Fast R-CNN + ZFnet

Feature maps can vote on certain areas of the image, just like a more complicated Hough transform. these are called position-sensitive score maps

R-CNN and Fast R-CNN: Generate region proposals, and then for each region, predict bounding box offsets and the classification

[R-FCN](https://jonathan-hui.medium.com/understanding-region-based-fully-convolutional-networks-r-fcn-for-object-detection-828316f07c99): Fully Convolutional Network. Instead of running a new alg on each ROI, it does something fully convolutional on the entire image, and then selects from that with the ROIs.

- Each subsection of the ROI is classified based on the expected image at that position. this is called a position-based ROI. the ROI is converted into a map which denotes the likelihood of that section of the ROI belonging to that section of the original object. so if you had an ROI for a car, and you had the left door of the car on the right side of the ROI, it would be scored lowly, even though the left door of the car would still be classified as a car. this is because the side of the car is invalid for that bounding box.
    - could this be used for instance segmentation too? such as predicting the border between two instances? or what if you could do position-based instance segmentation
    - the position-based ROI is calculated extremely effectively: we have a channel corresponding to each position-sensitive score map. basically, a channel for the left side of a car, the right side of a car, etc. then, we go through the ROI, and multiply the left side of the ROI by the channel for the left side of the car, and multiply the right side of the ROI by the channel for the right side of the car, etc. this allows for much more computation to be shared, and imo is extremely clever.
- R-FCN is 20x faster than Fast R-CNN. Very cool!! barely sacrifices accuracy.
