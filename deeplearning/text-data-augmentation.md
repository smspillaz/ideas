# Text Data Augmentation
There's not much out there to do data augmentation on text data, yet so much of the text data
that people work with is either quite biased or quite sparse.

## Substitution via  paraphrases

If we we want to be invariant to who is speaking, we can use a paraphrase corpus along
with the sentence parse tree. Basically the only thing is that you have to get the parse tree
right - you can probably augment sentences where the parse tree probability is fairly high.

## Substitution via entity recognition

If we don't care about what specifically is being talked about in some text but only want to
classify somethign like sentiment, we can augment the data by retraining an entity recognizer
and then generating new text by swapping entities of the same type. For instance, if we were
to develop a hate speech detector, we probably don't want it to latch on to particular names,
so it makes sense to use lots of different names.

## Substitution with seq2seq Autoencoders

Try to train a model to find a latent variable for generating text from that distribution. This
will probably generate different text from what we had before.

Need some way of validating the generated text, otherwise it could be rubbish.
