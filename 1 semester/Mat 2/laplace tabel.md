
![[Pasted image 20241122084247.png]]
![[Pasted image 20241122100911.png]]
### Laplace ex
![[Pasted image 20250224155532.png]]
Example 1 Solve the following IVP. $$y′′−10y′+9y=5t, \ y(0)=−1 \ , \ y′(0)=2$$

Hide Solution

The first step in using Laplace transforms to solve an IVP is to take the transform of every term in the differential equation.

$$L({y′′})−10L({y′})+9L({y})=L({5t})
$$
Using the appropriate formulas from our [table of Laplace transforms](https://tutorial.math.lamar.edu/classes/de/Laplace_Table.aspx) gives us the following.

$$s^2Y(s)−sy(0)−y^′(0)−10(sY(s)−y(0))+9Y(s)=\frac{5}{s^2}
$$
Plug in the initial conditions and collect all the terms that have a Y(s)

in them.

$$(s^2−10s+9)Y(s)+s−12=\frac{5}{s^2}
$$
Solve for Y(s)

.

$$Y(s)=\frac{5}{s^2(s−9)(s−1)}+\frac{12−s}{(s−9) (s−1)}
$$
At this point it’s convenient to recall just what we’re trying to do. We are trying to find the solution, y(t)

, to an IVP. What we’ve managed to find at this point is not the solution, but its Laplace transform. So, in order to find the solution all that we need to do is to take the inverse transform.

Before doing that let’s notice that in its present form we will have to do partial fractions twice. However, if we combine the two terms up we will only be doing partial fractions once. Not only that, but the denominator for the combined term will be identical to the denominator of the first term. This means that we are going to partial fraction up a term with that denominator no matter what so we might as well make the numerator slightly messier and then just partial fraction once.

This is one of those things where we are apparently making the problem messier, but in the process we are going to save ourselves a fair amount of work!

Combining the two terms gives,

$$Y(s)=5+\frac{12s^2−s^3}{s^2(s−9)(s−1)}
$$
The partial fraction decomposition for this transform is,

$$Y(s)=\frac{A}{s}+\frac{B}{s^2}+\frac{C}{s-9}+\frac{D}{s-1}
$$
Setting numerators equal gives,

$$5+12s^2−s^3=As(s−9)(s−1)+B(s−9)(s−1)+Cs^2(s−1)+Ds^2(s−9)
$$
![[Pasted image 20241206092650.png]]