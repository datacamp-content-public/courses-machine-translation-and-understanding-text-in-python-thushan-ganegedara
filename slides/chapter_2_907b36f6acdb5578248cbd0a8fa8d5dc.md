---
title: Insert title here
key: 907b36f6acdb5578248cbd0a8fa8d5dc

---
## Implementing an encoder-decoder model

```yaml
type: "TitleSlide"
key: "82c07b1839"
```

`@lower_third`

name: Thushan Ganegedara
title: Data Scientist


`@script`
In this lesson, you will learn how to implement an encoder decoder model for machine translation, using keras functional API.


---
## Recap - Encoder Decoder Model

```yaml
type: "FullImageSlide"
key: "a1cf58d984"
```

`@part1`
![Encoder decoder model](https://assets.datacamp.com/production/repositories/4386/datasets/1d8e11ffdf7357d7fbd2e00ffd4468bf220896a8/encoder_decoder_model.svg)


`@script`
But, before jumping into implementation details, let us revisit what architecture of an encoder decoder model is. 

First the encoder takes a source sentence and converts it to a consice representation, represented by the final states of the encoder). Then the decoder takes in this representation and generates the translated sentence.

Next, let us examine the implementation details of the encoder decoder model. You will first learn how to implement the encoder, then the decoder and finally the full model.


---
## Implementing the Encoder

```yaml
type: "TwoColumns"
key: "3b12b965ca"
center_content: false
```

`@part1`
![Encoder](https://assets.datacamp.com/production/repositories/4386/datasets/5d8dc8063d9e5826e9f02c8cade7148187b70845/encoder.svg)


`@part2`
```
encoder_inputs = Input(
    shape=(en_seq_len, en_vocab), 
    name='encoder_inputs')

encoder_lstm = LSTM(
    latent_dim, return_state=True, 
    name='encoder_lstm')

encoder_outputs, state_h, state_c = 
    encoder_lstm(encoder_inputs)
```{{2}}


`@script`
Implementing the encoder is very straight forward. The encoder has three main components:
* The encoder input
* A sequence of LSTM cells
* The context vector

You will be using the layers provided in the tf.keras.layers package. The image on the right shows some of the usages of these layer objects. First you define an input layer. Input layer is essentially a batch of sentences, where each sentence is a sequence of words and each word is represented as an one-hot encoded vector. Specifically, the input layer will hold a 3-dimensional tensor of shape <batch_size, number of words in a source sentence after padding denoted by en_seq_len, source vocabulary size denoted by en_vocab>. Note that when defining the shape argument of the input layer, you do not specify the batch size.

Then a sequence of LSTM cells is defined by the LSTM layer. The parameter latent_dim defines the number of hidden units in a single LSTM cell, return_state=True means that the LSTM cell will also output state values in addition to the output. Then the final line computes the output of the LSTM using the input layer.


---
## Implementing the Decoder

```yaml
type: "TwoColumns"
key: "4504b15e2f"
```

`@part1`
![Decoder](https://assets.datacamp.com/production/repositories/4386/datasets/765b532d02d8c14baad0e9e6b345c13bf346ac8b/decoder.svg)


`@part2`
```
decoder_inputs = Input(
    shape=(fr_seq_len, fr_vocab), 
    name='decoder_inputs'
)

decoder_lstm = LSTM(
    latent_dim, return_sequences=True, 
    return_state=True, name='decoder_lstm'
)
decoder_lstm_outputs, _, _ = 
    decoder_lstm(
         decoder_inputs, 
         initial_state=encoder_states
    )

decoder_dense = Dense(
    fr_vocab, activation='softmax', 
    name='dense'
)
decoder_outputs = decoder_dense(
    decoder_lstm_outputs
)
```{{2}}


`@script`
Let us now analyse the decoder. The decoder is a bit more complex than the encoder. However the decoder can be summarized to three compoents as well:
* The decoder input
* A sequence of LSTM cells and their outputs
* A softmax layer and its output 

First you define a decoder input similar to the encoder input, however the shape would be <batch_size, target sentence length after padding, target vocabulary size>. Then an LSTM layer is defined similar to the encoder_lstm but you set the return_sequences argument True. This will make sure that you will get all the outputs produced by each LSTM cell, instead of just the final output. When computing the LSTM output, you set initial state to be the final state of the encoder using the inital_state argument. This output is next fed to a dense layer, which acts as a softmax layer to produces the final prediction, recoded in the variable decoder_outputs.


---
## Defining the Final Model

```yaml
type: "FullCodeSlide"
key: "a1b03662fa"
```

`@part1`
```
model = Model([encoder_inputs, decoder_inputs], decoder_outputs)
```{{1}}


`@script`
Finally you can define the full model. To define a model with the functional API you use the Model object and define inputs and outputs of the model. At runtime, you will feed in the actual data. Inputs are source sentences and target sentences, where the output is the target sentences with words offset by 1.


---
## Let's practice!

```yaml
type: "FinalSlide"
key: "c1fbf1dc47"
```

`@script`
Now you have learnt how to implement an encoder decoder model using the keras functional API. Let us know practice what you learnt by training the model on some data and predicting from it!

