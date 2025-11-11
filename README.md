# E-Commerce-Funnel-Analysis
📈 Funnel analysis of an e-commerce site in Python. Merges &amp; segments user data (by device, sex, time) to find conversion bottlenecks and device-specific bugs.

This repository contains a comprehensive funnel analysis for a simple 4-page e-commerce website. The analysis, contained in the Funnel_Analysis.ipynb Jupyter notebook, investigates user conversion paths, identifies significant drop-off points, and uncovers time-sensitive and device-specific issues affecting the site's performance.

<img width="2048" height="2048" alt="image" src="https://github.com/user-attachments/assets/ee54747b-b78a-4327-95bc-846206615b6d" />


****🎯 Project Goal****

The primary goal of this analysis is to:

**Define the Conversion Funnel:** Map the specific sequence of pages users take from visiting the home page to completing a purchase.

**Calculate Conversion Rates:** Measure the overall conversion and step-to-step drop-off rates.

**Identify Bottlenecks:** Pinpoint the exact stages in the funnel where the most users are lost.

**Segment Analysis:** Compare user behavior across different demographics (Device and Sex) to find discrepancies.

**Analyze Trends:** Perform a time-series analysis to see if and when conversion problems started.

**Provide Actionable Insights:** Deliver clear, data-driven recommendations to the product and engineering teams.


****funnel The Conversion Funnel****

The website's conversion funnel is defined by four sequential pages:

**Home Page (/home):** The initial landing page for all users.

**Search Page (/search):** Users search for products.

**Payment Page (/payment):** Users enter payment information.

**Payment Confirmation Page (/confirmation):** The final conversion step after a successful purchase.


****💾 Data Sources****

The analysis merges data from five separate files to build a complete view of the user journey.

**user_table.csv:** (Provided) User-level dimension data, including user_id, date (join date), device, and sex.

**search_page_table.csv:** (Provided) A log of users who successfully visited the search page.

**home_page_table.csv:** (Required by Notebook) A log of users who visited the home page.

**payment_page_table.csv:** (Required by Notebook) A log of users who reached the payment page.

**payment_confirmation_table.csv:** (Required by Notebook) A log of users who successfully completed a purchase.



****📈 Analysis Workflow****

The Funnel_Analysis.ipynb notebook follows a structured workflow:

**Data Loading:** All five CSV files are loaded into separate pandas DataFrames.

**Data Merging:** A master funnel DataFrame is constructed by sequentially left-joining the page tables, starting from home_page. This technique correctly maps each user's progression, showing NaN values for steps they did not reach.
This master funnel table is then inner-joined with the user_table to enrich the data with user attributes (device, sex).

**Overall Funnel Calculation:** The overall conversion and drop-off rates are calculated for the entire user base.

**Segmentation Analysis:** The data is grouped by device (Mobile vs. Desktop) and sex (Male vs. Female) to calculate and visualize segmented funnel performance.

**Time-Series Analysis:** The date column from the user_table is converted to datetime objects.
The data is grouped by date and device to calculate the daily conversion rates for each step of the funnel.
These daily rates are plotted to identify when specific conversion problems began.


****💡 Key Findings & Actionable Insights****

The analysis uncovered two distinct and critical problems:

**Insight 1:** A Sudden Drop-off Began in Early March

The time-series analysis reveals a sudden, sharp decline in conversion rates at the beginning of March 2015. This problem is device-specific:

**For Mobile Users:** The problem is moving from the Home Page to the Search Page.

**For Desktop Users:** The problem is moving from the Search Page to the Payment Page.

**Recommendation:** This strongly suggests a technical bug or a flawed A/B test was introduced in early March. The engineering team should immediately investigate code changes or experiments pushed at that time that could have affected these specific page transitions differently for mobile and desktop users.

**Insight 2:** Desktop Conversion is Persistently Low

Separate from the March bug, the analysis shows that Desktop users have a consistently and significantly lower overall conversion rate than Mobile users. This is not a new problem; it has been present in the data from the beginning.

**Recommendation:** This is a major strategic issue, not a simple bug. The company is losing a large amount of potential revenue from its desktop audience. A full review of the desktop user experience (UX) is required. We recommend:

Running user experience (UX) research sessions with desktop users.
A/B testing different layouts, calls-to-action, and form designs on the desktop search and payment pages.
Investigating potential sources of friction, such as a complex checkout process on desktop.


****📊 Visualizations in the Notebook****

The analysis notebook generates several key visualizations to support these findings:

**Overall Funnel:** A bar chart showing the user drop-off at each of the 4 steps.

**Segmented Funnels (Device & Sex):** Grouped bar charts comparing the conversion rates for Mobile vs. Desktop and Male vs. Female.

**Daily Conversion Rates (Time-Series):** Line plots showing the daily conversion rates for each funnel step, segmented by device, which clearly highlights the drop in early March.


****🚀 How to Run the Analysis****

**Clone the repository:**

git clone [https://github.com/YOUR_USERNAME/funnel-analysis-repository.git](https://github.com/YOUR_USERNAME/funnel-analysis-repository.git)
cd funnel-analysis-repository


**Create a virtual environment (Recommended):**

python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate


**Install the required libraries:**

pip install pandas matplotlib seaborn jupyterlab


(You can also create a requirements.txt file with these packages)

**Add the missing data files:**
Ensure home_page_table.csv, payment_page_table.csv, and payment_confirmation_table.csv are present in the root directory.

**Run Jupyter Lab:**

jupyter lab


Open and run the Funnel_Analysis.ipynb notebook.

**🌟 About Me**

Hi, I'm Deepanjali Srivastava

I am a data-driven professional with a passion for transforming raw data into actionable insights. I specialize in data analytics, data warehousing, and business intelligence, with a deep expertise in SQL.

My goal is to help organizations solve complex problems and make strategic decisions by building robust data solutions and uncovering hidden patterns. I am meticulous, a strong problem-solver, and thrive in environments where I can leverage data to drive growth and efficiency.

**🚀 What I Do**

📈 Data Analytics: Performing in-depth exploratory data analysis (EDA) and querying to answer key business questions.

🧰 Data Warehousing: Designing and building scalable data models (Star/Snowflake schemas) and ETL/ELT pipelines.

📊Business Intelligence: Creating reports and dashboards that provide clear, actionable insights.

⚙️ Optimization: Writing complex, high-performance SQL queries and optimizing database performance.

**🛠️ My Tech Stack**

Databases & Warehouses: PostgreSQL, MySQL, SQL Server, BigQuery, Snowflake

BI Tools: Tableau, Power BI, Looker

Languages:SQL, Python (Pandas, NumPy)

**📫 Let's Connect**

I am always open to discussing new projects, sharing ideas, or exploring new opportunities.

LinkedIn: (https://www.linkedin.com/in/deepanjali-srivastava-762749243/)
