# Analysis of Instagram posts (pictures) using Google Vision API

## 1. Introduction
As a social media analytics consultant, understanding what drives engagement is crucial to provide useful insights for influencers and brands looking to post engaging content on social media. This project focuses on analyzing Instagram post data, particularly the images posted, to identify which type of content tends to increase and decrease user engagement. 

By applying topic modeling using Latent Dirichlet Allocation (LDA), to the labels derived from Google Vision API on Instagram images, the content is categorized into distinct themes. The analysis aimed to identify patterns in engagement across these themes, providing actionable insights that could help an influencer enhance their strategy and increase interaction on their social media content.

## 2. Data Preparation
The dataset from [Kaggle](https://www.kaggle.com/datasets/thecoderenroute/instagram-posts-dataset?resource=download) has information about 2,000 instagram posts from different accounts. The dataset includes the image posted, the number of likes and comments, the caption accompanying the post, and the follower count of the respective accounts. The initial step in data preparation involves extracting the necessary information from the data, which is stored in JSON format. This extraction is done using the Python package Instaloader. Following this, the next step is to annotate the images with descriptive labels. For this purpose, the Google Vision API is used, which analyzes the images and returns a set of relevant labels, which are used for further analysis. The text generated is preprocessed by removing stopwords and punctuations, lemmatization and tokenization to prepare them to be used as input for topic modeling.

## 3. Topic Modeling
The first step is to apply Topic Modeling using Latent Dirichlet Allocation (LDA) on the image labels returned from Google Vision API. Using Coherence score as the metric, the optimal number of topics for this analysis was found as 7. The table below provides the list of topics and the top keywords associated with each topic:

| **Topic**                      | **Top 25 Words**                                                                    |
|-------------------------------|-------------------------------------------------------------------------------------|
| Formal Events and Fashion     | fashion, design, sleeve, event, formal, wear, font, smile, blazer, collar, shirt, happy, suit, cap, plant, dress, magenta, flooring, advertising, gesture, sky, beard, poster, blue, publication |
| Personal Style and Beauty     | hair, shoulder, smile, hairstyle, facial, human, eyelash, photography, flash, joint, sleeve, thigh, skin, neck, happy, expression, lip, eyebrow, leg, comfort, chin, head, fashion, muscle, knee |
| Sports and Athletics          | sport, jersey, uniform, player, equipment, baseball, gesture, short, game, ball, gear, event, sleeve, sportswear, shirt, cap, smile, cricket, bat, competition, team, glove, helmet, hat, grass |
| Outdoor and Leisure Activities | happy, people, sky, photography, flash, nature, smile, plant, leisure, thigh, gesture, cloud, fun, dress, sleeve, fashion, waist, travel, eyewear, water, tree, design, shoe, art, grass |
| Branding and Advertising      | font, blue, electric, rectangle, brand, circle, graphic, logo, event, vision, care, number, art, plant, sunglass, glass, eyewear, happy, magenta, darkness, screenshot, goggles, beard, advertising, parallel |
| Food and Dining               | food, ingredient, tableware, recipe, cuisine, waist, dish, neck, sleeve, dress, fashion, shoulder, piece, one, garment, vegetable, produce, design, thigh, leaf, plate, photography, baked, flash, staple |
| Automotive and Technology     | automotive, vehicle, tire, car, wheel, design, motor, lighting, hood, device, sky, land, grille, font, communication, light, exterior, plant, character, fictional, plate, registration, gesture, gadget, electronic |

## 4. Evaluating Engagement for different topics
To understand the impact of different topics on user engagement, the number of comments is used as the metric for engagement. Using the topic distributions provided by LDA, posts are sorted based on the number of comments. This is segmented into quartiles, and the highest and lowest engagement quartiles are analyzed. This comparison can provide insights on which topics are more prevalent in highly engaging content versus less engaging content.

| **Topic Name**                    | **High Engagement Avg** | **Low Engagement Avg** | **Absolute Difference** |
|----------------------------------|-------------------------|------------------------|-------------------------|
| Formal Events and Fashion        | 0.143                   | 0.142                  | 0.001                   |
| Personal Style and Beauty        | 0.176                   | 0.220                  | 0.044                   |
| Sports and Athletics             | 0.204                   | 0.055                  | 0.149                   |
| Outdoor and Leisure Activities   | 0.230                   | 0.197                  | 0.033                   |
| Branding and Advertising         | 0.119                   | 0.165                  | 0.046                   |
| Food and Dining                  | 0.068                   | 0.167                  | 0.099                   |
| Automotive and Technology        | 0.060                   | 0.054                  | 0.006                   |

Based on the results from this analysis, our recommendation to an influencer on Instragram would be to prioritize content related to "Sports and Athletics", "Outdoor and Leisure Activities", "Formal Events and Fashion", and "Automotive and Technology". Conversely, topics such as "Food and Dining", "Personal Style and Beauty", and "Branding and Advertising" may be less engaging and should be approached with caution. Diversifying content based on these recommendations could potentially enhance overall engagement and audience retention.