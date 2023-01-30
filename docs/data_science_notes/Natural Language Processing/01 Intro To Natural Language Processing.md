---
sidebar_position: 1
---

# Intro To Natural Language Processing

Natural Language Processing deals which computation to understand human languages better and apply computing resources for various tasks. In this introduction, we will be dealing with the famous `NLTK` library to perform some NLP tasks.

## Loading The Example Text Corpus

Once you have installed NLTK, you can load the book text corpus and play around with it. It contains fairly large text examples as seen below. 

### Loading The Text

You can load the texts and the associated functions as below:

```python
from nltk.book import *
```

This will load a bunch of text, contained in variables from `text1` to `text9`. You will be able to see a brief description of the text as the library loads. 

### Searching Text

You can apply some search methods as below:

`concordance`: Find direct matches of a word and find the surrounding sentence. 

```python
text1.concordance('monstrous')
```

The output will be as below:

![](../../assets/Pasted%20image%2020230130202217.png)

You can also get the output as a list with the `concordance_list` function. 

`similar`: You can also get similar words. NLTK uses statistical analysis to find similar words. 

```python
text4.similar('nation')

# country people government world union time constitution states ...
```

`common_contexts`: find common contexts of two words:

```python
text4.common_contexts(['this', 'nation'])

# and_we and_the
```

`dispersion_plot`: We can use this to see how particular words have appeared in the text:

```python
text4.dispersion_plot(['citizens', 'democracy', 'freedom', 'duties', 'America', 'liberty'])
```

![](../../assets/Pasted%20image%2020230130202608.png)

`generate`: This generates some sentences using statistical tools, although, it's not that good. 

```python
text4.generate()
```

![](../../assets/Pasted%20image%2020230130202706.png)

### Counting Words

Like normal python, you can use `len()` to count words in an example. You can also use functions such as `set` to count the unique words in a text. Using both these methods, we can find the *lexical richness* of the text, i.e. the average number of times a word has appeared.

```python
len(text4) / len(sorted(set(text4))) # lexical richness of the text, find average times a word has been used
```

You can also find the lexical diversity percentage of the word, by using the `count` function to see the percentage of the word that has appeared in the text. 

```python
def lexical_diversity_percentage(word, text):
    word_count = text.count(word)
    return 100 * (word_count / len(text))
```

Using `FreqDist`, we can find the frequency distribution of the words and draw a plot of that. 

```python
fdist4 = FreqDist(text4) # find frequency distribution of the words
vocab4 = fdist4.keys() # get the keys of the dict
fdist4.plot(50, cumulative=True) # plot the words in a graph cumulatively
```

![](../../assets/Pasted%20image%2020230130203510.png)

Hapaxes are not so frequent words in the text corpus, we can find that using the `hapaxes()` function. 

Since we have the text as an iterable, we can iterate over it like a list and do various things, such as finding really long words.

```python
long_words4 = [w for w in text4_words if len(w) > 15] # find long words
```

Or not short and not too long words

```python
not_short_long_words = [w for w in text4_words if len(w) > 7 and len(w) < 15] # find not short and not long words
```

Collocations are words that appear together, we can also find them using the `collocations` function. 

Using these tools, we can also find the length of the words and its distributions.

```python
word_lens = [len(w) for w in text4]
FreqDist(word_lens).items()
```