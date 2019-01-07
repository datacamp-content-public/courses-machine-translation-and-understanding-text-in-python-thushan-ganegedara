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
Hi, in this lesson, we will be exploring some general ideas around word vectors; a powerful numerical representation of words that is ubiquitously used for natural language processing tasks.


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
What are word vectors?

As mentioned earlier, word vectors are numerical representations of words. For example, the word vector of the word cat might look like this; a fixed length vector of real numbers.

More importantly, word vectors preserve the semantics of words as the words are mapped to the vector space.
 
Take a look at the image below. If you imagine a 3 dimensional space to which the words are mapped, the word vectors might be positioned as follows.

The word cat will be very close to the word dog, however far away from the word volcano.


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

Doesn't capture the any concepts{{1}}

![Naive representation](https://assets.datacamp.com/production/repositories/4386/datasets/d2fabb11480b7f756f3625919c6c56245d1a3333/ch1_naive.png){{1}}


`@part2`
When word vectors are used,{{2}}
* cat = (0.52, 0.02, 0.49){{2}}
* dog = (0.49, -0.05, 0.4){{2}}
* volcano = (1.09, -0.45, -0.87){{2}}

Cat is very similar to a dog, but very different from a volcano{{3}}

![Word vector representation](https://assets.datacamp.com/production/repositories/4386/datasets/959912f00dd79ae4e8321ef56863ce3ab98b6635/ch1_wordvec.png){{3}}


`@script`
Now you know what word vectors capture. But why do we need such powerful representations of words?

Why not use a naive representation?

For example, let us represent the words cat, dog and volcano as follows, where each number corresponds to the alphabetical index of each letter in the word, such as 3 for the third letter c, 1 for the first letter a, and so on.

This representation does not help computers to infer additional information given the data.

Now think about the following representation, where the words cat, dog and volcano are represented with word vectors.

This allows the computer to understand the concepts or semantics of the words. Now the computer knows, cat is very similar to a dog but very different from a volcano. 

Such a representation is very powerful and enables us to solve very complex NLP problems much more effectively. This is because the behaviour of the machine learning model will be tightly coupled with the meanings of the words. For example, when the model is looking at similar words, the model will experience only a slight change in the input, and vice-versa. 

We now know the general concept behind word vectors and why they are important. Now let us see how word vectors can be derived.


---
## How are word vectors learnt?

```yaml
type: "FullSlide"
key: "8e4a99ea2a"
```

`@part1`
> You shall know a word by the company it keeps - J.R. Firth{{1}}

**Example:** {{2}}

John is a stubborn boy. His pervicacious nature always gets him in trouble{{2}}

* What does "pervicacious" mean?{{2}}


`@script`
All word vector algorithms rely on a fundamental characteristic of language, which is captured in the following statement. 

"You shall know a word by the company it keeps"

This was uttered by J.R. Firth a famous British linguist.

Let us put this statement to test. Can the meaning of a word be derived from its context? Consider the following sentence.

John is a stubborn boy. His pervicacious nature always gets him in trouble.

Assume someone asked you what "pervicacious" means? Unless you know the meaning, you would automatically start looking at the context words of the word "pervicacious". You will see that words like "stubborn" and "trouble" are present in the surrounding. Which tells you that "pervicacious" means "being stubborn".

Word vector algorithms exactly uses this information. For example, the skip-gram algorithm tries to predict all surrounding words of a given word, using a neural network.


---
## Let's practice!

```yaml
type: "FinalSlide"
key: "238fd42a15"
```

`@script`
In this lesson you learnt why word vectors are important, and the underpinning idea on which word vector algorithms are built. In the next lesson we will learn about two popular word vector algorithms, known as skip-gram and continuous bag-of-words.

