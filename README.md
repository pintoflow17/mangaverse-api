# MangaVerse API Documentation

## Introduction

**MangaVerse API** is your ultimate gateway to a vast collection of manga data, designed for developers and enthusiasts who want to explore, analyze, and integrate manga information into their applications. With a user-friendly interface and a comprehensive database, you can access details about titles, authors, genres, chapters, and more.

### Key Features

- **Extensive Database**: Access a wide range of manga titles and their associated metadata.
- **Search Functionality**: Easily search for manga by title, genre, or author.
- **Chapter Information**: Retrieve detailed information about chapters, including summaries and release dates.
- **User Reviews and Ratings**: Get insights from the community with user-generated reviews and ratings.

## Authentication

The URL you need to use is the following: `https://mangaverse-api1.p.rapidapi.com/`
The API requires the headers listed below:

- **`x-rapidapi-host`**: `mangaverse-api1.p.rapidapi.com`
- **`x-rapidapi-key`**: `YOUR_API_KEY`

Make sure to replace `YOUR_API_KEY` with your API key. You can register one [here](https://rapidapi.com/belchiorarkad-FqvHs2EDOtP/api/mangaverse-api1/pricing).
Some frameworks automatically add extra headers, you have to make sure to remove them in order to get a response from the API.

## Endpoints

The API is configured to accept only **GET** requests. Below are the available endpoints with their descriptions and required parameters.

### 1. **`GET /search`**

- **Description**: Searches for manga or anime titles based on a query string.

| Parameter | Type   | Default | Description                            | Required |
|-----------|--------|---------|----------------------------------------|----------|
| `query`   | string | -       | The title to search for                | Yes      |

Example request:

```javascript
fetch('https://mangaverse-api1.p.rapidapi.com/search?query=Naruto', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'mangaverse-api1.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Example response:

```json
[
  {
    "id": 11,
    "type": "manga",
    "name": "Naruto",
    "url": "https://myanimelist.net/manga/11/Naruto",
    "image_url": "https://cdn.myanimelist.net/r/116x180/images/manga/3/249658.jpg?s=892c44200eb8169ca89a66f4a7eecc81",
    "thumbnail_url": "https://cdn.myanimelist.net/r/116x76/images/manga/3/249658.jpg?s=feb0c103518fc929e18e1bb97e0cabc2",
    "payload": {
      "media_type": "Manga",
      "start_year": 1999,
      "published": "Sep 21, 1999 to Nov 10, 2014",
      "score": "8.07",
      "status": "Finished"
    },
    "es_score": 6.3428125
  },
  {
    "id": 6444,
    "type": "manga",
    "name": "Naruto",
    "url": "https://myanimelist.net/manga/6444/Naruto",
    "image_url": "https://cdn.myanimelist.net/r/116x180/images/manga/1/125935.jpg?s=58badea937fa8be3d7ab0bffe41d6fb2",
    "thumbnail_url": "https://cdn.myanimelist.net/r/116x76/images/manga/1/125935.jpg?s=a6576a58fcf88203c9afc83f8f98b851",
    "payload": {
      "media_type": "One-shot",
      "start_year": 1997,
      "published": "Aug 18, 1997",
      "score": "6.49",
      "status": "Finished"
      ...
```

### 2. **`GET /info`**

- **Description**: Retrieves information about a manga or anime by its title.

| Parameter   | Type    | Default | Description                                             | Required |
|-------------|---------|---------|---------------------------------------------------------|----------|
| `title`     | string  | -       | The title of the manga or anime                         | Yes      |
| `bestMatch` | boolean | `true`  |  Determines whether to search for the best match or not | No       |

Example request:

```javascript
fetch('https://mangaverse-api1.p.rapidapi.com/info?title=Killing%20Stalking', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'mangaverse-api1.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Example response:

```json
{
  "title": "Killing Stalking",
  "synopsis": "Yoon Bum is a broken, beaten, and scarred human being, whose mental instability and loneliness have led him to unhealthy outlets for his pent up emotions. With his weakened mind, Bum has found solace in watching his handsome classmate Oh Sangwoo; Bum's love runs so deep, in fact, that he has begun stalking him. While creeping in Sangwoo's house one day, Bum makes a horrifying discovery—a torture chamber and a naked young woman tied up, gagged, and pleading for help.\n\nThe life of this woman is doomed, and Bum cannot escape either, as he is soon discovered. His eyes sickening and crazed, Sangwoo takes Bum as his newest pet and victim. What awaits the mentally tortured Bum is a world of physical mutilation, toxic dependence, and abuse masquerading as so-called love.\n\n[Written by MAL Rewrite]",
  "picture": "https://cdn.myanimelist.net/images/manga/1/220586.jpg",
  "characters": [
    {
      "link": "https://myanimelist.net/character/175570/Sangwoo_Oh",
      "picture": "https://cdn.myanimelist.net/images/characters/16/393992.jpg",
      "name": "Oh, Sangwoo",
      "role": "Main",
      "seiyuu": {
        "name": ""
      }
    },
    {
      "link": "https://myanimelist.net/character/175571/Bum_Yoon",
      "picture": "https://cdn.myanimelist.net/images/characters/6/393995.jpg",
      "name": "Yoon, Bum",
      "role": "Main",
      "seiyuu": {
        "name": ""
      }
    },
    {
      "link": "https://myanimelist.net/character/175575/Seungbae_Yang",
      "picture": "https://cdn.myanimelist.net/images/characters/4/393624.jpg",
      "name": "Yang, Seungbae",
      "role": "Supporting",
      "seiyuu": {
        "name": ""
        ...
```

### 3. **`GET /manga/details`**

- **Description**: Retrieves detailed information about a manga based on its ID.

| Parameter | Type   | Default | Description                                         | Required |
|-----------|--------|---------|-----------------------------------------------------|----------|
| `id`      | string | -       | The ID of the manga for which details are requested | Yes      |

Example request:

```javascript
fetch('https://mangaverse-api1.p.rapidapi.com/manga/details?id=2', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'mangaverse-api1.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Example response:

```json
{
  "result": {
    "title": "Berserk",
    "image": "https://cdn.myanimelist.net/images/manga/1/157897.jpg",
    "altTitles": {
      "synonyms": "Berserk: The Prototype",
      "japanese": "ベルセルク",
      "english": "Berserk"
    },
    "info": {
      "type": "Manga",
      "volumes": "Unknown",
      "chapters": "Unknown",
      "status": "Publishing",
      "published": "Aug  25, 1989 to ?",
      "genres": [
        "Action",
        "Adventure",
        "Award Winning",
        "Drama",
        "Fantasy",
        "Horror",
        "Supernatural"
      ],
      "themes": [
        "Gore",
        "Military",
        "Mythology",
        "Psychological"
      ],
      ...
```

### 4. **`GET /news`**

- **Description**: Retrieves news related to anime, providing insights into recent developments, announcements, and events. Provides pagination support.

| Parameter | Type   | Default | Description                            | Required |
|-----------|--------|---------|----------------------------------------|----------|
| `limit`   | string | `120`   | Number of news entries to retrieve     | No       |

Example request:

```javascript
fetch('https://mangaverse-api1.p.rapidapi.com/news', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'mangaverse-api1.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Example response:

```json
{
  "result": [
    {
      "title": "A Glimpse Into the Wacky World of Dandadan",
      "link": "https://myanimelist.net/news/71906725",
      "image": "https://cdn.myanimelist.net/r/100x156/s/common/uploaded_files/1730084264-98c513a39e9211d06b81a030f36b65c2.jpeg?s=3d7c45860f044617368d52fa42f7ffa9",
      "text": " With its blend of supernatural thrills, extraterrestrial encounters, and quirky humor, Dandadan (Dan Da Dan) has become one of the most anticipated anime of the year since its debut in October 2024. Based on Yukinobu Tatsu's popular manga, the series takes viewers on a wild ride...",
      "newsNumber": "71906725"
    },
    {
      "title": "Romance Meets Sports: Shouya Chiba, Akari Kitou Bring Us Inside 'Ao no Hako'",
      "link": "https://myanimelist.net/news/71892880",
      "image": "https://cdn.myanimelist.net/r/100x156/s/common/uploaded_files/1729915585-295d38c2688e0bb1b8755a4005bf948d.jpeg?s=e1ec076209fb7a82b811e65530208be8",
      "text": " With its down-to-earth yet charming cast, Ao no Hako (Blue Box) has continuously been a fan favorite in Weekly Shounen Jump since the serialization began. Combining romance and sports, a genre pairing not frequently seen in the West, the manga's main characters notably all play...",
      "newsNumber": "71892880"
    },
    {
      "title": "In Pursuit of Egoism: The Essence of 'Blue Lock'",
      "link": "https://myanimelist.net/news/71886250",
      "image": "https://cdn.myanimelist.net/r/100x156/s/common/uploaded_files/1729834381-4dea759b0604ad3bf1ac2fbff1a3844e.jpeg?s=88b466e681f27a4200e74249b41bd3df",
      "text": " Blue Lock has quickly become a standout in the sports anime genre, known for its intense action and psychological depth as it redefines the high-stakes world of soccer. With Season 2 currently airing, the series continues to capture audiences with its bold storytelling and strik...",
      "newsNumber": "71886250"
    },
    {
      "title": "'Izure Saikyou no Renkinjutsushi' Reveals Additional Cast, Staff, First Promo",
      "link": "https://myanimelist.net/news/71879625",
      "image": "https://cdn.myanimelist.net/r/100x156/s/common/uploaded_files/1729727852-22f0f6b788eb13c49cba0e963e7808ae.jpeg?s=cecb9af896524e6016b5f559d247199a",
      "text": "The official website of the Izure Saikyou no Renkinjutsushi? (Someday Will I Be the Greatest Alchemist?) television anime revealed two additional cast, staff, a key visual (pictured), and the first promotional video on Wednesday. The anime series adapting Maru Kogitsune's adventu...",
      "newsNumber": "71879625"
    },
    ...
```

### 5. **`GET /episodes`**

- **Description**: Retrieves a list of episodes for a given anime title.

| Parameter | Type   | Default | Description                                             | Required |
|-----------|--------|---------|---------------------------------------------------------|----------|
| `title`   | string | -       | The title of the anime for which episodes are requested | Yes      |

Example request:

```javascript
fetch('https://mangaverse-api1.p.rapidapi.com/episodes?title=Naruto', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'mangaverse-api1.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Example response:

```json
{
  "result": [
    {
      "epNumber": 1,
      "aired": "Feb 15, 2007",
      "discussionLink": "https://myanimelist.net/forum/?topicid=530",
      "title": "Homecoming",
      "japaneseTitle": "Kikyou (帰郷)"
    },
    {
      "epNumber": 2,
      "aired": "Feb 15, 2007",
      "discussionLink": "https://myanimelist.net/forum/?topicid=111130",
      "title": "The Akatsuki Makes Its Move",
      "japaneseTitle": "Akatsuki, Shidou (暁、始動)"
    },
    {
      "epNumber": 3,
      "aired": "Feb 22, 2007",
      "discussionLink": "https://myanimelist.net/forum/?topicid=595",
      "title": "The Results of Training",
      "japaneseTitle": "Shugyou no Seika (修業の成果)"
    },
    {
      "epNumber": 4,
      "aired": "Mar 1, 2007",
      "discussionLink": "https://myanimelist.net/forum/?topicid=639",
      "title": "The Jinchuriki of the Sand",
      "japaneseTitle": "Suna no Jinchuuriki (砂の人柱力)"
    },
    ...
```

### 6. **`GET /genre-list`**

- **Description**: Retrieves a list of available genres in the manga database.

Example request:

```javascript
fetch('https://mangaverse-api1.p.rapidapi.com/genre-list', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'mangaverse-api1.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Example response:

```json
{
  "result": {
    "genres": [
      {
        "id": "1",
        "name": "Action",
        "available": 9,
        "url": "https://myanimelist.net/manga/genre/1/Action"
      },
      {
        "id": "2",
        "name": "Adventure",
        "available": 4,
        "url": "https://myanimelist.net/manga/genre/2/Adventure"
      },
      {
        "id": "5",
        "name": "Avant Garde",
        "available": 82,
        "url": "https://myanimelist.net/manga/genre/5/Avant_Garde"
      },
      {
        "id": "46",
        "name": "Award Winning",
        "available": 499,
        "url": "https://myanimelist.net/manga/genre/46/Award_Winning"
      },
      {
        "id": "28",
        "name": "Boys Love",
        ...
```

### 7. **`GET /manga/genre`**

- **Description**: Retrieves manga based on a specified genre.

| Parameter | Type   | Default | Description                                              | Required |
|-----------|--------|---------|----------------------------------------------------------|----------|
| `genreId` | string | -       | The ID of the genre for which manga titles are requested | Yes      |
| `page`    | string | `1`     | The page number for paginated results                     | No       |

Example request:

```javascript
fetch('https://mangaverse-api1.p.rapidapi.com/manga/genre?genreId=2', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'mangaverse-api1.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Example response:

```json
{
  "result": [
    {
      "title": "Berserk",
      "link": "https://myanimelist.net/manga/2/Berserk",
      "info": [
        "Manga, 1989",
        "Publishing",
        "? vol, ? chp"
      ],
      "genres": [
        "Action",
        "Adventure",
        "Award Winning",
        "Drama",
        "Fantasy",
        "Horror",
        "Supernatural"
      ],
      "synopsis": "Guts, a former mercenary now known as the Black Swordsman, is out for revenge. After a tumultuous childhood, he finally finds someone he respects and believes he can trust, only to have everything fall apart when this person takes away everything important to Guts for the purpose of fulfilling his own desires. Now marked for death, Guts becomes condemned to a fate in which he is relentlessly pursued by demonic beings.\n\nSetting out on a dreadful quest riddled with misfortune, Guts, armed with a massive sword and monstrous strength, will let nothing stop him, not even death itself, until he is finally able to take the head of the one who stripped him—and his loved one—of their humanity.\n\n[Written by MAL Rewrite]\n\nIncluded one-shot:\nVolume 14: Berserk: The Prototype",
      "authors": [
        "Miura, Kentarou",
        "Studio Gaga",
        "Young Animal",
        "Gore",
        "Military",
        "Mythology",
        "Psychological",
        "Seinen"
      ],
      ...
```

### 8. **`GET /manga/characters`**

- **Description**: Retrieves information about characters featured in a manga based on its ID.

| Parameter | Type   | Default | Description                                                      | Required |
|-----------|--------|---------|------------------------------------------------------------------|----------|
| `id`      | string | -       | The ID of the manga for which character information is requested | Yes      |

Example request:

```javascript
fetch('https://mangaverse-api1.p.rapidapi.com/manga/characters?id=2', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'mangaverse-api1.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Example response:

```json
{
  "result": [
    {
      "name": "Casca",
      "role": "Main",
      "favorites": 4456
    },
    {
      "name": "de Vandimion, Farnese",
      "role": "Main",
      "favorites": 1039
    },
    {
      "name": "Griffith",
      "role": "Main",
      "favorites": 15394
    },
    {
      "name": "Guts",
      "role": "Main",
      "favorites": 82985
    },
    {
      "name": "Isidro",
      "role": "Main",
      "favorites": 296
    },
    {
      "name": "Puck",
      "role": "Main",
      ...
```

### 9. **`GET /manga/stats`**

- **Description**: Retrieves statistical information about a manga based on its ID, providing insights into its popularity, ratings, and other relevant metrics.

| Parameter | Type   | Default | Description                                                        | Required |
|-----------|--------|---------|--------------------------------------------------------------------|----------|
| `id`      | string | -       | The ID of the manga for which statistical information is requested | Yes      |

Example request:

```javascript
fetch('https://mangaverse-api1.p.rapidapi.com/manga/stats?id=2', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'mangaverse-api1.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Example response:

```json
{
  "result": {
    "summary_stats": {
      "Reading": "395,119",
      "Completed": "94,775",
      "On-Hold": "56,957",
      "Dropped": "11,592",
      "Plan to Read": "163,817",
      "Total": "722,260"
    },
    "stats": [
      {
        "score": 10,
        "percentage": 68.7,
        "votes": 248970
      },
      {
        "score": 9,
        "percentage": 18.8,
        "votes": 68077
      },
      {
        "score": 8,
        "percentage": 7.5,
        "votes": 27223
      },
      {
        "score": 7,
        "percentage": 2.6,
        "votes": 9492
        ...
```

### 10. **`GET /manga/review`**

- **Description**: Retrieves reviews for a manga based on its ID, with support for pagination.

| Parameter | Type   | Default | Description                                         | Required |
|-----------|--------|---------|-----------------------------------------------------|----------|
| `id`      | string | -       | The ID of the manga for which reviews are requested | Yes      |
| `page`    | string | `1`     | The page number for paginated results               | No       |

Example request:

```javascript
fetch('https://mangaverse-api1.p.rapidapi.com/manga/review?id=2', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'mangaverse-api1.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Example response:

```json
{
  "result": [
    {
      "reviewer": {
        "username": "TheCriticsClub",
        "profileUrl": "https://myanimelist.net/profile/TheCriticsClub",
        "pictureUrl": "https://cdn.myanimelist.net/s/common/userimages/023e47fa-3582-4a1c-a4d5-6d27e6238aea_42x62_i?s=4005ca1527beb95f7d1c6f21167a7977"
      },
      "tags": [
        {
          "type": "status",
          "value": "Recommended",
          "details": ""
        },
        {
          "type": "status",
          "value": "Preliminary",
          "details": "(295/? chp)"
        }
      ],
      "date": "Apr 29, 2008",
      "rating": 10,
      "reviewText": "Story - 9.38\n\nThe first three volumes may discourage some of the readers because it's starts off kind of slow and the initial artwork is not quite up to..."
      ...
```

### 11. **`GET /manga/recommendation`**

- **Description**: Retrieves recommendations for a manga based on its ID, suggesting other manga titles that users might enjoy.

| Parameter | Type   | Default | Description                                                 | Required |
|-----------|--------|---------|-------------------------------------------------------------|----------|
| `id`      | string | -       | The ID of the manga for which recommendations are requested | Yes      |

Example request:

```javascript
fetch('https://mangaverse-api1.p.rapidapi.com/manga/recommendation?id=2', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'mangaverse-api1.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Example response:

```json
{
  "result": [
    {
      "text": "Both focus on an antihero of sorts with extreme proficiency in slicing dudes. Beautiful artwork, complex and mature themes, and a (while not yet present in ...",
      "recommendedBy": "Veronin"
    },
    {
      "text": "The character of Guts (of Berserk) is ostensibly inspired by the legendary Miyamoto Musashi, both of them being unmatched swordsmen who overcame death and tragedy ...",
      "recommendedBy": "zenoslime"
    },
    {
      "text": "Berserk and Vagabond are classic tales that shows the journey of an anti-hero protagonist. There is a lot of purpose for their actions and both series focuses a ...",
      "recommendedBy": "Stark700"
    },
    {
      "text": "- Both have anti-heroes as the main character \n- Beautiful artwork that is easily noticeable\n- Lots of blood and gore",
      "recommendedBy": "Rance-sama"
    },
    {
      "text": "The manga that is not most similar to Berserk but you will probably like the most if you liked Berserk would surely be Vagabond. They are two amazingly highly ...",
      "recommendedBy": "majinleen"
    },
    {
      "text": "Both stories are about characters who's life revolves around violence. While Berserk is about a quest of pure rage, Vagabond is the path of a warrior and where it may lead.",
      "recommendedBy": "SpiritsRise"
    },
    {
      "text": "Both series start out with a main character and follow him as a lonely little boy who grows up to become incredibly powerful. \nBoth series have incredibly ...",
      "recommendedBy": "sullynathan"
    },
    ...
```

### 12. **`GET /manga/interest-stacks`**

- **Description**: Retrieves interest stacks for a manga based on its ID, allowing users to see what other manga titles readers of the specified manga are interested in.

| Parameter | Type   | Default | Description                                                 | Required |
|-----------|--------|---------|-------------------------------------------------------------|----------|
| `id`      | string | -       | The ID of the manga for which interest stacks are requested | Yes      |
| `page`    | string | `1`     | The page number for paginated results                       | No       |

Example request:

```javascript
fetch('https://mangaverse-api1.p.rapidapi.com/manga/interest-stacks?id=2', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'mangaverse-api1.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Example response:

```json
{
  "result": [
    {
      "title": "Tezuka Osamu Cultural Prize (Grand Prize)",
      "titleLink": "https://myanimelist.net/stacks/52",
      "image": "https://cdn.myanimelist.net/images/manga/2/298132.webp",
      "author": "",
      "description": "Named after Osamu Tezuka, the Tezuka Osamu Cultural Prize (手塚治虫文化賞, Tezuka Osamu Bunkashō) is a yearly manga prize awarded to manga artists or their ...",
      "stats": "37 Entries · Apr 22, 10:21 AM",
      "reportLink": "https://myanimelist.net/modules.php?go=report&type=intereststacks&id=52",
      "stackId": "52",
      "numStacks": "226"
    },
    {
      "title": "Dark Fantasy",
      "titleLink": "https://myanimelist.net/stacks/227",
      "image": "https://cdn.myanimelist.net/images/manga/1/157897.webp",
      "author": "flottings",
      "description": "Manga with dark fantasy world building. Stories set in a fantasy setting",
      "stats": "6 Entries · Apr 7, 2022 1:30 AM",
      "reportLink": "https://myanimelist.net/modules.php?go=report&type=intereststacks&id=227",
      "stackId": "227",
      "numStacks": "42"
    },
    {
      "title": "Sexually explicit manga",
      "titleLink": "https://myanimelist.net/stacks/285",
      "image": "https://cdn.myanimelist.net/images/manga/1/189001.webp",
      "author": "IrrelevantGuy",
      "description": "I initially struggled to outline what \"sexually explicit manga\" exactly means, but I ultimately went with \"any manga where a sizeable portion of its ...",
      ...
```

### 13. **`GET /manga/news`**

- **Description**: Retrieves news related to a specific manga based on its ID, providing updates, announcements, and other relevant information.

| Parameter | Type   | Default | Description                                     | Required |
|-----------|--------|---------|-------------------------------------------------|----------|
| `id`      | string | -       | The ID of the manga for which news is requested | Yes      |

Example request:

```javascript
fetch('https://mangaverse-api1.p.rapidapi.com/manga/news?id=2', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'mangaverse-api1.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Example response:

```json
{
  "result": [
    {
      "title": "Kentarou Miura's Assistants Resume 'Berserk' Serialization, 'Holyland' Creator Kouji Mori to Supervise",
      "link": "https://myanimelist.net/news/66547854",
      "image": [
        "https://cdn.myanimelist.net/r/50x78/s/common/uploaded_files/1654587114-bf53f8de5beebd981afec1932486e604.jpeg?s=14bd951b901aa46034b344818e7cbd31",
        "https://cdn.myanimelist.net/r/100x156/s/common/uploaded_files/1654587114-bf53f8de5beebd981afec1932486e604.jpeg?s=40ce2d8135aef696b704817d9a766e0b"
      ],
      "date": "Jun 7, 2022 12:33 AM by Vindstot",
      "author": "Vindstot",
      "discussLink": "https://myanimelist.net/forum/?topicid=2021160"
    },
    {
      "title": "'Berserk' Creator Kentarou Miura Dies at 54",
      "link": "https://myanimelist.net/news/63203251",
      "image": [
        "https://cdn.myanimelist.net/r/50x78/s/common/uploaded_files/1621492994-97c345f3d0912b89a1207f235274b1a4.jpeg?s=b42ac2bcc10470f9f29e6d4647f4c4fc",
        "https://cdn.myanimelist.net/r/100x156/s/common/uploaded_files/1621492994-97c345f3d0912b89a1207f235274b1a4.jpeg?s=ab95a7a410c2f680291a1b3134020013"
      ],
      "date": "May 19, 2021 9:39 PM by Vindstot",
      "author": "Vindstot",
      "discussLink": "https://myanimelist.net/forum/?topicid=1924224"
    },
    {
      "title": "North American Anime & Manga Releases for March",
      "link": "https://myanimelist.net/news/62171559",
      "image": [
        "https://cdn.myanimelist.net/r/50x78/s/common/uploaded_files/1614653396-7a00b4ffc582810d1d397ad1fad351c3.png?s=7020936c11aba46d98b01136bea9c6a7",
        "https://cdn.myanimelist.net/r/100x156/s/common/uploaded_files/1614653396-7a00b4ffc582810d1d397ad1fad351c3.png?s=a840c460ec300e333a525ddea425e6a6"
        ...
```

### 14. **`GET /manga/forum`**

- **Description**: Retrieves forum discussions related to a specific manga based on its ID, allowing users to engage with other fans and discuss various aspects of the manga.

| Parameter | Type   | Default | Description                                                   | Required |
|-----------|--------|---------|---------------------------------------------------------------|----------|
| `id`      | string | -       | The ID of the manga for which forum discussions are requested | Yes      |

Example request:

```javascript
fetch('https://mangaverse-api1.p.rapidapi.com/manga/forum?id=2', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'mangaverse-api1.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Example response:

```json
{
  "result": [
    {
      "topicId": "2186100",
      "title": "Berserk Chapter 377 Discussion",
      "author": "Barrycade",
      "link": "https://myanimelist.net/forum/?topicid=2186100",
      "date": "Oct 25",
      "replies": "32",
      "lastPostAuthor": "petvma",
      "lastPostDate": "3 hours ago"
    },
    {
      "topicId": "365371",
      "title": "Berserk Chapter 276 Discussion",
      "author": "AlexSadist-sama",
      "link": "https://myanimelist.net/forum/?topicid=365371",
      "date": "Nov 14, 2011",
      "replies": "14",
      "lastPostAuthor": "GureJoestar",
      "lastPostDate": "Yesterday, 2:47 AM"
    },
    {
      "topicId": "365333",
      "title": "Berserk Chapter 273 Discussion",
      "author": "AlexSadist-sama",
      "link": "https://myanimelist.net/forum/?topicid=365333",
      "date": "Nov 14, 2011",
      "replies": "13",
      "lastPostAuthor": "GureJoestar",
      ...
```

### 15. **`GET /manga/clubs`**

- **Description**: Retrieves clubs or groups dedicated to discussing or sharing content related to a specific manga based on its ID.

| Parameter | Type   | Default | Description                                       | Required |
|-----------|--------|---------|---------------------------------------------------|----------|
| `id`      | string | -       | The ID of the manga for which clubs are requested | Yes      |

Example request:

```javascript
fetch('https://mangaverse-api1.p.rapidapi.com/manga/clubs?id=2', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'mangaverse-api1.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Example response:

```json
{
  "result": [
    {
      "link": "https://myanimelist.net/clubs.php?cid=20081",
      "name": "Recommendation Club",
      "members": 34234
    },
    {
      "link": "https://myanimelist.net/clubs.php?cid=2056",
      "name": "Ecchi Squad",
      "members": 11778
    },
    {
      "link": "https://myanimelist.net/clubs.php?cid=85302",
      "name": "Türkiye Kulübü",
      "members": 7258
    },
    {
      "link": "https://myanimelist.net/clubs.php?cid=25565",
      "name": "20+",
      "members": 3137
    },
    {
      "link": "https://myanimelist.net/clubs.php?cid=413",
      "name": "Dark Anime Club",
      "members": 2916
    },
    {
      "link": "https://myanimelist.net/clubs.php?cid=67310",
      "name": "Casual Discussion 2.0",
      ...
```

### 16. **`GET /manga/pictures`**

- **Description**: Retrieves pictures or images related to a specific manga based on its ID, providing visual content such as artwork, covers, and promotional materials.

| Parameter | Type   | Default | Description                                          | Required |
|-----------|--------|---------|------------------------------------------------------|----------|
| `id`      | string | -       | The ID of the manga for which pictures are requested | Yes      |

Example request:

```javascript
fetch('https://mangaverse-api1.p.rapidapi.com/manga/pictures?id=2', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'mangaverse-api1.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Example response:

```json
{
  "result": [
    {
      "imgSrc": "https://cdn.myanimelist.net/images/manga/1/157569.jpg",
      "reportLink": "https://myanimelist.net/modules.php?go=report&type=mangapic&id=157569"
    },
    {
      "imgSrc": "https://cdn.myanimelist.net/images/manga/1/157897.jpg",
      "reportLink": "https://myanimelist.net/modules.php?go=report&type=mangapic&id=157897"
    },
    {
      "imgSrc": "https://cdn.myanimelist.net/images/manga/1/157931.jpg",
      "reportLink": "https://myanimelist.net/modules.php?go=report&type=mangapic&id=157931"
    },
    {
      "imgSrc": "https://cdn.myanimelist.net/images/manga/2/158988.jpg",
      "reportLink": "https://myanimelist.net/modules.php?go=report&type=mangapic&id=158988"
    },
    {
      "imgSrc": "https://cdn.myanimelist.net/images/manga/3/180363.jpg",
      "reportLink": "https://myanimelist.net/modules.php?go=report&type=mangapic&id=180363"
    },
    {
      "imgSrc": "https://cdn.myanimelist.net/images/manga/1/181571.jpg",
      "reportLink": "https://myanimelist.net/modules.php?go=report&type=mangapic&id=181571"
    },
    {
      "imgSrc": "https://cdn.myanimelist.net/images/manga/4/181572.jpg",
      "reportLink": "https://myanimelist.net/modules.php?go=report&type=mangapic&id=181572"
    },
    ...
```

### 17. **`GET /manga/more-info`**

- **Description**: Retrieves additional information or details about a specific manga based on its ID, providing insights beyond basic metadata.

| Parameter | Type   | Default | Description                                                       | Required |
|-----------|--------|---------|-------------------------------------------------------------------|----------|
| `id`      | string | -       | The ID of the manga for which additional information is requested | Yes      |

Example request:

```javascript
fetch('https://mangaverse-api1.p.rapidapi.com/manga/more-info?id=2', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'mangaverse-api1.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Example response:

```json
{
  "result": "Berserk: The Prototype\n(1988)\nBefore Berserk became what it is now, Miura Kentaro created a prototype chapter for the manga. The year was 1988 and he was still a student at that time. This is the prototype manga on which the Berserk manga is based.\nChapter count includes 380 chapters as of volume 41."
}
```

## Error Handling

The  API returns standard HTTP status codes to indicate the success or failure of API requests. Below are common errors and suggestions for handling them.

|Status Code|Message|Description|Suggested Handling|
|--|--|--|--|
| **400** | Bad Request | The request was malformed or missing required parameters (e.g., `domain` parameter not provided). | Verify that all required parameters are included and correctly formatted. |
| **401** | Unauthorized | Invalid or missing API key in the request headers. | Check that a valid API key is included in `x-rapidapi-key`. |
| **403** | Forbidden | Access to the requested resource is denied, possibly due to rate limits or restricted access. | Review rate limits and ensure API permissions. Retry after a delay if rate limit exceeded. |
| **404** | Not Found | The requested domain information could not be found (e.g., domain does not exist). | Check the spelling or availability of the domain. |
| **429** | Too Many Requests | The API rate limit has been exceeded. | Implement rate-limiting logic and retry after the specified rate limit reset time. |
| **500** | Internal Server Error | A server error occurred while processing the request. | Retry the request after a few seconds. If the error persists, contact API support. |
| **503** | Service Unavailable | The API service is temporarily unavailable (e.g., due to maintenance). | Retry the request later or check the API status page for maintenance alerts. |

## FAQs

### 1. What kind of data can I access through the MangaVerse API?

You can access information about manga titles, chapters, authors, genres, and user reviews.

### 2. How do I authenticate my API requests?

You will need to include your API key in the headers of your requests as specified in the API documentation.

### 3. Are there any usage limits for the API?

Yes, usage limits depend on the subscription plan you choose. Refer to the RapidAPI dashboard for specific limits.

### 4. Can I filter manga by genre?

Yes, the API provides filtering options to search for manga by different genres.

### 5. Is there support for multiple languages?

The MangaVerse API primarily supports data in English, but some titles may be available in other languages. Check individual title entries for language availability.
