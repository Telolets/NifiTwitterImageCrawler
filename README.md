# NifiTwitterImageCrawler

NiFi-based flow template to collect images from twitter hash-based filter streaming.

The template are separated into 3 parts:
### Top area
Where the tweet are collected, go the respective ProcessGroup, and recorded into database / filesystem.
![TopAreaImage](https://github.com/Telolets/NifiTwitterImageCrawler/blob/master/images/1toparea.png)
 
### Tweet Cleaning ProcessGroup
- Filter and extract RT (Retweet) / Quoted Tweet to the original tweet
- Filter out tweet without images.
![TweetCleaning](https://github.com/Telolets/NifiTwitterImageCrawler/blob/master/images/2tweetcleaning.png)

### Image Extraction ProcessGroup
- Load the image from the filtered tweet. 
- Each file are named with format including the tweet user. 
- Check duplication for each image (Can be from other person, or they reupload the image)
![ImageExtraction](https://github.com/Telolets/NifiTwitterImageCrawler/blob/master/images/3imageExtraction.png)
 

## Dependencies
* [Apache NiFi] - Obviously
* [MongoDB] - To record the JSON tweet
* [Redis] - To save the hashed image metadata for check duplication


## Why? 
1. As a person who has zero art skill, I really enjoy looking at artists works on twitter that I follow. Unfortunately twitter is moving very fast and I don't have time to follow them all the time.
2. After found out and read about Apache NiFi, I really eager to try creating something with it. So this is my first completed Nifi flow.
3. Previously I made this with .NET which is working for some time. Eventually there are many parts that keeps need to be fixed, mostly because the app is running 24 hours. Now it already run days without those small errors or I could ignore it.

## Problems and Todo
- Twitter filter does not work really well with japanese tweet. Japanese sentences did not have a spaces between words, which how the default twitter separate sentences to word-token. If there are good Japanese-word token separator, I could try create a Processor and extract better tags for each tweet (Currently only from hashtags).

[Apache NiFi]: <https://nifi.apache.org/>
[MongoDB]: <https://www.mongodb.com/>
[Redis]: <https://redis.io/>
