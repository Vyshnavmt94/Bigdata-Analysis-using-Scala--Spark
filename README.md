# Bigdata-Analysis-using-Scala--Spark
Spark Funds Investment Analysis using Scala Spark

# Introduction:
Spark Funds is an asset management company. The company wants to make investments in few other companies. The CEO of Spark Funds wants to understand the global trends in investments so that she can take the investment decisions effectively. The company has two minor constraints for investments such as: 
a)	To invest between 5 to 15 million USD per round of investment.
b)	To invest only in English-speaking countries because of the ease of communication with the companies it would invest.
In this work, an analysis on the previously available investment data is performed to identify best investment strategy for Sparks funds company.  The main strategy is to invest where other companies are investing, implying that the best sectors and countries are the ones where most investors are investing. 

# Dataset Description:
The dataset is based on the real time investment data taken from crunchbase.com [1, 2, 3]. The dataset has three data files. The company details with basic data on companies are available in companies.txt. The funding round details are present in rounds2.csv. Finally the different sector based classification of data is available in mapping.csv, which maps various category names in company’s data such as 3D printing, aerospace, agriculture, etc to eight broad sector names.  Each of these data files are explained in detail in tables [1-3]

![image](https://user-images.githubusercontent.com/41851165/69605085-32d79b00-1045-11ea-974b-d6c3808b436b.png)

![image](https://user-images.githubusercontent.com/41851165/69604952-dbd1c600-1044-11ea-8c26-d3f982ee7a7c.png)

![image](https://user-images.githubusercontent.com/41851165/69604980-f146f000-1044-11ea-911a-5fa372e727d5.png)

# Methodology:
The mail goal of this work is to identify best sectors, countries and a suitable investment type for making investments. The analysis is done in three different stages as follows:

1.	Investment type analysis: 
Comparison of the typical investment amounts in the funding types such as venture, seed, angel, private equity etc. is performed in this stage. This helps Spark Funds to choose the type that is best suited for their strategy. The funding types such as seed, venture, angel, etc. depend on the type of the company (start-up, corporate, etc.), its stage (early stage start-up, funded start-up, etc.), the amount of funding (a few million USD to a billion USD), and so on. For instance seed, angel and venture are three common stages of start-up funding. Seed/angel funding refer to early stage start-ups whereas venture funding occurs after seed or angel stages and involves a relatively higher amount of investment. Private equity type investments are associated with much larger companies and involve much higher investments than venture type. Start-ups which have grown in scale may also receive private equity funding. This means that if a company has reached the venture stage, it would have already passed through the angel or seed stages. In order to decide the funding type which is most suitable for sparks funds to invest, the total investment amount for each of the funding types is calculated. From this calculation, the funding type which has highest investment amounts is chosen.


2.	Country analysis:
This stage identifies the countries which have been most heavily invested in the past.  From the above stage the best investment type for sparks funds is found, which is to be narrowed down to countries. According to the spark funds constraints, the top English speaking countries with highest amount of funding needs to be found. To achieve this, first the top nine countries having highest amount of funding is identified and from these top three English speaking countries are chosen. Now having known the three most investment-friendly countries and the most suited funding type for Spark Funds, next stage is to find the best sectors in these countries.


3.	Sector analysis:
Understanding the distribution of investments across the eight main sectors. Even though the companies and rounds data have various sub-sectors, only eight main sectors provided in the mapping file is considered by mapping various sub-sector (primary sector) names in companies and rounds2 to its main sector. For instance, category lists such as ‘3D’, ‘3D Printing’, ‘3D Technology’, etc. are mapped to the main sector ‘Manufacturing’.
Now having each company’s main sector mapped to it, the analysis on these main sectors is to be performed. One of the other constraint of spark funds is to invest between 5 to 15 million USD per round of investment. Therefore, the final aim is to find the most heavily invested main sectors in each of the three best English speaking countries for best identified funding types in the range of  5 to 15 million USD.


# Conclusion:
Based on the data analysis performed, Sparks Funds should invest in:
	Funding type - Venture.
	Countries - USA, Britain and India.
	Top two sectors to invest in are - Others and Cleantech/semiconductors.
