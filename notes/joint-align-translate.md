# Neural Machine Translation By Jointly Learning to Align and Translate

### The pitch
Prior encoder-decoder (seq2seq) approaches translation have a major bottleneck: input sequences must be
squashed into a fixed-length vector. This translations to break down for long sentences. Here, *attention* comes to resque
and removes the fixed-length constraint

### Method
The idea is simple: while the prior standard *RnnEncDec* technique explicitly conditions the output only on the prior state (a function of the prior input and output), *RnnSearch* conditions each output on the entire input (indirectly, via an attention distribution). 

* 

![equation](https://ibin.co/2urAKszMkZRc.png)

*
