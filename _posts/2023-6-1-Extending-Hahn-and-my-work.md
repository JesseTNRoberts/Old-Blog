## Extending the first paper


Hahn shows that one can apply input restrictions to hard attention transformers such that Parity is unrecognizable in a single feedforward pass regardless of the number of layers. His construction can be shown more simply by appealing to the size of the embedding used to present data to the FFN. 

Consider, if an embedding is used such that it has only $c$ bits yet the input to the attention layer has $n$ values in the sequence, each encoding a binary value, then at most $2^c$ values may be losslessly compressed into the input of the FFN. Therefore, in the case of feedforward, single pass recognition of parity via soft attention, parity is not recognizable if $n > 2^c$. 



