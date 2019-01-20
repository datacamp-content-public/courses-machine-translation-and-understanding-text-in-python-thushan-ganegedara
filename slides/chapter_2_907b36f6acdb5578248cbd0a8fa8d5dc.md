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



---
## Recap - Encoder Decoder Model

```yaml
type: "FullImageSlide"
key: "a1cf58d984"
```

`@part1`
![Encoder decoder model](https://assets.datacamp.com/production/repositories/4386/datasets/1d8e11ffdf7357d7fbd2e00ffd4468bf220896a8/encoder_decoder_model.svg)


`@script`



---
## Implementing the Encoder

```yaml
type: "TwoColumns"
key: "3b12b965ca"
```

`@part1`
![Encoder](https://assets.datacamp.com/production/repositories/4386/datasets/5d8dc8063d9e5826e9f02c8cade7148187b70845/encoder.svg)


`@part2`
```
encoder_inputs = Input(
    shape=(en_seq_len, en_vocab), 
    name='encoder_inputs'
)

encoder_lstm = LSTM(
    latent_dim, return_state=True, 
    name='encoder_lstm')

encoder_outputs, state_h, state_c = 
    encoder_lstm(encoder_inputs)
```{{2}}


`@script`



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



---
## Let's practice!

```yaml
type: "FinalSlide"
key: "c1fbf1dc47"
```

`@script`


