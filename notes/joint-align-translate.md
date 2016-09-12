# Neural Machine Translation By Jointly Learning to Align and Translate

### The pitch: prior encoder-decoder (seq2seq) approaches translation have a major bottleneck: input sequences must be
squashed into a fixed-length vector. This translations to break down for long sentences. Here, *attention* comes to resque
and removes the fixed-length constraint.
http://latex.codecogs.com/gif.latex?%5Cdpi%7B120%7D%20s_i%20%3D%20f%28s_%7Bi-1%7D%2Cy_%7Bi-1%7D%2Cc_i%29

*
