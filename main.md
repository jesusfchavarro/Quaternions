<section id="themes">
	<h2>Themes</h2>
		<p>
			Set your presentation theme: <br>
			<!-- Hacks to swap themes after the page has loaded. Not flexible and only intended for the reveal.js demo deck. -->
                        <a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/black.css'); return false;">Black (default)</a> -
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/white.css'); return false;">White</a> -
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/league.css'); return false;">League</a> -
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/sky.css'); return false;">Sky</a> -
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/beige.css'); return false;">Beige</a> -
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/simple.css'); return false;">Simple</a> <br>
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/serif.css'); return false;">Serif</a> -
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/blood.css'); return false;">Blood</a> -
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/night.css'); return false;">Night</a> -
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/moon.css'); return false;">Moon</a> -
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/solarized.css'); return false;">Solarized</a>
		</p>
</section>

H:

# Quaternions

Jesus Felipe Chavarro Muñoz

H:

## Index

  1. Complex numbers
	- Definition
	- Operation
	- Conjugate
	- Magnitude
	- Rotation
	- Matrix representation

V:

2. Quaternions
	- Definition
	- Magnitude
	- Conjugate and inverse
	- Quaternions as an Axis-Angle Pair
	- Negation
	- Identity
	- Multiplication
	- 3D rotation

V: 

3. Geometric interpretation
4. Interpolations
	- "Difference"
	- Exponentiation
	- Slerp
	- Squad

H: 

## Complex numbers

<img src="fig/fig1.svg" alt="Complex plane" width="40%" style="float: left; background: white; margin-right:25px;">
<div style="width: auto; float: rigth; margin=auto">
The complex pair $(a, b)$ defines the number $a+bi$, where $i$ is the so-called imaginary number such that $i^2 = –1$.

The set of complex numbers “live” in a 2D plane.
</div>
V: 

### Operations
#### sum

$$ (a+bi) + (c+di) = (a+c) + (b+d)i$$

#### multiplication

\\begin{aligned}
(a+bi) (c+di) &= ac + adi + bci + bdi^{2} \\\\ 
&= ac + (ad + bc)i + bd(-1) \\\\
&= (ac - bd) + (ad + bc)i 
\\end{aligned}

V:

### Conjugate

<img src="fig/fig2.svg" alt="Complex plane" width="33%" style="float: left; background: white; margin-right:25px;">

<div style="width: auto; float: rigth; margin=auto">
We can compute the conjugate of a complex number by negating the imaginary portion.
$$z = (x+yi)$$
$$\overline {z} = z^{*} = (x-yi)$$
</div>

V:

### Magnitude

\\begin{aligned}
\\lVert p \\rVert &= \sqrt {pp^{*}}  \\\\
\\lVert (a+bi) \\rVert &= \sqrt {(a+bi)(a-bi)} \\\\ 
\\lVert (a+bi) \\rVert &= \sqrt {a^{2}+b^{2}} \\\\
\\end{aligned}

V:

### Rotation

To perform a rotation, we define a second complex number $q = (\cos \theta, \sin \theta)$. Now, the rotated
vector $p'$ can be computed by the complex multiplication:


\\begin{aligned}
p &= (x+yi)  \\\\
q &= (\cos \theta + (\sin \theta)i)  \\\\
p'&= pq \\\\
  &= (x+yi)(\cos \theta + (\sin \theta)i) \\\\
  &= (x\cos \theta - y\sin \theta) + (x\sin \theta + y\cos \theta)i
\\end{aligned}

V:

### Matrix representation

Complex numbers $a + bi$ can also be represented by 2×2 matrices that have the following form:

$$P = \begin{pmatrix}a&-b\\\\b&a\end{pmatrix}$$

 - The squere of the magnitude $\\lVert p \\rVert$ is the determinant: $\lVert p \rVert^{2} = \det P$ . <!-- .element: class="fragment" data-fragment-index="1" -->
 - The conjugate corresponds to the transpose: $p^{*} = P^{T}$. <!-- .element: class="fragment" data-fragment-index="2" -->

H:

## Quaternions

A quaternion contains a scalar component and a 3D vector component. We usually refer to the sca-
lar component as $w$.

$$ [w\ \mathbf{v}] = [ w \ (x\ y\ z)] = (x\ y\ z\ w)$$ 

V:

### Quaternions - complex

Quaternions extend the complex number system by having three imaginary numbers, $i$, $j$, and
$k$, which are related as follows:

$$i^{2}=j^{2}=k^{2}=ijk=-1$$ <!-- .element: class="fragment" data-fragment-index="1" -->

$$ij=k, ji=-k$$ <!-- .element: class="fragment" data-fragment-index="2" -->

$$jk=i, kj=-i$$ <!-- .element: class="fragment" data-fragment-index="3" -->

