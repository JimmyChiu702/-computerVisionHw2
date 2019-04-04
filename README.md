# Generate Images with GANPaint
原圖|加草|加藍天|加樹 
-|-|-|-|-
![](https://i.imgur.com/KqdiFpY.png)|![](https://i.imgur.com/p9VLOzh.png)|![](https://i.imgur.com/KLaDhe0.png)|![](https://i.imgur.com/VWpucDy.png)

# Dissect any GAN model and Analyze What You Find
我們的model使用的是living room，我們在各層間發現一些現象：
1. level1偵測living room的特徵比較模糊，基本上就是佈景中的某個區塊，還看不出區塊中明顯的特性，例如：
![](https://i.imgur.com/CtkErXs.png)![](https://i.imgur.com/9aFQqmi.png)![](https://i.imgur.com/8e9LITe.png)
![](https://i.imgur.com/1GrC4aD.png)![](https://i.imgur.com/XfbKjT8.png)![](https://i.imgur.com/w11Cg4j.png)
level7偵測living room的特徵就變得比較明顯，這些特徵也變得更複雜更多元，不再只是場景中的特定區塊


2. 我們觀察到這些units偏好學習以下幾種物品：
    * 沙發
    * 窗簾
    * 天花板
    * 桌子
    * 牆壁
    * 壁畫

# Compare with other method - Patch Match
This method can find the corresponding patch of the target image from the source image, and then use the corresponding patches to construct the edge region. This method can used in applications such as object removal, reshuffle, and moving object in one image.

## Algorithm
### 1. Define the DDF(Nearest Neighbor Field) function
Define the DDF function and use it to find the correspondence of patches.

### 2. Get the Offsetmap
Find the corresponding patch of every patch using DDF function, and construct offsetmap to record the offset of the corresponding patch.

### 3. Reshuffle
Use the offsetmap to reshuffle the patches. And this method use coarse-to-fine approach to get better result.