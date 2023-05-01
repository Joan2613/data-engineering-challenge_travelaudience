## Decisions
There were 3 different versions of the program, however the implemented one was the fastest of all:
* At the beginning we were thinking about using geopandas, however the time to preprocess the dataset to a suitable format (shape file or something similar) was high so initially we discarted the idea.

* The first method was a brute force implementation. In all cases we tried to use the best metric to calculate distances on the globe using latitude and longitude. For this particular case was the Haversine metric. We used the package with the same name in order to calculate it and then we got the one with minimum value. Howeber it is clear that this approach is not functional because if we compare each dataset we will have (# airports) * (sample size) comparisons.

* The second idea was to prioritize 5 points using a normal euclidean metric and afterwards using the more refined metric. For this case, the priorization was done using a clustering algorithm called KDTree. Nevertheless, the time to process 1000 datapoints was 2 seconds, so slower than the required processing time.

* Finally, we opted to employ a clustering algorithm (Ball Tree) with the haversine metric in order to prioritize the first result. Initially we used the apply method to go row by row, but the function was faster when applied overall. 

## Trade offs

The main trade off was speed. We thought about using an euclidean metric in order to simplify times and give good accuracy (some errors) calculating the closest airport because sometimes the euclidean metric fails to capture the real distance when working with latitudes/longitudes. 

We opted for the Haversine metric, however to reduce times it is possible to change it to euclidean

For now, the running times are:
* The code runs in 112 ms for 1000 data points.
* In one second it can process around 15000 datapoints.
* The complete dataset is runned in approximately 58 seconds.



