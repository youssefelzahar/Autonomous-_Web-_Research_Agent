# 🕸️ AutoUNMS AI Agent for Web Scraping

This project is a web scraping AI agent built using **n8n**. It allows you to search and scrape data from the web using a **manual trigger** and returns summarized results in HTML format.

## 🔄 Workflow Overview

1. **Manual Trigger** – Initiates the workflow manually.
2. **HTTP Request (Search)** – Uses the **Serper API** to search Google for relevant links.
3. **Code Node** – Extracts URLs from the search results and prepares a list of links (5 pages, 5 links per page).
4. **SplitInBatches** – Iterates through the list of links in batches.
5. **HTTP Request (Scraping)** – Sends GET requests to each link to fetch the HTML content.
6. **Code Node (Cleaning)** – Cleans the raw HTML and removes unwanted tags like `<script>` and `<style>`.
7. **Gemini API** – Summarizes the cleaned content into readable text.
8. **HTML File Conversion** – Converts the final summarized data into a downloadable HTML file.

## 📥 Input

- **Trigger**: Manual (from n8n UI)
- **Search Term**: For example: `Cairo apartment price`

## 📤 Example Output

Real Estate Listing (Cairo Apartments)

| City       | Price   |
|------------|---------|
| Cairo      | 1500000 |
| Giza       | 950000  |
| Nasr City  | 1200000 |
| New Cairo  | 1700000 |
| Heliopolis | 1400000 |

---

## 🛠️ Technologies Used

- **n8n** – Workflow automation engine
- **Serper API** – Google Search API for scraping links
- **Gemini API** – Summarizes raw content into clean text
- **JavaScript** – Custom code nodes for text cleaning and parsing
- **HTML** – Output format for structured results
- **Manual Trigger** – Used to manually initiate scraping
- **HTTP Request Nodes** – To call external APIs and fetch HTML pages
- **SplitInBatches Node** – For looping over links in batches

## 📄 Output Format

- The final result is exported as a structured HTML file with the summarized and cleaned content.

## 📌 Use Cases

- Real estate listings
- Product price comparison
- News summarization
- Academic or research scraping

## 🔧 How to Use
Install n8n (locally, cloud, or Docker).

Import Workflow: Load the .json into n8n.

Set API Credentials:

Serper API Key: https://serper.dev

Gemini API Key (optional): https://ai.google.dev

Run Manual Trigger

Input Query: For example: "Cairo apartment prices"

Receive Output: Clean table of City and Price, downloadable or saved to file.

## 📜 License
MIT License
© 2025 Youssef Elzahar – Built with n8n, AI, and automation 💡