$$ki=j, ik=-i$$ <!-- .element: class="fragment" data-fragment-index="4" -->

V:

### Magnitude

\\begin{aligned}
\\lVert \mathbf{p} \\rVert &= \\lVert [ w \ (x\ y\ z)] \\rVert \\\\
		&= \\lVert [ w \ \mathbf{v}] \\rVert \\\\ 
		&= \sqrt {w^{2} + \\lVert \mathbf{v} \\rVert^{2} }  \\\\
		&= \sqrt {w^{2} + x^{2} + y^{2} + z^{2}}  \\\\
\\end{aligned}

V:

### Conjugate and inverse

The conjugate of a quaternion, denoted $\mathbf{q}^{*}$ , is obtained by negating the vector portion of the quaternion: 

\\begin{aligned}
\mathbf{q}^{\*} &= [ w \ \mathbf{v}]^{*}  \\\\
		&= [ w \ -\mathbf{v}] \\\\ 
		&= [ w \ (-x\ -y\ -z)]  \\\\
\\end{aligned} <!-- .element: class="fragment" data-fragment-index="1" -->

V:

The inverse of a quaternion, denoted $\mathbf{q}^{-1}$ , is defined as the conjugate of a quaternion divided by its magnitude: 

$$ \mathbf{q}^{-1} = \frac{\mathbf{q}^{\*}}{ \\lVert \mathbf{q} \\rVert } $$

When we multiply a quaternion q by its inverse $\mathbf{q}^{-1}$ , we get the identity quaternion $ [1, \mathbf{0}]$.

V:

### Quaternions as an Axis-Angle Pair

Let us define the vector $\mathbf{n}$ to be the axis of rotation and the scalar $\theta$ to be the amount of rotation about this axis.

\\begin{aligned}
\mathbf{q} &= [ \cos(\theta/2) \ \sin(\theta/2)\mathbf{n}]  \\\\
		&= [ \cos(\theta/2) \ (\sin(\theta/2)x \ \sin(\theta/2)y \ \sin(\theta/2)z \)]
\\end{aligned} <!-- .element: class="fragment" data-fragment-index="1" -->

V:

### Negation

$$ -q = -[w\ \mathbf{v}] = -[w\ \mathbf{v}] = (-x\ -y\ -z\ -w)$$ 

the quaternions $\mathbf{q}$ and $\mathbf{-q}$ actually represent the same angular displacement. 

### Identity  <!-- .element: class="fragment" data-fragment-index="1" -->

When we multiply any quaternion $\mathbf{q}$ by the identity quaternion, the result is $\mathbf{q}$. <!-- .element: class="fragment" data-fragment-index="1" -->

$$ \mathbf{I} = [1, \mathbf{0}] $$ <!-- .element: class="fragment" data-fragment-index="2" -->

V:

### Quaternion Multiplication

Quaternions can be multiplied according to their complex number interpretation.

$$ (w_{1}+x_{1}i + y_{1}j + z_{1}k)(w_{2}+x_{2}i + y_{2}j + z_{2}k) $$

After a lot of arithmetic we could say: <!-- .element: class="fragment" data-fragment-index="1" -->

$$ [w_{1}\ \mathbf{v}\_{1}] \[w_{2}\ \mathbf{v}\_{2}] $$ <!-- .element: class="fragment" data-fragment-index="2" -->

$$ = [ w_{1} w_{2} - \mathbf{v}\_{1} \cdot \mathbf{v}\_{2} \ \ \ w_{1}\mathbf{v}\_{2} + w_{2}\mathbf{v}\_{1} + \mathbf{v}\_{2} \times \mathbf{v}_{1}] $$ <!-- .element: class="fragment" data-fragment-index="2" -->

V: 

### 3D rotation

Let us “extend” a standard 3D $(x\ y\ z)$ point into quaternion space:

$$\mathbf{p} = [0\ (x\ y\ z) ]$$

Let $\mathbf{q}$ be a rotation quaternion, where $\mathbf{n}$ is a unit vector axis of rotation, and $\theta$ is the rotation angle. <!-- .element: class="fragment" data-fragment-index="1" -->

$$\mathbf{q} = [ \cos(\theta/2) \ \sin(\theta/2)\mathbf{n}]$$ <!-- .element: class="fragment" data-fragment-index="1" -->

V: 

we can rotate the 3D point $\mathbf{p}$ about $\mathbf{n}$ by performing the following quaternion multiplication:

$$\mathbf{p}^{´} = \mathbf{qpq}^{-1}$$


<section data-background="https://media.giphy.com/media/CiYImHHBivpAs/giphy.gif">
	
</section>

