# Measuring San Francisco’s Muni Bus Line Delays as Ridership Expands

San Francisco’s Muni bus lines have been in flux for the past two or more years due to the repercussions and restrictions of COVID-19. As ridership has been steadily increasing, riding the bus during peak commuting hours has proved that popular bus lines experience delays, crowding, and congestion- similar to what it was like riding the bus pre-pandemic. This project aims to look at what has been observed for those recently riding the bus and look at the muni system as a whole to see which bus lines are experiencing the most delays. In this exercise, I analyze and visualize SFMTA ridership data, SFMTA Muni route data, static GTFS data, and GTFS-RT data from the year 2019 to 2022. In looking at this time period, we will be able to see conditions of riding the bus pre-pandemic, when ridership and bus frequency was at a high while setting a baseline, to what it was like riding the bus during the height of the pandemic, and to now. In doing so, we hope to understand how the Muni bus network could alleviate some of its delays and congestion on popular lines. 

## Background

My motivation for this project was to further understand what I have been experiencing on my commute by utilizing the python skills I have learned in the past year. As I have been commuting from San Francisco to Berkeley during peak hours on the weekdays, my normal route is taking the 38 or 38 Rapid from my home to Powell street, where I then get off and walk over to the Powell BART station and transfer to rail. I observed a stark difference from my commute in 2021 to 2022, starting around February to March of this year, and was shocked by the crowding I was seeing, which I documented through photos of what I was experiencing. 

