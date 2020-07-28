# hate_speech_classifier
Dataset Link: https://github.com/aitor-garcia-p/hate-speech-dataset

Goal: Classify hate speech dataset from white supremacist forum
- Generate dataset insights (ex. Class Distribution, Most Common Words, Highest TF-IDF Weightings, etc.)
- Clean Data (ex. Standardize numbers/dates/links, perform stemming)
- Benchmark various models, and compare them to the Majority Class

Results/Observations:
- Logistic regression appears to perform better than the svm
- In general, the incorrectly classified posts don't have any of the preprocessing symbols (except number), which suggests the preprocessing is helping
    - Often, the language used in these are less specific (ex. dark skinned beings)
    - In general this stuff is still subjective: Test index 157: Guess: 0.0 Act: 1 Post: "it s just the way they are ."
    - Snowball stemmer helped a fair bit (makes sense since theres not much data, and some of the words could be hidden in their plural forms)
        - Logistic Regression Results (It changes depending on what split you get, but the performance improvement is often there):
            - With Stemmer: 0.7594142259414226
            - With stemmer but removing stopwords: 0.7196652719665272
            - No Stemmer: 0.7238493723849372
    - NLTK lemmatizer didnt work as well... probably because it doesnt do that well with handling unknown words, and its results depend on context
