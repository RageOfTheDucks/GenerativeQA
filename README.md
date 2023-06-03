# GenerativeQA

Text Mining project on generative QA in low performance environments

---

## Model

During the NLP course we had to produce, unsing the Hugging Face transformers library, a simple Open Generative Question Answering (QA) model. The task was also constraint in using a specific transformer-based model, limiting the possible approaches. At the end, general results were not great, leading me in wanting to try different approaches to better understand this complex subject.

Dataset used: **CoQA**

Approaches:

- Reference model: T5
- Ensamble model

  The base idea is to decompose the problem into two main branches of questions: yes-or-no questions and open questions. In yes-or-no question it would use a BooleanQA approach, while in open questions it would use in sequence an ExtractiveQA model and then a generative text-to-text model to better structure/generate the answer.

---

## Results analysis

### T5

- mean F1:  54.72581772847185

- mean EM:  43.9

- Total Time = 2751s | 46m

### Ensamble

- mean F1:  55.44076754686662

- mean EM:  44.2

- Total Time = 4550s | 1h 15m

### Simple Encoder-Decoder (previous project)

- mean F1:  0.14790483405483407

- Total Time = 2453s | 41m

---

## Comments

At the end, performance were particularly similar, having the ensamble being effectively a bit more accurate.

However, this result does not prove that this ensamble could actually outperform the original T5 approach, since the two network had different training time.

We had to limit the subset of samples on the T5 approach due to the limitation of our environment but, nevertheless, it managed to achieve similar high performance with more samples and less training time with respect to the Extractive QA.

The most computational demanding part of the ensamble was the Extractive QA part, which required the most amount of training and inevitably was the main responsable for the ensamble performance.
