--- 
front: 
hard: Getting Started 
time: minutes 
--- 

# Quaternion 

- Description 

Quaternions are used to represent rotations. 

They are compact and not affected by gimbal lock. 

They are based on complex numbers and are not easy to understand. You will rarely have the opportunity to access or modify individual quaternion components (x, y, z, w) 

You can rotate a rotation using multiplication, or rotate a vector. 

## Constructor 

### Quaternion(x, y, z, w) 

- Description 

Used to construct a rotation. 

- Parameters 

| Parameter name | Data type | Description | 
| ------ | :------- | :------------------------------------ | 
| x | float | The x component of the quaternion | 
| y | float | The y component of the quaternion | 
| z | float | The z component of the quaternion | 
| w | float | The w component of the quaternion. Do not modify the quaternion directly. | 

- Return value 

| Data type | Description | 
| :--------- | :------------------------- | 
| Quaternion | Returns Quaternion(x, y, z, w) | 

- Example 

```python 
from common.utils.mcmath import Quaternion 
q = Quaternion(1, 2, 3, 4) 
``` 



### Quaternion(vecTuple) 

- Description 

Used to construct a rotation. 

- Parameters 

| Parameter name | Data type | Description | 
| -------- | :-------------------------------- | :----------------- | 
| vecTuple | tuple(float, float, float, float) | 4-length tuple array | 

- Return value 

| Data type | Description | 
| :--------- | :----------------------------------------------------------- | 
| Quaternion | Returns Quaternion(vecTuple[0], vecTuple[1], vecTuple[2], vecTuple[3]) | 

- Example 

```python 
from common.utils.mcmath import Quaternion 
a = (0, 0, 0, 1) 
q = Quaternion(a) 
``` 

## Static method 

Static method that can be called directly through Quaternion.MethodName() without creating an instance.

### AngleAxis 

- Description 

Creates a rotation of `angle` degrees around `axis` 

- Parameters 

| Parameter name | Data type | Description | 
| ------ | :------- | :------- | 
| angle | float | Angle of rotation | 
| axis | Vector3 | Axis of rotation | 

- Return value 

| Data type | Description | 
| :--------- | :-------------------------------- | 
| Quaternion | Rotation of `angle` degrees around `axis` |


- Example 

```python 
from common.utils.mcmath import Quaternion 
newQuaternion = Quaternion.AngleAxis(45, Vector3.Up()) # Create a rotation of 45° around the y axis 
``` 

### Euler 

- Description 

Create a rotation of z degrees around the Z axis, then x degrees around the X axis, and finally y degrees around the Y axis (note the order). Note: If the Euler rotation has a universal joint lock, the EulerAngle returned by the quaternion will be abnormal. 

- Parameters 

| Parameter name | Data type | Description | 
| ------ | :------- | :---------------- | 
| x | float | Angle of rotation around the x-axis | 
| y | float | Angle of rotation around the y-axis | 
| z | float | Angle of rotation around the z-axis | 

- Return value 

| Data type | Description | 
| :--------- | :----------------------------------------------------------- | 
| Quaternion | Rotate z degrees around the Z axis first, then x degrees around the X axis, and finally y degrees around the Y axis | 

- Example 

```python 
from common.utils.mcmath import Quaternion 
newQuaternion = Quaternion.Euler(30, 15, 45) # Create a rotation that first rotates 45° around the z-axis, then 30° around the x-axis, and finally 45° around the y-axis 
``` 

### Dot 

- Description 

The dot product of two rotations. 

The dot product is a floating point value that is equal to the sum of the products of the corresponding components of the two rotations. 

- Parameters 

| Parameter Name | Data Type | Description |

| ------ | :--------- | :---- | 
| a | Quaternion | Rotate a | 
| b | Quaternion | Rotate b | 

- Return value 

| Data type | Description | 
| :------- | :------------- | 
| float | Dot product of two vectors | 

- Example 

```python 
from common.utils.mcmath import Quaternion 
a = Quaternion(1, 2, 3, 1) 
b = Quaternion(0, 3, 1, 1) 
c = Quaternion.Dot(a, b) # 1 * 0 + 2 * 3 + 3 * 1 + 1 * 1 = 10 
``` 

### Cross 

- Description 
The Glassermann product of two rotations. Cross(a, b) represents the resultant rotation of rotating a and then rotating p. It can also be obtained directly through a * b. 

- Parameters 

| Parameter name | Data type | Description | 
| ------ | :--------- | :---- | 
| a | Quaternion | Rotate a | 
| b | Quaternion | Rotate b | 

- Return value 

| Data type | Description | 
| :--------- | :------------------- | 
| Quaternion | Grassmann product of two vectors | 

- Example 

```python 
from common.utils.mcmath import Quaternion 
a = Quaternion(1, 2, 3, 1) 
b = Quaternion(0, 3, 1, 1) 
c = Quaternion.Cross(a, b) 
``` 




### Conjugate 

- Description 

Returns the conjugate rotation of the rotation, with the w component unchanged and the other components negated 

- Parameters 

