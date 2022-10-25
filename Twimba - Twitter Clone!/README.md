# Twimba: Twitter Clone


- Textarea
  - multiline input field
  - The opening and closing tag need to be together.
  ```jsx
  <main>
    <div class="container">
      <textarea placeholder="Ask me anything!" id="chat-input"></textarea>
      <button id="talk-btn">Talk to me!</button>
    </div>
  </main>
  ```

![Untitled](Twimba%20Twitter%20Clone%208a1de2c47d674bb6b26323af62acd2d3/Untitled.png)

- forEach()
  - a method for iterating over arrays
  ```jsx
  const characters = [
    {
      title: "Ninja",
      emoji: "🥷",
      powers: ["agility", "stealth", "aggression"],
    },
    {
      title: "Sorcerer",
      emoji: "🧙",
      powers: ["magic", "invisibility", "necromancy"],
    },
    {
      title: "Ogre",
      emoji: "👹",
      powers: ["power", "stamina", "shapeshifting"],
    },
    {
      title: "Unicorn",
      emoji: "🦄",
      powers: ["flight", "power", "purity"],
    },
  ];

  // for (let character of characters){
  //     console.log(character)
  // }

  characters.forEach(function (character) {
    console.log(character.title);
  });
  ```
  - example of a nested forEach() example
    - this example will return each power in the powers array
  ```jsx
  characters.forEach(function(character){
      character.powers.forEach(function(power){
          console.log(power)
      })
  ```
