# Major League Hacking Past Seasons
A list of all past MLH hackathons grouped by season and year.

## Scraping Process
Paste this following script into your browsers console REPL. Afterwards, your clipboard should now have a copy of that seasons hackathons in JSON
```javascript
let scrape = () => ({
    year: $("h1").text().match(/[0-9]+/g)[0],
    season: $("h1").text().match(/Spring|Fall|North America|Europe/g)[0],
    events: $(".event-wrapper").map((_, e) => {
      e = $(e);
      return {
        name: e.find(".event-name").text(),
        url: e.find(".event-link").attr("href"),
        date:{
          start: new Date(e.find(`meta[itemprop="startDate"]`).attr("content")),
          end: new Date(e.find(`meta[itemprop="endDate"]`).attr("content"))
        },
        location: {
          city: e.find(`span[itemprop="city"]`).text(),
          state: e.find(`span[itemprop="state"]`).text(),
        }
      }
    }).toArray()
  });

var lines = JSON.stringify([scrape()], null, 2);
lines = lines.substring(lines.indexOf("\n") + 1);
lines = lines.substring(lines.lastIndexOf("\n"), -1);
lines += ",\n";
copy(lines);
lines
```

## Seasons
What hackathons are in this dataset?  
| Season                                             | Region        | Start Date       | End Date         | Events |
|----------------------------------------------------|---------------|------------------|------------------|--------|
| [Fall 2013](https://mlh.io/seasons/f2013/events)   | North America | 6 September 2013 | 13 October 2013  | 5      |
| [Spring 2014](https://mlh.io/seasons/s2014/events) | North America | 17 January 2014  | 27 July 2014     | 38     |
| [Fall 2014](https://mlh.io/seasons/f2014/events)   | North America | 30 August 2014   | 6 December 2014  | 36     |
| [Fall 2014](https://mlh.io/seasons/f2014/events)   | Europe        | 4 October 2014   | 7 December 2014  | 10     |
| [Spring 2015](https://mlh.io/seasons/s2015/events) | North America | 10 January 2015  | 16 August 2015   | 60     |
| [Spring 2015](https://mlh.io/seasons/s2015/events) | Europe        | 7 February 2015  | 28 June 2015     | 18     |
| [Fall 2015](https://mlh.io/seasons/f2015/events)   | North America | 7 August 2015    | 29 November 2015 | 52     |
| [Fall 2015](https://mlh.io/seasons/f2015/events)   | Europe        | 2 October 2015   | 20 December 2015 | 14     |
| [Spring 2016](https://mlh.io/seasons/s2015/events) | North America | 15 January 2016  | 29 May 2016      | 91     |
| [Spring 2016](https://mlh.io/seasons/s2015/events) | Europe        | 30 January 2016  | 15 May 2016      | 25     |
| [2017](https://mlh.io/seasons/na-2017/events)      | North America | 27 August 2016   | -                | 163    |
| [2017](https://mlh.io/seasons/eu-2017/events)      | Europe        | 7 October 2016   | -                | 36     |
| [2018](https://mlh.io/seasons/na-2018/events)      | North America |                  |                  |        |
| [2018](https://mlh.io/seasons/eu-2018/events)      | Europe        |                  |                  |        |
| [2019](https://mlh.io/seasons/na-2019/events)      | North America |                  |                  |        |
| [2019](https://mlh.io/seasons/eu-2019/events)      | Europe        |                  |                  |        |
