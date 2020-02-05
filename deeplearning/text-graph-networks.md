Would be interesting to set up the following toy problem:

 - Given some corpus of linked documents (such that the is a graph with edges between documents)
 - Feed in the text of those documents into some graph-producing model
 - Compute loss based on how well we estimate the graph from the text alone (can be done with transformer or something like that)

Lots of datasets exist to compute this. Wikipedia would be a good start, or other interlinked web pages. It would also
be interesting to see what documents the model *thinks* are linked together based on a probabilistic model.
