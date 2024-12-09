# ABSA_VLSP2018
Aspect-Based Sentiment Analysis (ABSA) for hotel's reviews in Viet Nam using PhoBERT

Example: Hơi xa trung tâm, bãi biển không được đẹp lắm. Tiện nghi khách sạn đầy đủ. Nhân viện thân thiện vui vẻ. Xung quanh khách sạn khá yên tĩnh, không đông vui cho lắm
=> {LOCATION#GENERAL, negative}, {FACILITIES#GENERAL, positive}, {SERVICE#GENERAL, positive}

You can see my solution in Kaggle: https://www.kaggle.com/code/duongquanganh/absa-vlsp2018-solution.

The dataset and my reference is from : https://github.com/ds4v/absa-vlsp-2018.

My solution includes 5 parts:
1. Preprocessing:
   + Convert raw data into a DataFrame with three columns: comment, aspect, and sentiment.
   + Use vncorenlp for segmentting words in comments.
   + Aspects have 34 unique values and sentiment has 3 unique values so with each comment, I encode aspects and sentiment accordingly to (34,4) np.array.
   + This is 4 with 3 representing sentiment labels (positive, negative, neutral) and 1 for aspect absence.
2. Fine-tune model
   + I use tokenizer and model of PhoBERT-base.
   + I reference hyperparametes of Trainer from: https://github.com/ds4v/absa-vlsp-2018.
3. Test with test_dataset
   + Predict aspect-sentiment labels for unseen hotel reviews in the test dataset.
4. Evaluation with test_dataset.
   + Measure performance on 600 test samples.
   + Analyze performance for individual aspects in the hotel domain.
5. Input your comment and try
