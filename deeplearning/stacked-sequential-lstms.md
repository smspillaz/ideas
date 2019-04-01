# Stacked Sequential LSTMs

In a normal LSTM each layer in time only depends on the previous layer at the previous
timestep.

   o <-- o <-- o

In principle, an LSTM should be able to remember long term dependencies through the
operation of its forget gates, but its memory is still effectively limited by the
hidden layer size and by the fact that the forget/update gates only mitigate the
vanishing gradient problem but don't actually eliminate it alltogether.

One thing that LSTMs do allow us to do is stack layers when processing the sequence, eg:

   o <-- o <-- o
   ^     ^     ^
   |     |     |
   |     |     |
   o <-- o <-- o

In principle this should allow us to extract more information from the hidden states by
encoding non-linear features into them (in the sense that we have hidden-states of hidden
states). But the hidden states are only derived from those hidden states themselves

In the attention model we take all the hidden states, then multiply each by some attention
weights and softmax the result into a probability distribution such that we know
which states to pay attention to the most when doing some task over all the hidden states:

   h_1 --|
         |
   h_2 --(x) Wa => softmax([a_1, a_2, a_3])
         |
   h_3 --|

This allows us to "shortcut" back to the various hidden states through the attention operator
without having gradients be lost in the backpropagation phase for very long term dependencies. This
makes sense for machine translation where we only need to understand the sentence in order to be able
to translate it, but only kind of works for document understanding.

However, this approach depends only on the hidden states where each timestep exists at the unit-level.
But words/subwords/characters are not the only atoms in a sequence. For instance, you can have a
meta-structure, like a sequence of subwords from a sequence of characters, a sequence of words from
subwords, a sequence of sentences from words, a sequence of paragraphs from sentences, etc.

So, we could model that latent document structure as well:

    sow <-- c <-- a <-- t <-- sow <-- d <-- o <-- g <-- sow
     ^                         |                         |
     | Wa => softmax -> concat | Wa => softmax -> concat |
    hw0 <-------------------- hw1 <-------------------- hw2

(continue for sentences, paragraphs etc).