- CDN - Content Delivery Network
  - a remote service
  - provides assets to web applications
    - ex: functions, styles, icons ..
  - gives us a snippet of code that will bring the asset into our application
  - Font Awesome is an example of a CDN.
  [font-awesome - Libraries - cdnjs - The #1 free and open source CDN built to make life easier for developers](https://cdnjs.com/libraries/font-awesome)
  ```jsx
  function getFeedHtml() {
    let feedHtml = ``;
    tweetsData.forEach(function (tweet) {
      feedHtml += `
  <div class="tweet">
      <div class="tweet-inner">
          <img src="${tweet.profilePic}" class="profile-pic">
          <div>
              <p class="handle">${tweet.handle}</p>
              <p class="tweet-text">${tweet.tweetText}</p>
              <div class="tweet-details">
                  <span class="tweet-detail">
                      <i class="fa-regular fa-comment-dots"></i>
                      ${tweet.replies.length}
                  </span>
                  <span class="tweet-detail">
                      <i class="fa-solid fa-heart"></i>
                      ${tweet.likes}
                  </span>
                  <span class="tweet-detail">
                  <i class="fa-solid fa-retweet"></i>
                      ${tweet.retweets}
                  </span>
              </div>   
          </div>            
      </div>
  </div>
  `;
    });
    return feedHtml;
  }
  ```
  ![Untitled](Twimba%20Twitter%20Clone%208a1de2c47d674bb6b26323af62acd2d3/Untitled%201.png)
- Data attributes
  - storing extra information in HTML elements
  ```html
  <!-- data-<uniqueName>  = "<dataAttributeName>" -->

  <i class="fa-solid fa-share" data-share="image-1"></i>
  ```
  ```jsx
  document.addEventListener("click", function (e) {
    console.log(e.target.dataset.share);
  });
  ```
- Copying Object & Arrays

  - if you assign an index of an object, you’re creating a shallow copy, not a real copy. So if you make any changes to the variable assigned to the specific object, the changes will be reflected in the main array/object.

  ![Untitled](Twimba%20Twitter%20Clone%208a1de2c47d674bb6b26323af62acd2d3/Untitled%202.png)

- Increment & Decrement Retweet Icon Challenge
  ```jsx
  import { tweetsData } from "./data.js";
  const tweetInput = document.getElementById("tweet-input");
  const tweetBtn = document.getElementById("tweet-btn");

  tweetBtn.addEventListener("click", function () {
    console.log(tweetInput.value);
  });

  document.addEventListener("click", function (e) {
    if (e.target.dataset.like) {
      handleLikeClick(e.target.dataset.like);
    } else if (e.target.dataset.retweet) {
      handleRetweetClick(e.target.dataset.retweet);
    }
  });

  function handleLikeClick(tweetId) {
    const targetTweetObj = tweetsData.filter(function (tweet) {
      return tweet.uuid === tweetId;
    })[0];

    if (targetTweetObj.isLiked) {
      targetTweetObj.likes--;
    } else {
      targetTweetObj.likes++;
    }
    targetTweetObj.isLiked = !targetTweetObj.isLiked;
    render();
  }

  function handleRetweetClick(tweetId) {
    const targetTweetObj = tweetsData.filter(function (tweet) {
      return tweet.uuid === tweetId;
    })[0];

    if (targetTweetObj.isRetweeted) {
      targetTweetObj.retweets--;
    } else {
      targetTweetObj.retweets++;
    }
    targetTweetObj.isRetweeted = !targetTweetObj.isRetweeted;
    render();
  }
  ```
  ![Untitled](Twimba%20Twitter%20Clone%208a1de2c47d674bb6b26323af62acd2d3/Untitled%203.png)
- Conditionally Render CSS

  - giving elements different classes under different conditions
  - The `${<className>}` is used for any variable that gets rendered out based off a JS function

  ```jsx
  const galleryContainer = document.getElementById("gallery-container");

  let isLiked = false;

  document.addEventListener("click", function (e) {
    if (e.target.dataset.heart) {
      isLiked = !isLiked;
      render();
    } else if (e.target.dataset.share) {
    }
  });

  function render() {
    let heartClass = "";

    if (isLiked) {
      heartClass = "liked";
    }

    let imageHtml = `
      		<div id="image-1" class="img-container">
  			<img src="dino2.jpeg" alt="Man in front of dinosaur">
  			<div class="social-icons-container">
  				<i class="fa-solid fa-heart ${heartClass}" data-heart="image-1"></i>
  				<i class="fa-solid fa-share " data-share="image-1"></i>
  			</div>
      `;
    galleryContainer.innerHTML = imageHtml;
  }

  render();
  ```

  - Retweet & Like icons changing colours

  ```jsx
  import { tweetsData } from "./data.js";
  const tweetInput = document.getElementById("tweet-input");
  const tweetBtn = document.getElementById("tweet-btn");

  tweetBtn.addEventListener("click", function () {
    console.log(tweetInput.value);
  });

  document.addEventListener("click", function (e) {
    if (e.target.dataset.like) {
      handleLikeClick(e.target.dataset.like);
    } else if (e.target.dataset.retweet) {
      handleRetweetClick(e.target.dataset.retweet);
    }
  });

  function handleLikeClick(tweetId) {
    const targetTweetObj = tweetsData.filter(function (tweet) {
      return tweet.uuid === tweetId;
    })[0];

    if (targetTweetObj.isLiked) {
      targetTweetObj.likes--;
    } else {
      targetTweetObj.likes++;
    }
    targetTweetObj.isLiked = !targetTweetObj.isLiked;
    render();
  }

  function handleRetweetClick(tweetId) {
    const targetTweetObj = tweetsData.filter(function (tweet) {
      return tweet.uuid === tweetId;
    })[0];

    if (targetTweetObj.isRetweeted) {
      targetTweetObj.retweets--;
    } else {
      targetTweetObj.retweets++;
    }
    targetTweetObj.isRetweeted = !targetTweetObj.isRetweeted;
    render();
  }

  function getFeedHtml() {
    let feedHtml = ``;

    tweetsData.forEach(function (tweet) {
      let likeIconClass = "";

      if (tweet.isLiked) {
        likeIconClass = "liked";
      }

      let retweetIconClass = "";

      if (tweet.isRetweeted) {
        retweetIconClass = "retweeted";
      }

      feedHtml += `
  <div class="tweet">
      <div class="tweet-inner">
          <img src="${tweet.profilePic}" class="profile-pic">
          <div>
              <p class="handle">${tweet.handle}</p>
              <p class="tweet-text">${tweet.tweetText}</p>
              <div class="tweet-details">
                  <span class="tweet-detail">
                      <i class="fa-regular fa-comment-dots"
                      data-reply="${tweet.uuid}"
                      ></i>
                      ${tweet.replies.length}
                  </span>
                  <span class="tweet-detail">
                      <i class="fa-solid fa-heart ${likeIconClass}"
                      data-like="${tweet.uuid}"
                      ></i>
                      ${tweet.likes}
                  </span>
                  <span class="tweet-detail">
                      <i class="fa-solid fa-retweet ${retweetIconClass}"
                      data-retweet="${tweet.uuid}"
                      ></i>
                      ${tweet.retweets}
                  </span>
              </div>   
          </div>            
      </div>
  </div>
  `;
    });
    return feedHtml;
  }

  function render() {
    document.getElementById("feed").innerHTML = getFeedHtml();
  }

  render();
  ```

  ![Untitled](Twimba%20Twitter%20Clone%208a1de2c47d674bb6b26323af62acd2d3/Untitled%204.png)

- UUID
  - Universally Unique Identifiers
    - a string of 36 characters
    - often used to identify pieces of data
    - Highly likely to be globally unique
    - GUID === UUID
  - You can use this repo from Github to generate UUIDs through a CDN
    [GitHub - uuidjs/uuid: Generate RFC-compliant UUIDs in JavaScript](https://github.com/uuidjs/uuid#cdn-builds)
    ```jsx
    import { v4 as uuidv4 } from "https://jspm.dev/uuid";

    const cars = [
      {
        brand: "Nissan",
        model: "Leaf",
        price: 3000,
        uuid: "4fb2b6b7-c7ee-4c80-8de1-390e89f43d7f",
      },
      {
        brand: "Toyota",
        model: "Prius",
        price: 6000,
        uuid: "82a13f62-d239-46a2-a94f-020189338e1a",
      },
    ];

    cars.push({
      brand: "Tesla",
      model: "Model S",
      price: "🤦‍♂️",
      uuid: uuidv4(),
    });

    console.log(cars);
    ```
  - I had to google how to add elements to the beginning of an array:
    ![Untitled](Twimba%20Twitter%20Clone%208a1de2c47d674bb6b26323af62acd2d3/Untitled%205.png)
- The following challenge allows me to add new tweets to the tweetsData object and render it.
  ```jsx
  function handleTweetBtnClick() {
    if (tweetInput.value) {
      tweetsData.unshift({
        handle: `@Scrimba`,
        profilePic: `images/scrimbalogo.png`,
        likes: 0,
        retweets: 0,
        tweetText: tweetInput.value,
        replies: [],
        isLiked: false,
        isRetweeted: false,
        uuid: uuidv4(),
      });
    }
    tweetInput.value = "";
    render();
  }
  ```
  ![Untitled](Twimba%20Twitter%20Clone%208a1de2c47d674bb6b26323af62acd2d3/Untitled%206.png)
- Keeping variables within their local scope as much as possible is best practice. As the code bases grows, having global variables becomes a risk if other developers accidently name their variable the same.
