**Natural Language Processing Proposal**

Toki Pona is a constructed language with a limited vocabulary of 120 words. This effectively allows us to ignore some aspects of the sparsity problem, as even the least used items and structures will still pop up enough for us to evaluate it. The limited vocabulary also puts a much higher load on pragmatic interpretation of the sentence, as the literal reading may not be so useful.

For my project, I will first do a preliminary analysis of the corpora to see if we still see the general statistical trends we expect from true natural languages. I’ll look at word counts, n-grams, and peek at structure. There’s not that much literature for Toki Pona, but this has already been worked on so I’ll mostly be reproducing results. This is also important to have enough background to evaluate how good the later results are.

For the data, I will use the poki Lapo corpus, possibly supplemented with David A. Robert’s fork of a Toki Pona corpus or Tatoeba. Datasets for Toki Pona are generally quite small, and while the quality of the data is decent, there is some cleanup to be done, mostly to remove chunks of English such as dates or links. Given the small vocabulary and limited grammar, there should be enough occurrences for a model to see everything at least a few times.

Transformer models, based on or modifications of the most current architectures, have been proven to be capable at translation and generation for both constructed languages and low resource languages. However, given the limited vocabulary, I want to compare how good older, simpler models are, when largely freed from the sparsity problem.

I’ll make an N-gram model, and see how well it performs. I will compare it to N-gram models for English. Optimistically, I will also make a generative model using Zach Tomaszweski’s grammar and parser by parsing the data and assigning weights to the options for each rule.

Since N-grams are already provided in the dataset, I’ll compare how well N-grams of size 1-4 against each other. I’ll hold out part of the dataset and use the cross entropy, or a similar metric which measures how likely predictions are to be correct. I will also generate a few sentences to subjectively evaluate.

Evaluating a language model that generates whole sentences is more unusual, so I’ll settle for just generating a lot of sentences and evaluating them subjectively. I can also collect general statistics about them, and see if it follows the same patterns as the general dataset. While it is weighted to approximate the dataset, it may deviate in unexpected ways. Since it is weighted, it can also predict the most likely parse for sentences with multiple parses (which is most sentences in Toki Pona).The model can be evaluated by checking how often it is able to predict the correct parse.

**Sources/Links**

Toki Pona Corpus
https://github.com/kulupu-lapo/poki/tree/main
https://github.com/davidar/nltk-tp/
https://tatoeba.org/en/audio/index/tok
https://huggingface.co/datasets/SzuTao/Tokie_Pona_Language

Zach Tomaszewski’s Grammar
https://www2.hawaii.edu/~chin/661F12/Projects/ztomaszewski.pdf

Toki Pona Transformer Translator
https://huggingface.co/ckb/en-toki-mt

Toki Pona Language Model
https://github.com/adam-mcdaniel/toki-pona-language-model/
