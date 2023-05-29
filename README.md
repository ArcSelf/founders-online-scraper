# Thomas Jefferson Reference Scraper

This project is a Python script that scrapes text data from Thomas Jefferson's letters on the Founders Online website and identifies references related to specific keywords. It utilizes the `requests` library for making HTTP requests, the `BeautifulSoup` library for parsing HTML content, and the `spacy` library for natural language processing.

## How it Works

1. The script loads a pre-trained English language model from Spacy (`en_core_web_sm`) and adds a sentencizer to the pipeline.
2. The base URL for Thomas Jefferson's letters on the Founders Online website is set.
3. The script specifies the number of pages to process and prepares a list of keywords related to various topics.
4. The keywords are converted to their lemma forms and stored in a set for efficient searching.
5. The script initializes a reference count and defines the path for an Excel workbook.
6. If the workbook exists, it is loaded; otherwise, a new workbook is created.
7. The script selects the worksheet for Thomas Jefferson's references or creates a new one if it does not exist.
8. If the sheet is empty, it sets the column headers and alignment.
9. For each page to be processed (determined by the `num_pages` variable):
    - A random page number is generated within the range of available pages.
    - The URL for the current page is constructed.
    - A GET request is sent to the URL, and the HTML content is obtained.
    - The text within the `<p>` tags on the page is extracted using BeautifulSoup.
    - The text is processed using the Spacy model to identify matching paragraphs based on the keywords.
    - The title of the page is extracted from the `<h1>` tag with class "title".
    - Matching references are added to the worksheet, including the page number, keywords, title, URL, and the matching paragraph.
    - The reference count is incremented, and the reference details are printed.
10. Once all the pages are processed, the workbook is saved.
11. The total reference count is printed.

## Getting Started

To use this script, follow these steps:

1. Make sure you have Python 3.x installed on your system.
2. Install the required dependencies by running the following command:

pip install requests beautifulsoup4 spacy openpyxl

3. Download or clone this repository to your local machine.
4. Open the script file (`reference_scraper.py`) in a text editor or Python IDE.
5. Modify the script if necessary, such as changing the `num_pages` variable or updating the `keywords` list.
6. Run the script by executing the following command in your terminal or command prompt:

python reference_scraper.py

7. The script will scrape the specified number of pages, identify matching references, and store them in an Excel workbook.
8. The total number of references found will be displayed once the script finishes.

## Notes

- The script uses a random page selection method to retrieve diverse references. You can adjust the `num_pages` variable to control the number of pages processed.
- The Excel workbook path is set to `"references.xlsx"`. If the file does not exist, a new workbook will be created in the same directory as the script.
- Each time the script is run, it will append new references to the existing worksheet or create a new worksheet if it does not exist.
- The script prints the details of each reference found, including the page number, matched keywords, title, URL, and the matching paragraph. You can comment out or remove the print statements if you don't need them.

Feel free to modify and customize the code according to your needs. If you encounter any issues or have suggestions for improvements, please feel free to contribute or reach out to the project's author.

**Note: It's always a good practice to include a license file (e.g., MIT License) and proper attribution to any external libraries used in your project.**

Enjoy using the Thomas Jefferson Reference Scraper! If you have any questions, please don't hesitate to ask.
