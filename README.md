//Save-into-local-storage

@@ -41,15 +41,24 @@ function newTweet(e){
    //Add to the list
    tweetList.appendChild(li);

//Add to local storage
    //Add to local storage
    addTweetLocalStorage(tweet);

    //Print the alert
    alert('Tweet Added');

    this.reset();

}

//Remove the tweets from the DOM
function removeTweet(e){
    if(e.target.classList.contains('remove-tweet')) {
        e.target.parentElement.remove();
    }

    //Remove from Storage
    removeTweetLocalStorage(e.target.parentElement.textContent);

}

@@ -98,4 +107,24 @@ function localStorageOnLoad() {
    //Add to the list
    tweetList.appendChild(li);
    });
}

//Removes the tweet from local storage
function removeTweetLocalStorage(tweet) {
    //Get tweets from Storage
    let tweets = getTweetsFromStorage();

    //Remove the X from the Tweet
    const tweetDelete = tweet.substring(0, tweet.length - 1);

    //Loop throught the tweets and remove the tweet that's equal
    tweets.forEach(function(tweetLS, index) {
        if(tweetDelete === tweetLS) {
           tweets.splice(index, 1);
        }
    });

    //Save the Data
    localStorage.setItem('tweets',JSON.stringify(tweets));