![IMG_1456](https://user-images.githubusercontent.com/98346785/167916723-4e8fbbe3-1e16-469f-9f96-27f85a6bbd75.jpg)
![IMG_0830](https://user-images.githubusercontent.com/98346785/167916748-949d5b26-1192-421d-bfc3-4ad73ca871ab.jpg)
![IMG_1459](https://user-images.githubusercontent.com/98346785/167916760-c76b061b-538c-4e87-9cc5-893530ea9d4e.jpg)
![IMG_1768](https://user-images.githubusercontent.com/98346785/167916771-c393dbd0-0192-408b-a94a-8fcf002c8244.jpg)

*Photos taken February 1st, 2022 and March 16th, 2022.*

It can be seen that there is little to no standing room on the bus during peak hours, where a rider may have to wait another 10 minutes for the next bus to arrive since there is no room on the bus that had just passed. Having this kind of crowding adds to delays- the bus idles for up to 3 minutes as the chaotic dance of people getting on and off the bus at each stop culminates to a point of stress. Social distancing is not a thing on peak commuter buses, where people are squeezing onto the bus and preventing the doors from closing, all while triggering the sensors to repeat the phrase “stand clear of the door.” 

Through reading news articles from local papers, it was clear that major employers in the central business district (CBD) were having their employees return back to the offices to some capacity in 2022- making bus lines like the 38 crowded with bringing people from residential parts of San Francisco to the CBD. (https://www.sfchronicle.com/sf/article/Mayor-Breed-wants-office-workers-to-return-to-San-16948733.php)

It is important to have a grasp on how the SFMTA Muni bus system adapted during the height of COVID-19 and now how they are trying to gain more of a sense of normalcy. In April 2020, during the height of the covid 19 pandemic- SFMTA had cut 51 of 68 bus lines in the city, leaving 17 in operation due to the stark decrease in ridership. Since then they have restored service and are now operating 51 bus routes, which include new service lines and adjusted frequencies of existing routes. Muni is expected to be running at 85% capacity of pre-pandemic levels this year, but reported ridership does not seemingly match. To understand ridership, I took SFMTA ridership data and constructed the figure below. (https://www.sfchronicle.com/sf/article/S-F-Muni-changes-are-coming-in-August-Here-s-16330618.php)

![Ridership_line](https://user-images.githubusercontent.com/98346785/167926609-c4493128-9cc2-4599-bb95-5cbd4a7775f4.png)
*Data Source: https://www.sfmta.com/reports/muni-ridership-average-weekday-ridership*

Pre-pandemic in 2019, Muni was seeing an average weekday ridership of 764,954, and currently, in 2022, they are seeing an average weekday ridership of 349,150 on their routes. 

In public comment, the SFMTA addressed recent delays in Muni due to not having enough drivers, as some drivers have called out sick and so forth. When it came to adjusted frequency and routes of lines, SFMTA has experienced a loss of revenue due to the massive decrease in ridership during the peaks of COVID-19. Operating at full capacity pre-COVID19 is not an option for the agency at this point. (https://www.sfchronicle.com/sf/article/Delays-expected-on-more-than-20-S-F-Muni-lines-16822301.php)

## Research Questions

- How have service cuts and adjusted SF Muni frequencies caused crowding and delays in Muni routes as employees are returning back to the CBD?
- Which SF Muni bus lines are experiencing the most delays as ridership has increased in the last year?

## Methodology

To understand which bus lines are experiencing the most delays, I utilize two different Python packages that digest GTFS data to showcase how routes have changed over time, along with visualizing the frequency of buses in the Muni system. The packages are Partridge and GTFS_Functions. 

First, I used Partridge to visualize the expanse of the Muni system from 2019 to 2022. In the attached figures below it can be visually seen that more bus lines running east to west in the downtown area in 2019 compared to now. From this, it can be inferred that riders are now crowding the bus lines that are in service within the area and having fewer bus options than they once did. 

![2019_GTFS](https://user-images.githubusercontent.com/98346785/168286678-8b7468a0-f3ef-4622-899d-2862be63b395.png)
![2020_GTFS](https://user-images.githubusercontent.com/98346785/168286721-5f584c22-e4fd-4527-95d2-0fa85fc9736d.png)
![2021_GTFS](https://user-images.githubusercontent.com/98346785/168286735-8ca10a6d-b2c0-4081-aff5-db4cbe5eb48d.png)
![2022_GTFS](https://user-images.githubusercontent.com/98346785/168286751-236d4ad7-b874-478d-986d-6ef406d22b48.png)

The red dots in the above images pinpoint a popular bus stop along the 38 and 38R bus routes. The Geary Street and Powell Street bus stop is in close proximity to the BART and is utilized as a transfer stop between the two modes. Riders will also take this stop from downtown San Francisco to more residential areas. To further explore the data, I wanted to see how frequent buses arrive at this stop during prime commuting hours over a 2 hour period in the afternoon. The below screenshots are output from a code that precisely does that to the static GTFS data using Partridge. 

![2019_Freq](https://user-images.githubusercontent.com/98346785/168286812-21fb0485-4130-4835-8343-6a48e42b81b9.png)
![2020_Freq](https://user-images.githubusercontent.com/98346785/168286827-619ff596-a015-49e5-b272-36ca594d4a0a.png)
![2021_Freq](https://user-images.githubusercontent.com/98346785/168286836-ea28783e-0e03-4900-b962-9606245d64ee.png)
![2022_Freq](https://user-images.githubusercontent.com/98346785/168287042-7c5008aa-0100-4601-9259-ea5818f94180.png)

Before jumping in and comparing the GTFS data to GTFS-RT data, I zoomed out of looking at the frequency of one bus route and explored the frequency of bus routes in the whole Muni system using GTFS_Functions built-in mapping capabilities that interactively show you which bus routes have a frequency of 5 minutes or less, and which are between 5 to 10 minutes, and which take longer that 10 minutes. In looking between 2019 and 2022, we can see more frequent buses in 2019 than in 2022. In using GTFS_Functions one can hover their mouse along the output maps below and see the name of the colored line that corresponds with it's set bin of frequency. 

![Route_freq_2019](https://user-images.githubusercontent.com/98346785/168292469-6b800197-5fe6-4507-90e1-a128ca8fc0b0.png)
![Route_freq_2022](https://user-images.githubusercontent.com/98346785/168292484-1c414981-69e7-47c6-bcbf-c68dfa274bef.png)


## Key Findings

![download](https://user-images.githubusercontent.com/98346785/168286647-1e6c585b-a499-4673-881d-95c05fee6f66.png)

![download (2)](https://user-images.githubusercontent.com/98346785/168334998-26ef22f8-ce41-4539-a8e5-c482f1610555.png)
![download (1)](https://user-images.githubusercontent.com/98346785/168320897-a4f27833-5494-4a9e-bef4-474dffad3aad.png)































## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/Leyla-Wah/SFMuni-Delays/edit/gh-pages/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown  

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [Basic writing and formatting syntax](https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/Leyla-Wah/SFMuni-Delays/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
