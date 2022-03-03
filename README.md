# LongTextSentiment_BERT
A pretrained BERT model for longer movie/series reviews

## PRETRAINED MODEL

SOURCE: https://huggingface.co/aychang/roberta-base-imdb

- the most downloaded TextClassification model trained on an IMDB dataset - reported to have 94% accuracy
- although I prefer using TensorFlow, there were no pretrained models for it, so I was forced to work with PyTorch

## BATCHING

- since BERT has a limit of 512 tokens per instance, this presents a real limitation on sentiment analysis for anything longer than a short Tweet, as the default truncation implemented during the tokenization phase results in a massive loss of data 
- to avoid this, we can chunk longer texts into shorter instances - in our case, we wanted to go with the maximum allowed size od 512 - each of which is passed to our model as separate inputs, and is scored independently
- the assumption is that an average of the individual sentiment scores would be the correct overall sentiment of the entire text
- with our example, an interesting thing happened - when reviewing the individual sentiment scores, it turns out that the beginning and the end of the text containted an overwhelming majority of positive sentiment, but there were some convincingly negative things said in the middle, however - the overall sentiment still turned out to be positive - which we assume is the correct evaluation
