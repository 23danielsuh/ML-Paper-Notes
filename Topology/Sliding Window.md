# Sliding Window
### Code for Sliding Window
![[Screen Shot 2022-06-06 at 07.47.54.png]]![[Screen Shot 2022-06-06 at 07.48.02.png]]
```python
def getSlidingWindow(x, dim, Tau, dT):
    """
    Return a sliding window of a time series,
    using arbitrary sampling.  Use linear interpolation
    to fill in values in windows not on the original grid
    Parameters
    ----------
    x: ndarray(N)
        The original time series
    dim: int
        Dimension of sliding window (number of lags+1)
    Tau: float
        Length between lags, in units of time series
    dT: float
        Length between windows, in units of time series
    Returns
    -------
    X: ndarray(N, dim)
        All sliding windows stacked up
    """
    N = len(x)
    NWindows = int(np.floor((N-dim*Tau)/dT))
    if NWindows <= 0:
        print("Error: Tau too large for signal extent")
        return np.zeros((3, dim))
    X = np.zeros((NWindows, dim))
    spl = InterpolatedUnivariateSpline(np.arange(N), x)
    for i in range(NWindows):
        idxx = dT*i + Tau*np.arange(dim)
        start = int(np.floor(idxx[0]))
        end = int(np.ceil(idxx[-1]))+2
        # Only take windows that are within range
        if end >= len(x):
            X = X[0:i, :]
            break
        X[i, :] = spl(idxx)
    return X
```
#### Varying Parameters for Sliding Window:
- $\tau$ - increasing leads to a bigger sliding window, decreasing leads to a smaller sliding window
- Dimensions - increasing leads to a bigger sliding window, decreasing leads to a smaller sliding window
	- For a fixed $\tau$, the eigenvalues are closest to each other (circle is perfect), when the end of the sliding window reaches the amplitude of the signal
	- This means that the period length is going to be $\tau*dim$, when this leads to a perfect circle with the sliding window
- $dT$ - Increasing leads to more points in the PCA, decreasing leads to less points in the PCA
#### Sliding Window + PCA + Persistent Homology
- We can create a sliding window on the sinusoid, create the PCA graph from it, and then run Persistent Homology on the PCA to see the shape of the data
- 