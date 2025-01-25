## UAE Foodie Dashboard
### WebScraping -Talabat-data-with-python-selenium and Visualization with Power-Bi
Discover the UAE's top dining options with insights extracted from Talabat, a leading online food delivery platform. This interactive dashboard showcases highly rated restaurants, their best-selling dishes, delivery locations, and diverse cuisines to help you find your next favorite meal effortlessly.

**Problem statement** : Web Scrape restaurant names their ratings, reviews, cuisines, best-selling dishes, and delivery locations in the UAE from Talabat.com to provide actionable insights and enabling users to explore and help in dining decisions in a seamless and interactive manner ?

**My approach** : I used the Selenium package to web scrape restaurant details from the website (detailed approach explained below). The extracted data was initially unstructured and largely textual, so I utilized regular expressions to parse and extract specific information, such as cuisines, best-selling dishes, and delivery locations, ensuring it was suitable for dashboard creation After cleaning and transforming the data, I saved it in an Excel file and built an interactive Power BI dashboard. By using advanced DAX functions and combining custom visuals through SVG classes, Ito make it impactful.

Data sourced from - [talabat.com/uae/restaurants](https://www.talabat.com/uae/restaurants)

This project blends technology, creativity, and data storytelling to uncover trends and insights in the vibrant restaurant landscape of the UAE. 
- ⚙️ **Data Source**: Scraped from Talabat UAE using Python Selenium.
- 🧹 **Data Preparation**: Processed and cleaned with Python Pandas and Excel.
- 📂 **Scope**: While the website features over 1,000 restaurants, this analysis focuses on a practical subset of 132 restaurants as of January 2025.

![image](https://github.com/user-attachments/assets/39c617c2-89e5-49de-9f30-debed9000f6d)

![image](https://github.com/user-attachments/assets/20d39a89-1ea0-4b75-a4e6-35fe87d9690d)

![image](https://github.com/user-attachments/assets/be09ce0e-2adc-402d-b741-9460d24b6267)

**[Dashboard Link](https://shorturl.at/tTxyP)**

**Note:** The information reflects data from Talabat.com as of January 2025. It does not represent all UAE restaurants or top- ranked restaurants but is based on the limited extracted data from the website for this project.


### **Data Extraction Using Selenium from Talabat UAE**
The task was to scrape restaurant details from the Talabat UAE website using Selenium, a powerful tool for web automation. The goal was to visit multiple restaurant pages, gather their ratings, cuisine types, and descriptions, and store the data for further analysis. Here's how I approached it and the key Selenium functions used to achieve this.
The process started by setting up the **Chrome WebDriver** through the `Service` function. This is essentially what allows Selenium to automate the Chrome browser on my machine. I used the **`driver.get()`** function to open the Talabat website and start the data extraction process. The website lists restaurants on multiple pages, so I needed to handle pagination and ensure the script could move through several pages to fetch more data.
Here I mainly used **XPATH** function in webpage to locate specific elements in webpage.

And futher I used the **`find_elements(By.XPATH)`** method to locate all the restaurant links on the page. This step was crucial because it identified the clickable links for each restaurant, allowing me to navigate to their individual pages. To ensure smooth scrolling (as some elements were out of view), I used **`execute_script()`**, which is a neat trick to scroll down to a specific restaurant before clicking on it.

After opening a restaurant's page, I applied **WebDriverWait** to make sure all elements like the restaurant's name, rating, and description were fully loaded before attempting to extract the information. This is an important step because websites often load content dynamically, and rushing through can result in missed data or errors. I also used regular expressions (`re.search()`) to extract numeric ratings from the text and clean up the cuisine information. The extracted details were then added to a list for later use.

One of the main challenges was handling errors gracefully. For example, if a restaurant's page didn't load properly or showed a "Page Not Found" error, the script handled it by navigating back to the main page and continuing with the next restaurant. This was done using try-except blocks, which ensure that the script doesn't crash when it encounters an issue. Additionally, I used **`driver.back()`** to return to the previous page and continue from where it left off.

Another challenge was dealing with pagination. After processing each page, I used **`find_element()`** to locate the "Next" button and clicked on it to move to the next set of restaurants. To make sure the next page loaded completely, I used **explicit wait function** which is **`EC.element_to_be_clickable()`**, to make sure that the script didn't proceed until the "Next" button was interactable.

Overall, the key Selenium functions that played a big role in this project were:
- **`driver.get()`** to open the website.
- **`find_elements(By.XPATH)`** to locate multiple web elements on a page.
- **`execute_script()`** to scroll into view for hidden elements.
- **`click()`** to interact with clickable items.
- **WebDriverWait** to wait for elements to load.
- **`driver.back()`** to return to the previous page.


