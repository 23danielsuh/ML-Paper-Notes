# Wasserstein and Bottleneck Distance
### Bottleneck Distance
- Let's say we are given a persistence diagram with a set of points $\{b_i, d_i\}$ from 2 different Persistent Homologies -> $\{p_1, p_2, p_3, ...\}$ and $\{q_1, q_2, q_3, ...\}$
- A partial match between $P$ and $Q$ is a bijection $M$ between a subset of $P$ and a subset of $Q$
	- A bijection is basically just every element of both sets are paired with another element of the other set
	- We can leave some of the points unpaired
	- We take the l-infinity distance, which is defined as $||p-q||_{\infty}=max(|b-b'|, |d-d'|)$, or the max between the two manhattan distances
	- For an unpaired point, we find the distance between the point $(b, d)$ and the nearest point on the diagonal: $\frac{d-b}{2}=||(b, d)-\frac{1}{2}(b+d, b+d)||_{\infty}$
	- Cost function c(M) can be defined (basically just take the max of these things):
	- ![[Screen Shot 2022-06-06 at 08.51.58.png]]
	- The bottleneck distance $d_b(P, Q)$ between persistance diagrams $P$ and $Q$ is:
	-   ![[Screen Shot 2022-06-06 at 08.54.44.png]]
		- This person left out that it takes the infimum over all partial matchings $M$
	- Some properties of the bottleneck distance:
		- $d_b(P, P) = 0$
		- $d_b(P, Q) = d_b(Q, P)$
		- $d_b(P, R) \leq d_b(P, Q) + d_b(Q, R)$

### Wasserstein Distance
![[Screen Shot 2022-06-06 at 09.01.48.png]]
- Wasserstein distance accounts for the closer functions $f$ and $g$, where as the $sup$ does not
- Geodesics - Shortest possible line between two points
	- Using the wasserstein distance, we just translate along the axis
	- Using the $sup$, we have to scale and change the shape of the different functions
- Wasserstein distance is really the difference between probability measures, not functions
- The functions are not functions, they are pdfs
- ![[Screen Shot 2022-06-06 at 09.05.59.png]]
- The goal is to move the blue points to the red points with minimal work
- This is what it looks like when you transport all of the blue pionts to the red points:
- ![[Screen Shot 2022-06-06 at 09.07.02.png]]
- Transport plan is how you allocate certain values to different points (see above)
	- $\sum y_{i, 1} = x_1$ and $\sum_{i, 2} = x_2$, etc.
- To use the Wasserstein distance, we look at all possible transport plans and choose the one with the lowest cost
- Cost function:
	- ![[Screen Shot 2022-06-06 at 09.12.06.png]]
		- $d(x_i, y_i)$ refers to the distance between the points (euclidean probably)
		- The conditions to the side refer to how the sums have to add up to each value for the points, and $\pi_{i, j}\geq 0$ because we can't transfer a negative value
		- A transport plan is a joint probability distribution
- Actual wasserstein distance:
	- ![[Screen Shot 2022-06-06 at 09.15.51.png]]