## DD Transformers


Dual Decoder transformers use self-attention and cross-attention to permit distinct discourse and deliberation. This provides a theoretical capability of seq2seq modeling while also permitting potential Turing completeness. 

DD transformers may operate as either half-duplex or full duplex models. That is, one side of the model can be held static with no changes in attention while the other is generating (half-duplex). Or, the model can be executed so that after every generation, the cross attention is reevaluated in the opposite decoder, leading to a change in attention (full-duplex). 

Half-Duplex DD transformers can be approximated via a pair of traditional encoder-decoder models coupled with an appropriate execution algorithm. The decoder of each transformer is, at each time step, copied into the encoder of the other model. This assumes that the encoder has shared weights with the encoder. This is not suitable for approximation of the full duplex model.  



