# Lab 6
This lab will focus of laplacian, sobel, and unsharped mask.

## Laplacian
The Laplacian filter, often referred to as the Laplacian of Gaussian (LoG), is a popular edge detection filter used in image processing. It highlights regions of rapid intensity change in an image, typically corresponding to edges. The Laplacian filter is particularly effective at detecting edges in noisy images because it considers the second derivative of the image intensity.

    ### 1D Laplacian First Equation
```python
matrix = np.array([[50, 60, 70, 60, 50, 50],
                   [50, 60, 60, 60, 50, 50],
                   [50, 50, 50, 50, 50, 50],
                   [100, 120, 130, 140, 120, 100],
                   [100, 100, 100, 100, 100, 100],
                   [100, 100, 100, 100, 100, 100]])
```
Create Image

```python
laplacian_image1d = np.zeros_like(matrix)
for i in range(matrix.shape[0]):
    for j in range(matrix.shape[1]-1):
        laplacian_image1d[i, j] = matrix[i,j+1] - matrix[i,j]
print(laplacian_image1d)

>[[ 10  10 -10 -10   0   0]
 [ 10   0   0 -10   0   0]
 [  0   0   0   0   0   0]
 [ 20  10  10 -20 -20   0]
 [  0   0   0   0   0   0]
 [  0   0   0   0   0   0]]
```
Use sliding windows algorthim

### 1D Laplacian Second Equation

```python
laplacian_image2d = np.zeros_like(matrix2)
for i in range(matrix2.shape[0]):
    for j in range(1,matrix2.shape[1]-2):
        print(f"{matrix2[i,j]} + {matrix2[i,j+1]} + {matrix2[i,j-1]} - {2*matrix2[i,j]}")
        laplacian_image2d[i, j] = matrix2[i,j+1] + matrix2[i,j-1] - 2*matrix2[i,j]
laplacian_image2d
> array([[  0,   0, -20,   0,   0,   0],
       [  0, -10,   0, -10,   0,   0],
       [  0,   0,   0,   0,   0,   0],
       [  0, -10,   0, -30,   0,   0],
       [  0,   0,   0,   0,   0,   0],
       [  0,   0,   0,   0,   0,   0]])
```

### 2D Laplacian Second Equation.

```python
laplacian_image2d_second = np.zeros_like(matrix3)
for i in range(1,matrix3.shape[0]-2):
    for j in range(1,matrix3.shape[1]-2):
        print(f"index({i}, {j}): {matrix3[i+1,j]} + {matrix3[i-1,j]} + {matrix3[i,j+1]} + {matrix3[i,j-1]} - {4*matrix3[i,j]}")
        laplacian_image2d_second[i, j] = matrix3[i+1,j] + matrix3[i-1,j] + matrix3[i,j+1] + matrix3[i,j-1] - 4*matrix3[i,j]
laplacian_image2d_second
> array([[  0,   0,   0,   0,   0,   0],
       [  0,   0,   0,   0,   0,   0],
       [  0,  50,  50,  50,   0,   0],
       [  0, -50, -50, -50,   0,   0],
       [  0,   0,   0,   0,   0,   0],
       [  0,   0,   0,   0,   0,   0]])
```

### 2D laplacian filter.
All the pervious code uses equations but we can use a predefined filter.
```python
laplacian_kernel = np.array([[0, 1, 0],
                             [1, -4, 1],
                             [0, 1, 0]])
```
this is the filter for 2nd laplacian.
```python
laplacian_image_filter = np.zeros_like(matrix3)
for i in range(matrix3.shape[0]-2):
    for j in range(matrix3.shape[1]-2):
        laplacian_image_filter[i+1, j+1] = np.sum(laplacian_kernel * matrix3[i:i+3,j:j+3])
laplacian_image_filter
> array([[  0,   0,   0,   0,   0,   0],
       [  0,   0,   0,   0,   0,   0],
       [  0,  50,  50,  50,  50,   0],
       [  0, -50, -50, -50, -50,   0],
       [  0,   0,   0,   0,   0,   0],
       [  0,   0,   0,   0,   0,   0]])
```
Appling filter on the image yelled the same result.


