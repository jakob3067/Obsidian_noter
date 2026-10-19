
Forward mapping vs backwords mapping
**Forward example**
![[Pasted image 20260628114129.png]]
**Backwords example**
![[Pasted image 20260628114159.png]]






Backwords mapping
![[Pasted image 20260628114110.png]]




Linear vs ikke linear tranformation af billede
![[Pasted image 20260628114310.png]]


### Affline tranformation

![[Pasted image 20260628114603.png]]

**Know tranformation**
if you know the translation you want for the pickture

**unknown tranforamtion**
Sometimes you dont know the transformations so you can sample 3 observation to be sure 


### Perspective tranformation

![[Pasted image 20260628121640.png]]


# interpolation

When backward mapping gives you a non-integer source coordinate like (2.67), that exact position doesn't exist in the pixel grid — pixels only live at integer locations. Interpolation is how you estimate the value at that in-between position using the surrounding known pixels.


![[Pasted image 20260628122708.png]]'


## non linear distortion
![[Pasted image 20260628122816.png]]


![[Pasted image 20260628122801.png]]


