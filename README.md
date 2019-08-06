# Marujana_Project

Classification of user types in marijuana- related communications on Twitter, using machine/deep learning techniques

As social media has become an emerging medium to share information in last decade, it has been used by individuals to express their opinions on issues concerning the public. While analysis of this data on social media enabled researchers and analysts to assess the public opinion, it introduced challenges to probable solutions. Legalization of usage of marijuana the collected social media data can be from ordinary personal users or non-personal users such as retail and media. Since we can accurately measure the public opinion on marijuana legalization based on the content of personal users, we need to separate them from non-personal accounts. In this study, I classify users on Twitter into two categories (personal and non-personal) using their profile images since it has been shown that profile picture is an important indicator of the type of a user. I have used an annotated dataset comprising Twitter users, of which are personal users. The dataset was annotated by domain experts in the field of drug abuse and epidemiology, through visiting user profiles on Twitter and looking at their tweets, profile information and profile pictures.

Profile image of users contain different elements regarding the domain of marijuana. For example, while non-personal user might have elements more related to marijuiana (cannabis leaf), personal user might have more random objects. Therefore, users can be classified based on their profile pictures. On the other hand, Such classification will need meaningful numerical representations of these pictures. To be able to assure the relatedness of these images to the marijuana domain, I have translated these images into textual form. After, I have downloaded profile image of each user utilizing the Twitter API through their usernames. I have used a pretrained image classification model called Resnet to retrieve recognized elements from those images. Resnet is a deep learning image classification model, built with imagenet dataset. It produces keywords of elements that it recognizes in the image along with probabilities. I have taken the top 20 keywords for each profile picture. The following entry shows an example output for one image.

[[('n04229816','ski_mask',0.06031425),
  ('n03868863','oxygen_mask',0.02989922),
  ('n02939185', 'caldron', 0.025016505),
  ('n03623198', 'knee_pad', 0.022867722),
  ('n04005630','prison', 0.020947931), 
  ('n03127747', 'crash_helmet', 0.020083249), 
  ('n03724870', 'mask', 0.01899933), 
  ('n04589890', 'window_screen', 0.017520446), 
  ('n07248320', 'book_jacket', 0.01621286)),
  ('n02895154','breastplate',0.014856376),
  ('n03787032','mortarboard',0.013829801),
  ('n04286575','spotlight',0.01367411), 
  ('n02916936', 'bulletproof_vest', 0.0124737555), 
  ('n04023962', 'punching_bag',0.010889093),
  ('n04404412', 'television', 0.010588252), 
  ('n02483708', 'siamang', 0.010586046),
  ('n03929855', 'pickelhaube', 0.010481742),
  ('n03976467', 'Polaroid_camera', 0.0099254595),
  ('n03124170', 'cowboy_hat', 0.009637286)]]

After the retrieval of keywords associated with each image, I utilized a word-embedding algorithm, word2vec. I have used Google’s pre-trained Word2Vec model to obtain the numerical embedding vector of the keywords that represent the profile pictures. This word embedding model produces 300 dimension vector for each word. Some keywords may contain multiple words (e.g., oxygen_mask), and I have collected their embedding and taken their average. To obtain the embedding of each image, I similarly averaged the embeddings of 20 images.

Finally, I have classified users as non-personal and personal. I have used embedding of images for this classification I have applied a logistic regression model on the training set.
