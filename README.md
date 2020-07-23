# GraphGRU
GraphGRU.ipynb is a Jupyter python file for a customized layer in the Keras/Tensorflow format.
The code takes a graph, represenetd as a list of tensors, and combines it with a memory vector
and produces an output memory vector. Various learnable matrices are introduced to couple the
memory to the vertices and to the edges of the graph.

Introduction
The purpose of this document is to generalize the structure of a GRU recurrent unit –  which generally combines an input vector at time t with a memory vector at time t-1 to produce a memory vector at time t (see figure 1) – to a model which combines a graph at time t with a memory vector at time t-1 to produce a memory vector at time t. The generalization is based on the observation that all recurrent memory cells (even a simple RNN) combine the incoming memory and the incoming input linearly to produce the outgoing memory. Thus, every component of the new memory is a linear combination of all of the old memory components and all of the input components. With a graph it is only necessary to enumerate all of its components and define weights that map each to the new memory components.
The objective is to design a model architecture which preserves the graph structure created with the similarity and spatial edges and to analyze their time-dependence by inputting each graph at each time t into a GRU unit in the same way that sequences of vectors are time-analyzed.
The problem is complicated somewhat in that the elements of a graph are edges (which can be thought of as matrices of real numbers) and node (or vertex) labels. The labels are themselves vectors representing the node features (e.g. “boy,” “trampoline,” etc.). Thus it is useful (for writing clarity) to calculate node and edge influences separately. Similarly, since there are two types of edges (meaning that the edges carry a label) we must define separate weights for each type (although we could possibly share weights to see if that works).