V:
<div style="float:left">
<h2>What?</h2>
$$\mathbf{p}^{´} = \mathbf{qpq}^{-1}$$
</div>

H:

## Geometric interpretation

Given the multiplication $ij = k$, we could think in 2 ways:

- $i$ is an action and $j$ is the point.
- $j$ is an action and $i$ is the point.

respectively:
- $j$ is rotate with the right-hand rule with the thumb pointing $i$ direction.
- $i$ is rotate with the left-hand rule with the thumb pointing $j$ direction. 

<section data-background-iframe="https://eater.net/quaternions/video/intro" data-background-interactive></section>

V: 

H:

## Difference and interpolations

V:

### Quaternion “Difference”

For given orientations $\mathbf{a}$ and $\mathbf{b}$, we can compute the angular displacement
$\mathbf{d}$ which rotates from $\mathbf{a}$ to $\mathbf{b}$:

\\begin{aligned}
\mathbf{ad} &= \mathbf{b}  \\\\
\mathbf{(a^{-1}a)d}	&= \mathbf{a^{-1}b}  \\\\
[1\ \mathbf{0}]\mathbf{d}	&= \mathbf{a^{-1}b}  \\\\
\mathbf{d}	&= \mathbf{a^{-1}b}  \\\\
\\end{aligned} 

Now we have a quaternion to represent the angular displacement from one orientation to another.

V:

### Quaternion Exponentiation

- Quaternions can be exponentiated (raised to a power). This is denoted $\mathbf{q}^{t}$.
- As $t$ varies from $0...1$, $\mathbf{q}^{t}$ varies from $[1,\ \mathbf{0}]...\mathbf{q}$. 
- To compute a quaternion that represents one-third of the angular displacement represented by the quaternion $\mathbf{q}$, we would compute $\mathbf{q}^{1/3}$. 

V:

### Interpolation — aka “Slerp”

Stands for **S**pherical **L**inear int**erp**olation. Slerp is a ternary operator, take the "starting" and "ending" orientation and a interpolation paramenter:

$$slerp(\mathbf{q}\_{0},\mathbf{q}\_{1},t)$$

This function will return an orientation that interpolates from $\mathbf{q}\_{0}$ and $\mathbf{q}\_{1}$.

V:

If we were interpolating between two scalar values $a_{0}$ and $a_{1}$:

\\begin{aligned}
\Delta a &= a_{1} - a_{0} \\\\
lerp(a_{0},a_{1},t) &= a_{0} + t\Delta a 
\\end{aligned}

with the quarterion difference and exponentiation:

\\begin{aligned}
\Delta \mathbf{q} &= \mathbf{q}\_{0}^{-1}\mathbf{q}\_{1} \\\\
slerp(a_{0},a_{1},t) &= \mathbf{q}\_{0}\Delta\mathbf{q}^{t} 
\\end{aligned}

V:

### Quaternion Splines — aka “Squad”

Slerp provides interpolation between two orientations, but with a path with more than 3 points Slerp make discontinuities. 

In this case we use a Squad interpolation, which stand for **s**pherical and **quad**rangle, to thace our a path between control points.

V:

Let our “control points” be defined by a sequence of quaternions:

$$\mathbf{q\_{1},q\_{2},q\_{3},...,q\_{n-2},q\_{n-1},q\_{n}}$$

We will also define the “helper” quaternion $s_{i}$ , which can be thought of as intermediate control points:

$$ s_{i} = \exp(-\frac{\log(\mathbf{q}\_{i+1}\mathbf{q}\_{i}^{-1})+\log(\mathbf{q}\_{i-1}\mathbf{q}\_{i}^{-1})}{4})\mathbf{q}\_{i}$$

V:

We will also define an interpolation parameter $h$. As $h$ varies from $0...1$, squad traces out the segment of the curve between $\mathbf{q}\_{i}$ and $\mathbf{q}\_{i+1}$ :


$$squad(\mathbf{q}\_{i},\mathbf{q}\_{i+1},\mathbf{s}\_{i},\mathbf{s}\_{i+1},h) = $$
$$slerp(slerp(\mathbf{q}\_{i},\mathbf{q}\_{i+1},h),slerp(\mathbf{s}\_{i},\mathbf{s}\_{i+1},h),2h(1-h))$$

V:

<iframe width="1120" height="530" src="https://www.youtube.com/embed/_AjirMJx3Ds" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

H:

## References
* [Math primer for graphics and game development](https://tfetimes.com/wp-content/uploads/2015/04/F.Dunn-I.Parberry-3D-Math-Primer-for-Graphics-and-Game-Development.pdf)
* [Quaternions and spatial rotation - Wikipedia](https://en.wikipedia.org/wiki/Quaternions_and_spatial_rotation)
* [Visualizing quaternions](https://eater.net/quaternions)