# Balzano Research Paper
- The problem involves dimensionality reduction: given a set of points in a high-dimensional space, find some smaller manifold $M$ which is a linear subspace of the high-dimensional data
- Topological features are those which are preserved bydeormations without tearing (?); a line and a parabola are topologically identical, but a line and a circle are not
- Persistent homology is supposed to reveal topological information about the manifold $M$
- Identifying a shape from a finite collection of noisy data points is called manifold learning
- The means of overcoming this problem is to replace each point with a small ball of radius $\epsilon$, which smooths the space between the data points
- The choice of $\epsilon$ is important - imagine there is a circle with a gap between some points. If we choose an $\epsilon$ too small, then we will see an arc. If we choose an $\epsilon$ correctly though, we will see the circle ^9285af
- However, persistent homology avoids the necessity of fine-tuning $\epsilon$ by keeping track of what happens for *all* values of $\epsilon$
- Topological features that prsist for a wide range of $\epsilon$ are deemed to be featurers of the data set
- The topological features desired are homology groups, which means the "number of holes" in the manifold
- $H_0$ can be defined as the number of connected components in the dataset, while $H_1$ refers to the 2-dimensional holes in the manifold, $H_2$ refers to the 3-dimensional holes, and so on
- $h_0$ and $h_1$ are integers called Betti numbers that can be attached to any manifold ^839b7f
- $h_0(M)$ is the number of connected components of $M$
- A point has $h_0=1$ and $h_1=0$
- A circle has $h_0=1$ and $h_1=1$
- Persistent Homology are very sensitive to outliers (if the outliers are uninteresting points, then it makes sense to clean them out)
- "How long is long enough to be called persistent" is not a well-understood concept