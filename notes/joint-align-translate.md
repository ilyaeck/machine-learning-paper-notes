# Neural Machine Translation By Jointly Learning to Align and Translate

### The pitch
Prior encoder-decoder (seq2seq) approaches translation have a major bottleneck: input sequences must be
squashed into a fixed-length vector. This translations to break down for long sentences. Here, *attention* comes to resque
and removes the fixed-length constraint.

### General idea
OK, if straightforward seq2seq approach is not great for long sentences, how to we do better? 
First, consider what it means to learn sentence translation from examples. The problem can be seen as a combination of two subproblems: (a) word alignment: given a sentences and its translation from language A to B, compute an alignment scoring matrix measuring the "relevance" of each word in A to each word in B (in a given local _context_); and (b) given a good aligment scoring function, actually compute the best alignment. If we can do both (a) and (b), we should be able to translate sentences, but it's a chicken and egg problem! Since we start with only examples (no dictionary), we don't really know the words' meanings to tell if a given word alignement is good or bad. Converseley, given an alignment scoring function, we have a good chance of funding an optimal sentence alignment e.g., using gradient descent (read: back-propagation). 

### Method
The idea is simple: while the prior standard *RnnEncDec* technique explicitly conditions the output only on the prior state (a function of the prior input and output), *RnnSearch* conditions each output on the entire input (indirectly, via an attention distribution). 

* With *RnnSearch*, he outputs _y_i_ are generated (one at a time) according to the following distribution: 
![equation](https://ibin.co/2urAgk0zuIsS.png) where the key novelty is in the new context term _c_i_. 
* The context vector _c_i_ is a weighted sum of _annotations_ _h_j_ which are the encoder's output. So unlike with RnnEncDec, the entire input sentence has to be read before we can start generating outputs.
* The weights are essentially the *attention* are based on a separate (soft) alignment model ![equation](https://ibin.co/2urN3EivuVl4.png) that measures how well input[_i_] matches output[_j_]. So, instead of generating the next word's translation based on the input and output seen/generated so far, we have these attention weights highlighting the parts of the input that ought to be translated next (but still given the context)!
* The alignment model is a separate feed-forward (FF) neural net (NN), learned jointly with the rest of the components, yielding an end-to-end trainable network. 

### Results
Beats prior RnnEncDec art and is on par with the state-of-the-art Moses system that uses an additional large monolingual corpus (not used in this work).

![figure](https://ibin.co/2url159iHFC2.png)
