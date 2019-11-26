# Bigdata-Analysis-using-Scala--Spark
Spark Funds Investment Analysis using Scala Spark

# Introduction:
Spark Funds is an asset management company. The company wants to make investments in few other companies. The CEO of Spark Funds wants to understand the global trends in investments so that she can take the investment decisions effectively. The company has two minor constraints for investments such as: 
a)	To invest between 5 to 15 million USD per round of investment.
b)	To invest only in English-speaking countries because of the ease of communication with the companies it would invest.
In this work, an analysis on the previously available investment data is performed to identify best investment strategy for Sparks funds company.  The main strategy is to invest where other companies are investing, implying that the best sectors and countries are the ones where most investors are investing. 

# Dataset Description:
The dataset is based on the real time investment data taken from crunchbase.com [1, 2, 3]. The dataset has three data files. The company details with basic data on companies are available in companies.txt. The funding round details are present in rounds2.csv. Finally the different sector based classification of data is available in mapping.csv, which maps various category names in company’s data such as 3D printing, aerospace, agriculture, etc to eight broad sector names.  Each of these data files are explained in detail in tables [1-3]

![image](https://user-images.githubusercontent.com/41851165/69604895-bf358e00-1044-11ea-9205-a0263500f9e1.png)

Table 1: Company details in companies.txt file

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

Experiments and Results:
The experiments are performed as per the three stages mentioned in the methodology. Figure 1 and 2 shows the sample data of the companies.txt and rounds.csv respectively.  The companies data has total of 66368 rows and rounds data has only 66370 rows, which means two data points are missing in companies data. Now in order to perform the first stage of analysis, the companies data needs to be merged with the rounds.csv data. The two data frames are joined on the permalink column of rounds dataframe, by lowercasing all permalink data in both companies and rounds dataframes. The join operation is performed by intersection of keys from both dataframes. The resulting merged dataframe, master_frame has total of 114942 rows. Figure 3 shows the merged dataframe master_frame. The master_frame has many attributes which are not useful for the analysis such as funding_round_code,funding_round_permalink,funded_at,permalink,homepage_url,state_code,region, city, founded_at,status.  The master_frame id cleaned by dropping all of these non-contributing attributes and null values. The cleaned master_frame has total of 88529 rows. Figure 3 shows the sample data of master_frame.

Figure 1:  company details in companies.txt.

Figure 2:  Funding rounds details in rounds.csv.

                                         Figure3:  Master_frame sample data.

The cleaned master_frame is now analysed to obtain the funding type with highest investment amounts. The number of investment and the sum of investment for each funding type is calculated from the master_frame. From figure 4, it is observed that the funding type Venture has the highest number of investments as well as highest investment amount. 







(a)	                                                             (b)
Figure 4: Master_frame investment type analysis: (a) number of investment per type, (b) investment amount for each type.

Now after filtering out the master_frame with investment type as venture, the country analysis is performed. As per spark funds constraint, the investment need to be done in top English speaking countries. The english speaking countries are short listed as USA, GBR, IND, by manual analysis of the list provided for english as official language list. Figure 5 shows the filtered out master_frame with investment type as venture and top 3 english speaking countries as United States of America (USA), Britain (GBR), India (IND). The country analysis result in figure 6 shows that USA has highest number of investment as well as highest investment amount.

 
Figure 5: Filtered master_frame with investment type venture and english speaking countries USA, GBR, IND.





(a)	                                                                 (b)
Figure 6: Master_frame country analysis: (a) investment amount for each country,               (b) number of investment per country.

The third stage of analysis is performed sector wise on the eight main sectors available in mapping.csv file. Figure 7 shows the sample data of mapping.csv file. The mapping data has the eight main sectors in a pivoted format, which is unpivoted and used to map each primary sector in master_frame to one of the eight main sectors. The mapped master frame is filtered out to investment amount between 5-15 million USD, as per the constraint of spark funds. The master_frame is further filtered to obtain three dataframes D1, D2, D3 based on the country code. The sector based analysis is performed on these country filtered dataframe. 

Figure 7: Sector details in mapping.csv.

The results of sector based analysis is shown in figure 8 & 9 respectively. Figure 8 shows the investment amounts of each of the eight main sector for each countries USA, GBR and IND. Similarly, figure 9 shows the number of investment in each main sectors for these three countries. From the results obtained, it is inferred that the best investment strategy for spark funds is to invest in Others main sector in USA with investment type as venture. Further investment can be made on Britain and India under main sectors Cleantech/semiconductors and Others respectively.

                                                                                                	    (a)			                         (b)		                                    (c)                                     
  Figure 8: Total investment amounts of each main sectors in countries:  (a) USA, (b) GBR, (c) IND.


(a)			                         (b)		                                    (c)                                     
 Figure 9: Total number of investments in each main sectors in countries:  (a) USA, (b) GBR, (c) IND.

Conclusion:
Based on the data analysis performed, Sparks Funds should invest in:
	Funding type - Venture.
	Countries - USA, Britain and India.
	Top two sectors to invest in are - Others and Cleantech/semiconductors.
