A Decomposable Attention Model for Natural Language Inference
Ankur P. Parikh et al., Google

The pitch: a simple attention-based neural architecture for NL inference that yields state of the art results (on SNLI data) 
with less network complexity. Also, easy to parallellize. <br>

The task: Natural Language Inference, i.e., given a pair of sentences A and B, determine if A entails, contradicts or 
is neutral w.r.t. B.  <br>

Example:
1. Bob is in his room, but because of the thunder and lightning outside, he cannot sleep.
2. Bob is awake.
3. It is sunny outside.

(1,2) ==> entailment; (1,3) ==> contradiction 



Approach in a nutshell: sentence-level NLI ==> (soft) sub-phrase alignment + synonym/antonym determination. In a way, 
the claim is that the task is akin to translation from A to B.  <br>

The insight: at least for SNLI, pairwise comparisons are more inportant than global sentence-level representations.  

### Method 






