# matchYourSkills
Match Your Skills (Text similarity between resume and LinkedIn job descriptions)

Methodology:

Data Scraping:

The job listings from the LinkedIn search results are scraped using selenium. The required tags are identified, and the text data were extracted using CSS selector. Data like location, company name, job type is directly extracted but for the description part, further coding is required to navigate to each job listing. After expanding the job listing, which directs to a new URL, the description text data is scraped.
The description of job listings is tokenized using the NLTK package. NLTK package of python is the Natural Language tool kit, which enables us to preprocess the data, which is unstructured and human-readable texts, to a meaningful data format for us to analyze. The description data is filtered with stop words and punctuations, which is unnecessary for our analysis; this is the data cleaning part. This scraped data is stored in a CSV file for us to access later to compare the skills from the resume.
The user uploads the resume and the keywords for the LinkedIn search. The goal is to dynamically create the LinkedIn URL from user keywords to scrape the required data
according to the user requirements.
The resume formats which are processed right now are PDF, and resume parsing of word documents will be implemented in upcoming phases. Once the user uploads the resume, the text from the resume is extracted using the pdfminer package. And using the natural language tool kit, the text data is preprocessed. The skillset from the resume is identified using a lookup skill dictionary.
This skill set is analyzed using the scraped data, which is stored in the CSV file, and the best-matched job listing URL is presented to the user. This is achieved using the text matching algorithm.
The code is attached with this report which consists of PDF resume parsing, scraping of job description and preprocessing of data.
This skill set is analyzed using the scraped data stored in the CSV file, and a score is presented to the job listings. Based on the score, the user can identify the best matching job listing. This is achieved using the text matching algorithm.
The code is attached with this report which consists of PDF resume parsing, scraping of job description and preprocessing of data.
What was most challenging part in scraping?
Scraping the entire job descriptions for each job was very challenging. LinkedIn sign in page popped up when we were trying to access the job data continuously. Dynamically changing the url to scrape the job description was another roadblock.
To overcome all of these challenges, we had a loop that opens up a new window for each job link and have ‘try except’ block to overcome No such element exceptions if the sign in page pops up. This fixed the problems and we were able to scrape all the job descriptions.
Description of extracted data:
Job ID: LinkedIn job Identifier
Date: posting date of each job
Company: Name of the hiring
Company Title: Title of Position/Job Location: Location of the job Link: Web link for the job posting
Job Description: Description of Roles and Responsibilities and detailed requirements
Exploratory Data Analysis and Data Preprocessing:
Data from the given resume is extracted and converted to string. This data undergoes several processing steps to fit into the model: -

Resume data processing:
Convert Text to Lowercase
The removal of noise is one of the most important processes in processing language data
so that the machine can more readily find patterns in the data. There is a lot of noise in text data, which comes in the form of special characters like hashtags, punctuation, and digits. If they're there in the data, computers will have a hard time understanding them. As a result, we'll need to process the data to remove these items.
It's also vital to pay attention to the case of words. If we use both upper case and lower case variants of the same word, the computer will treat them as separate things, despite the fact that they are the same.
Remove Punctuations
Punctuation adds more noise to the text data and wouldn’t add any meaningful sense to the data so as a usual process of text data cleaning we have also removed punctuation in our data.
Why aren’t we removing all the punctuations?
But we have we exceptions in our case. We are not removing all the punctations. There few that we are changing it directly as words. This is because we remove punctuations from “C++ or C#” it will match with “C”, all three are 3 different languages/skills.
Tokenization
NLTK Tokenization is a technique for breaking down a huge amount of textual data into smaller chunks in order to analyze the text's character. Machine learning models can be trained with NLTK for tokenization, and natural language processing text cleaning can be done with NLTK. With NLTK, tokenized words and phrases can be vectorized and converted to a meaningful format to be fed into algorithm.
Stemming
The process of reducing words to their root form is known as stemming. The words
"rain," "raining," and "rained," for example, have extremely similar, and in many cases identical, meanings. These will be reduced to the root form of "rain" by the stemming process. This is yet another approach to minimize noise and data complexity.
Why aren’t we stemming in our text data cleaning/preprocessing?
In our project this is not necessary because at some point skillset like “Java” and “Javascript” could be stemmed together, even though we know they are not similar. So we do not perform stemming in our data preprocessing.
Part of Speech (POS) tagging
Part of speech (POS) tagging is a method of categorizing words that provides some information about how they are used in speech.
      
There are eight primary parts of speech, each of which has its own tag.
The NLTK library has a method to perform POS tagging. The below code performs POS tagging on our data set and where we can extract the skills, because name of all the skillset/tool will be a proper noun.
This also is one of our major data analysis part where we spent most time looking into nouns and proper nouns that actually made sense of the job description data that we had to match with the skill set. We also used 2 look out excel sheet to efficiently extract the skillset from the resume, these 2 excel sheets will have the skillset and the category that falls under, for example Python-programming language and seaborn is a data visualization package.
Lookup Excel sheet for skillset
List of Job Counts per Day:
New jobs are added in a company every day. Considering one month duration 03/29/2022 to 04/26/2022, the number of jobs count per day is visualized in the bar plot below.
<img width="697" alt="image" src="https://github.com/Harshi293/matchYourSkills/assets/144385477/3b9af5d2-c397-4941-aca8-ec46bf0c55d4">

Based on the above bar plot we observed that the job postings increases with days .04/26/2022 is having the highest job postings.
Companies with highest Job Openings:
An open job vacancy is advertised in a job posting. A job posting's objective is to alert potential candidates to a new opening and encourage them to apply. Every company will be having job vacancy and will be posted. Here is the bar plot of the Top 10 companies who are having most job positions in their Company.
<img width="858" alt="image" src="https://github.com/Harshi293/matchYourSkills/assets/144385477/0f516926-7cc1-4408-a28d-794bda1bd26e">
 Based on the above bar plot we observed that Clearance jobs has highest number of job postings followed by Hanson Professional Services Inc.
Analyzing the Job Skills and Job Description by using Word Cloud:
The visual representations of the frequency of different terms included in a document are called word clouds. It prioritizes more frequently occurring words, which are larger in size than less frequently occurring ones.
Using the Word Cloud gives us a better insight of Skills which previous analysis failed to give. “Software Engineer”, “Intern”, “Software” and “Summer” are the most used words in the Job Title.
  <img width="832" alt="image" src="https://github.com/Harshi293/matchYourSkills/assets/144385477/5b991449-e91c-4709-a845-fc69cf0046d3">
 With Respect to Job Title
If we observe below based on the job Description “Engineering”, Intern” and “Software” are the, most used words.
<img width="772" alt="image" src="https://github.com/Harshi293/matchYourSkills/assets/144385477/8ca3606c-50a5-4f58-ae74-bfb4a804299b">
 With Respect to Job Description


