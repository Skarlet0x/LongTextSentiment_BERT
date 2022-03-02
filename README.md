# LongTextSentiment_BERT
A pretrained BERT model for longer reviews

## PRETRAINED MODEL

SOURCE: https://huggingface.co/aychang/roberta-base-imdb

- the most downloaded TextClassification model trained in an IMDB dataset - reported to have 94% accuracy
- although I prefer using TensorFlow, there were no pretrained models for it, so I was forced to work with PyTorch

## BATCHING

- since BERT has a limit of 512 tokens per instance, this presents a real limitation on sentiment analysis for anything longer than a Tweet, as the default truncation implemented during the tokenization phase results in a massive loss of data 
