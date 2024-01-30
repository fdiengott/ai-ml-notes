A graph of Cost, $J(\vec{w},b)$ vs number of gradient descent iterations
where the y-axis is cost and the x-axis is # iterations

Plot the chart to figure out if the current learning rate is too large (if the cost increases) or too small (takes too many iterations to converge)

A good debugging tool for finding a good learning rate ($\alpha$) is to plot this chart for just a few iterations and see if it is consistently decreasing the cost or not. Find a learning rate that is too small, then increase by a factor of 3 or so until a rate too large is found. Then decrease until a value is found that both decreases the cost quickly and consistently