| Parameter name | Data type | Description | 
| ------ | :--------- | :---- | 
| q | Quaternion | Rotate q | 

- Return value 

| Data type | Description | 
| :--------- | :----------- | 
| Quaternion | Returns the conjugate rotation | 

- Example 

```python 
from common.utils.mcmath import Quaternion 
a = Quaternion(1, 2, 3, 1) 
b = Quaternion.Conjugate(a) # (-1, -2, -3, 1) 
``` 

### Inverse 

- Description 

Returns the inverse rotation of the rotation. If the modulus of rotation q is 1, then q*q<sup>-1</sup> will result in a zero rotation (0, 0, 0, 1) 

- Parameters 

| Parameter name | Data type | Description | 
| ------ | :--------- | :---- | 
| q | Quaternion | Rotation q | 

- Return value 

| Data type | Description | 
| :--------- | :---------------- | 
| Quaternion | Returns the inverse rotation of rotation q | 

- Example 

```python

from common.utils.mcmath import Quaternion 
a = Quaternion(1, 2, 3, 1) 
a.Normalize() # Normalize a 
b = Quaternion.Inverse(a) # b is the inverse rotation of a 
print a * b # The printed result is approximately (0, 0, 0, 1), and there may be very small non-zero numbers due to precision issues 
``` 

## Member methods 

### Length 

- Description 

Returns the length of the vector. 

The length of the vector is the square root of `(x*x+y*y+z*z)`. 

If you only need to compare the size of some vectors, you can use the LengthSquared() function to compare their squares (calculating squares is faster). 

- Return value 

| Data type | Description | 
| :------- | :--------------- | 
| float | The square of the length of the vector | 

- Example 

```python 
from common.utils.mcmath import Quaternion 
q = Quaternion(3, 4, 0, 0) 
print q.Length() # print 5 
``` 

### LengthSquared 

- Description 

Returns the square of the length of the vector. 

- Return value 

| Data type | Description | 
| :------- | :------------------- | 
| float | The vector normalized | 

- Example


```python 
from common.utils.mcmath import Quaternion 
q = Quaternion(3, 4, 0, 0) 
print q.LengthSquared() # print 25 
``` 

### ToTuple 

- Description 

Returns the tuple form (x, y, z, w) of the vector, which is convenient for players to convert and pass as parameters of other events. 

- Return Value 

| Data Type | Description | 
| :------- | :-------------------------------- | 
| tuple | Returns the tuple form of the vector (x, y, z, w) | 

- Example 

```python 
from common.utils.mcmath import Quaternion 
q = Quaternion(0, 0, 0, 1) 
print q.ToTuple() # print (0, 0, 0, 1) 
``` 

### Normalized 

- Description 

Returns the quaternion with a magnitude of 1. 

When normalizing, the quaternion orientation remains unchanged, but its magnitude is 1.0. 

Note that the current quaternion remains unchanged, and a new normalized quaternion is returned. If you want to normalize the original quaternion, use the Normalize method instead. 

If the quaternion is too small to be normalized, (0, 0, 0, 1) is returned, indicating zero rotation. 

- Return Value 

| Data Type | Description | 
| :--------- | :--------------------- | 
| Quaternion | The quaternion after normalization of this vector | 

- Example


```python 
from common.utils.mcmath import Quaternion 
q = Quaternion(3, 4, 0, 0) 
print q.Normalized() # print result (0.6, 0.8, 0, 0) 
print q # print result (3, 4, 0, 0), q has not changed 
``` 

### Normalize 

- Description 

Normalize the vector, the direction of the vector remains unchanged, but its length becomes 1.0. 

Please note that this function has no return value and only changes the current vector. If you want to return the normalized value of the current vector without changing the vector, please use the Normalized function. 

If the vector is too small to be normalized, it is set to the zero vector. 

- Example 

```python 
from common.utils.mcmath import Quaternion 
q = Quaternion(3, 4, 0, 0) 
q.Normalize() 
print q # print result (0.6, 0.8, 0, 0), q is normalized 
``` 

### EulerAngles 

- Description 

Returns a rotation of euler.z degrees around the z axis, euler.x degrees around the x axis, and euler.y degrees around the y axis (in that order). Euler angles can be read from a quaternion. Note: If the Euler rotation has a universal joint lock, the EulerAngle returned by the quaternion will be abnormal. 

- Example 

```python 
from common.utils.mcmath import Quaternion 
q = Quaternion.Euler(30, 15, 45) # Create a rotation that first rotates 45° around the z-axis, then 30° around the x-axis, and finally 45° around the y-axis 
print q.EulerAngles() # Print the result (30, 15, 45) 
``` 

## Operator 

### operate *


- Description 

Rotation multiplication, multiplication of two rotations means rotating the rotation on the left side of the operator first, then rotating the rotation on the right side of the operator. Equivalent to Quaternion.Cross(a, b). Does not satisfy the commutative law of multiplication, i.e. `a*b != b*a` 

### operate == 

- Description 

Determine whether two rotations are equal, and return True only when all components are equal 