### Laplacian on image

```python
image = ski.io.imread(r"./media/1-nature-photography-spring-season-mumtazshamsee.jpg",as_gray=True)
ski.io.imshow(image)
```
![alt text](image.png)
```python
image_laplacian = convolve(image, laplacian_kernel)
ski.io.imshow(image_laplacian)
```
![alt text](image-2.png)

to sharp image:
```python
sharp_image = image - image_laplacian
plt.imshow(sharp_image, cmap='gray')
```
![alt text](image-3.png)

## Sobel

The Sobel filter is a popular edge detection technique used in image processing and computer vision. It computes the gradient of the image intensity at each pixel, highlighting regions of high spatial frequency that correspond to edges. The Sobel filter is particularly useful because it combines smoothing (to reduce noise) with differentiation (to find edges). The Sobel filter uses two 3x3 convolution kernels to compute the gradient in the x (horizontal) and y (vertical) directions. The kernels are designed to respond maximally to edges running horizontally and vertically relative to the pixel grid.

Sobel has 2 filters one in x-direction and the other in y-direction.

code
```python
Sobel_x = np.array([[-1, 0, 1], [-2, 0, 2], [-1, 0, 1]])
Sobel_y = np.array([[1, 2, 1], [0, 0, 0], [-1, -2, -1]])
```
create x and y direction filters.

```python
G_X_image = image.copy()
G_Y_image = image.copy()

for i in range(1, image.shape[0] - 1):
    for j in range(1, image.shape[1] - 1):
        G_X_image[i, j] = np.sum(image[i - 1:i + 2, j - 1:j + 2] * Sobel_x)
        G_Y_image[i, j] = np.sum(image[i - 1:i + 2, j - 1:j + 2] * Sobel_y)
```
use sliding window algorthim.

```python
Soble_image = np.abs(G_X_image) + np.abs(G_Y_image)
```
after calculating x and y direction, add the 2 direction together to display all edges in the image.

```python
ski.io.imshow((Soble_image*100).astype(np.uint8))
```
Output:
![alt text](image-4.png)

Using library
```python
G_x = convolve(image, Sobel_x)
G_y = convolve(image, Sobel_y)
sobel = np.abs(G_x) + np.abs(G_y)
ski.io.imshow((sobel*100).astype(np.uint8))
```
![alt text](image-5.png)

## Unsharped mask

Unsharp masking is a technique used in image processing to enhance the edges and details in an image, making it appear sharper. Despite its name, unsharp masking is a sharpening method. The technique works by subtracting a blurred version of the image from the original image, thus highlighting areas of rapid intensity change (edges).

How Unsharp Masking Works
1. Blurring the Image: Create a blurred (or unsharp) version of the original image. This is typically done using a Gaussian blur.
2. Creating the Mask: Subtract the blurred image from the original image to create a mask that highlights the edges.
3. Adding the Mask to the Original: Add the mask back to the original image, thus enhancing the edges and details.

code: standard blur
```python
blured_image = image.copy()
for i in range(1, image.shape[0] - 1):
    for j in range(1, image.shape[1] - 1):
        blured_image[i, j] = np.mean(image[i-1:i+2, j-1:j+2])
ski.io.imshow(blured_image)
```
![alt text](image-6.png)

Code: unsharp mask 
```python
unsharp_mask = image - blured_image
ski.io.imshow(unsharp_mask)
```
![alt text](image-7.png)

code: sharped image
```python
k = 1.5
sharp_image = image + k*unsharp_mask
ski.io.imshow((sharp_image*255).astype(np.uint8))
```
![alt text](image-8.png)

code: Library
```python
import cv2

# Apply average blur
blurred_image = cv2.blur(image, (5, 5))
unsharp_mask = image - blurred_image
k = 1.5
sharp_image = image + k*unsharp_mask
ski.io.imshow((sharp_image*255).astype(np.uint8))
```
![alt text](image-9.png)