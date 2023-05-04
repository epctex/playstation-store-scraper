# Actor - Playstation Store Scraper

## Playstation Store scraper

Since Playstation Store doesn't provide a good and free API, this actor should help you to retrieve data from it.

The Playstation Store data scraper supports the following features:

-   Search any keyword - You can search any keyword you would like to have and get the results

-   Scrape lists - Scrape any list that you'd like to get from Playstation Store

-   Scrape category - You can check the categories and scrape the information of the newest updates.

-   Scrape concept - If you want to get concepts of a certain product, just type the url.

-   Scrape product - Scrape a very detailed information for each of the products that you'd like to get.

## Bugs, fixes, updates and changelog

This scraper is under active development. If you have any feature requests you can create an issue from [here](https://github.com/epctex/playstation-store-scraper/issues).

## Input Parameters

The input of this scraper should be JSON containing the list of pages on Playstation Store that should be visited. Possible fields are:

- `search`: (Optional) (String) Keyword that you want to search on Playstation Store.

- `startUrls`: (Optional) (Array) List of Playstation Store URLs. You should only provide concept, search, collection, category or product detail URLs.

- `country`: (Optional) (String) Playstation store country that you want to search on Playstation Store.

- `endPage`: (Optional) (Number) Final number of page that you want to scrape. Default is `Infinite`. This is applies to all `search` request and `startUrls` individually.

- `maxItems`: (Optional) (Number) You can limit scraped items. This should be useful when you search through the big lists or search results.

- `proxy`: (Required) (Proxy Object) Proxy configuration.

- `extendOutputFunction`: (Optional) (String) Function that takes a JQuery handle ($) as argument and returns object with data.

- `customMapFunction`: (Optional) (String) Function that takes each objects handle as argument and returns object with executing the function.

This solution requires the use of **Proxy servers**, either your own proxy servers or you can use [Apify Proxy](https://www.apify.com/docs/proxy).

### Tip

When you want to have a scrape over a specific listing URL, just copy and paste the link as one of the **startUrl**.

If you would like to scrape only the first page of a list then put the link for the page and have the `endPage` as 1.

With the last approach that explained above you can also fetch any interval of pages. If you provide the 5th page of a list and define the `endPage` parameter as 6 then you'll have the 5th and 6th pages only.

### Compute Unit Consumption

The actor optimized to run blazing fast and scrape many as listings as possible. Therefore, it forefronts all listing detail requests. If actor doesn't block very often it'll scrape 100 listings in 2 minutes with ~0.07-0.09 compute units.

### Playstation Store Scraper Input example

```json
{
  "startUrls":[
    "https://store.playstation.com/en-tr/product/EP4389-CUSA17440_00-DCLGAMEEU0000000",
    "https://store.playstation.com/en-tr/search/game",
    "https://store.playstation.com/en-tr/concept/10000886",
    "https://store.playstation.com/en-tr/category/d42c9dc6-5516-4a34-a511-c09894266d98/1"
  ],
  "search":"food game",
  "includeReviews": false,
  "proxy": {
      "useApifyProxy": true
  },
  "endPage": 5,
  "maxItems": 100
}

```

## During the Run

During the run, the actor will output messages letting you know what is going on. Each message always contains a short label specifying which page from the provided list is currently specified.
When items are loaded from the page, you should see a message about this event with a loaded item count and total item count for each page.

If you provide incorrect input to the actor, it will immediately stop with failure state and output an explanation of what is wrong.

## Playstation Store Export

During the run, the actor stores results into a dataset. Each item is a separate item in the dataset.

You can manage the results in any languague (Python, PHP, Node JS/NPM). See the FAQ or <a href="https://www.apify.com/docs/api" target="blank">our API reference</a> to learn more about getting results from this Playstation Store actor.

## Scraped Playstation Store Properties

The structure of each item in Playstation Store looks like this:

### Item Detail

```json
{
  "url": "https://store.playstation.com/en-tr/product/EP9000-BCES00850_00-LBPDLCORIGCO0083",
  "id": "EP9000-BCES00850_00-LBPDLCORIGCO0083",
  "privacyPolicy": null,
  "publisherName": "Sony Interactive Entertainment Europe",
  "descriptions": [
    {
      "type": "LONG",
      "subType": "NONE",
      "value": "Game For Anything<br>Turn your Sackboy® into a creative genius with this Game Writer costume, complete with a fashion-statement moustache and ironic T-shirt.<br><br>Sackboy® Says:<br>• This costume is also available to download from PlayStation®Store in the Sackboy's Casual Friday Costume Pack.<br><br>This add-on is for LittleBigPlanet™ 2.<br><br>Buy this add-on for LBP™ 2 and get the LittleBigPlanet™ Karting, LittleBigPlanet™ PlayStation®Vita and LittleBigPlanet™ 3 (PS4™ and PS3™) versions at NO EXTRA COST.<br><br>After purchase, open the PlayStation®Store “Download List” to find this add-on ready to be downloaded.<br><br>1-4 Players, 1300MB minimum space required, HDTV screen resolution: 720p, Network Features, Network Players 2-4, PlayStation®Move Optional<br><br>Download of this product is subject to the Sony Entertainment Network Terms of Service/User Agreement and any specific additional conditions applying to this product. If you do not wish to accept these terms, do not download this product. See Terms of Service for more important information.<br> PS4: One-time licence fee to download to multiple PS4 systems. Sign in to PSN is not required to use this on your primary PS4, but is required for use on other PS4 systems.<br>PS3: One-time fee for use of downloads on up to 2 activated PS3 systems.<br>PS Vita: One-time fee for use of downloads on up to 3 activated compatible Portable Console systems.<br>See Health Warnings for important health information before using this product.<br>Library programs ©Sony Computer Entertainment Inc. exclusively licensed to Sony Computer Entertainment Europe. Software Usage Terms apply, See eu.playstation.com/legal for full usage rights.<br><br>LittleBigPlanet™ 2 ©2010 Sony Computer Entertainment Europe. Published by Sony Computer Entertainment Europe. Developed by Media Molecule. “LittleBigPlanet”, “LittleBigPlanet logo”, “Sackboy” and “Sackgirl” are trademarks or registered trademarks of Sony Computer Entertainment Europe. All rights reserved."
    }
  ],
  "localizedGenres": null,
  "releaseDate": "2013-07-31T00:00:00Z",
  "spokenLanguages": [],
  "screenLanguages": [],
  "platforms": [
    "PS4"
  ],
  "contentRating": {
    "authority": "PEGI",
    "description": "PEGI 7+",
    "name": "PEGI_7",
    "url": "https://image.api.playstation.com/grc/images/ratings/hd/pegi/7.png",
    "interactiveElements": [],
    "descriptors": [
      {
        "description": "Fear",
        "name": "PEGI_FEAR",
        "url": "https://image.api.playstation.com/grc/images/descriptors/hd/pegi/fear.png"
      },
      {
        "description": "Online",
        "name": "PEGI_ONLINE",
        "url": "https://image.api.playstation.com/grc/images/descriptors/hd/pegi/online.png"
      },
      {
        "description": "Violence",
        "name": "PEGI_VIOLENCE",
        "url": "https://image.api.playstation.com/grc/images/descriptors/hd/pegi/violence.png"
      }
    ]
  },
  "name": "Game Writer Costume",
  "concept": null,
  "skus": [
    {
      "__ref": "Sku:EP9000-BCES00850_00-LBPDLCORIGCO0083-E001"
    },
    {
      "__ref": "Sku:EP9000-BCES00850_00-LBPDLCORIGCO0083-E002"
    }
  ],
  "isAgeRestricted": false,
  "activeCtaId": "ADD_TO_CART:ADD_TO_CART:EP9000-BCES00850_00-LBPDLCORIGCO0083-E001:OUTRIGHT",
  "webctas": [
    {
      "__ref": "GameCTA:ADD_TO_CART:ADD_TO_CART:EP9000-BCES00850_00-LBPDLCORIGCO0083-E001:OUTRIGHT"
    }
  ],
  "isInWishlist": false,
  "isWishlistable": true,
  "edition": null,
  "media": [
    {
      "type": "IMAGE",
      "role": "MASTER",
      "url": "https://image.api.playstation.com/cdn/EP9000/BCES00850_00/cbixxOGGNeGKWQpapaWWQ2HKRaSQP3NA.png"
    }
  ],
  "prices": [
    "4,50 TL"
  ],
  "editions": []
}
```

## Contact
Please visit us through [epctex.com](https://epctex.com) to see all the products that is available for you. If you are looking for any custom integration or so, please reach out to us through the chat box in [epctex.com](https://epctex.com). In need of support? [devops@epctex.com](mailto:devops@epctex.com) is at your service.
