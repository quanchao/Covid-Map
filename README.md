# Covid-19 Infection Map

This is the repository of the source code for the Covid-19 Infection Map([quanchao.me](http://quanchao.me)). The interactive maps enables people to see the trends of Covid-19 in United States from Mar.1 to Mar.31. The dataset is collected from the CDC official source as well as the Tweet as the unconfirmed source.
## Data Sources 
1. [tweet](https://developer.twitter.com/en/docs/tweets/search/api-reference/get-search-tweets)
2.  [CDC](https://www.cdc.gov/)

This is the sample data after preprocessing.

``` 
CDC data:

{

	"longitude": -119.4179,
	"latitude": 36.7783,
	"messgae": Confusion prevails overr how many people in Iran have been infected, and how many have died,, from the coronavirus. \u00a0 https://t.co/FiAQxu6uB"
}

Tweet Data:

{

	"Alabama":
		{"2020-03-13":{"cofirmed": "6", "deaths":"0"}
		{"2020-03-14":{"confirmed":"12", "deaths": "0"}
}

``` 

## Timechart of U.S. cases

The core part of the codes is to upate information on the map according to the selected data.
```
 function updateCorona(date) {
    for (var i = 0; i < statesData["features"].length; i++) {
        stateName = statesData.features[i].properties.name
        if (coronaData[stateName] == undefined) {
            console.warn(stateName);
            statesData.features[i].properties.density = 0;
        } else if (coronaData[stateName][date] == undefined) {
            statesData.features[i].properties.density = 0;
        } else {
            statesData.features[i].properties.density = coronaData[stateName][date]["confirmed"];
       	}                    
    }
}
```

![video](image/timetrend.gif)





## Tweet detction
![tweet](image/tweet.gif)