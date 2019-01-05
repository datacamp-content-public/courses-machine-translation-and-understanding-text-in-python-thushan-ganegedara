---
title: Insert title here
key: e493fe72b09a643d6cc7f8e7b6c447bb

---
## Introduction to word vectors

```yaml
type: "TitleSlide"
key: "638a28e7ca"
```

`@lower_third`

name: Thushan Ganegedara
title: Data Scientist


`@script`



---
## What are word vectors?

```yaml
type: "FullSlide"
key: "656785e824"
center_content: false
```

`@part1`
* numerical representations of words
 * cat = (0.52, 0.02, 0.49){{1}}
* captures meaning of words

![Word vectors](https://assets.datacamp.com/production/repositories/4386/datasets/829e90fa86a977034294f7e6fe205f703574cc86/word_vectors_general.png){{2}}


`@script`



---
## Why word vectors?

```yaml
type: "TwoColumns"
key: "bc8685959f"
```

`@part1`
Why not use a naive representation like,
* cat = (3, 1, 20)
* dog = (4, 15, 7)
* volcano = (22, 15, 12, 3, 1, 14, 15)

Doesn't capture the any concepts

![Naive representation](https://assets.datacamp.com/production/repositories/4386/datasets/d2fabb11480b7f756f3625919c6c56245d1a3333/ch1_naive.png)


`@part2`
When word vectors are used,{{1}}
* cat = (0.52, 0.02, 0.49){{1}}
* dog = (0.49, -0.05, 0.4){{1}}
* volcano = (1.09, -0.45, -0.87){{1}}

Cat is very similar to a dog, but very different from a volcano{{2}}

![Word vector representation](https://assets.datacamp.com/production/repositories/4386/datasets/959912f00dd79ae4e8321ef56863ce3ab98b6635/ch1_wordvec.png){{2}}


`@script`



---
## How are word vectors learnt?

```yaml
type: "FullSlide"
key: "8e4a99ea2a"
```

`@part1`
> You shall know a word by the company it keeps - J.R. Firth


John is a stubborn boy. His pervicacious nature always gets him in trouble{{1}}

* What does "pervicacious" mean?{{2}}


`@script`



---
## Final Slide

```yaml
type: "FinalSlide"
key: "238fd42a15"
```

`@script`


