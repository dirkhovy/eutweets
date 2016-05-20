# eutweets

In order to make the processing efficient and feasible, everything is broken up into parts.
First, compute an adjacency map and the regions for the grid size you want (i.e., the fraction of a lat/lng square to be taken as minimum unit to aggregate counts over). This data will be used by all other programs to avoid costly re-computation. You need to set the grid size, the rest has default values:
python src/compute_adjacency.py --country eu --coord_size 0.2 --num_neighbors 5 --prefix lib/

Then, run the vocab collection (sparse matrcies) on each JSON file:
python compare_regions_MAP.py --coord_size 0.2 --twitter <SOME_JSON_FILE>
This step will try to find an adjacency and regions map matching the country and coordinate grid size and otherwise throw an error. It goes over the data and extracts character n-grams.

Finally, collect all those counts, compute distributions, and run agglomerative clustering (this is not complete yet). It should read in the output of the two previous steps.
TODO: make this part work
