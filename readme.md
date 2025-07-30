# AutoUNMS AI Agent for Web Scraping & Summarization

**AutoUNMS** is an AI-driven web scraping and summarization agent built using [n8n](https://n8n.io/). It automates intelligent web search, content scraping across multiple pages, and summarization using the **Serper API** (Google search) and **Gemini API** (AI summarizer), producing clean, summarized HTML content.

---

## 🚀 Features

- 🔘 **Manual Trigger** to control when the workflow runs
- 🔍 **Search via Serper API** to simulate Google-style search queries
- 🔗 **Link Parsing & Batch Control** to loop through 5 pages with 5 results per page (25 total)
- 🌐 **Web Scraping** using HTTP GET requests on each result
- 🧼 **HTML Cleaning** to strip out tags like `<script>` and `<style>`
- ✨ **Summarization via Gemini API** to convert raw scraped text into readable insights
- 🧾 **HTML Output** to present all summaries in a clean HTML file format
- 🔄 Designed for flexibility and automation with minimal manual effort

---

## 🧠 Workflow Breakdown

1. **Manual Trigger**
   - Start the process manually from within the n8n UI.

2. **HTTP Request – Serper API**
   - Searches for the query term using Serper (Google alternative).
   - You can configure how many pages and results you want.

3. **Code Node – Link Splitter**
   - Extracts links from Serper API results and structures them into a flat list of URLs.

4. **Batch & Pagination**
   - Handles multiple pages (e.g., 5) with 5 links per page.
   - Uses `SplitInBatches` node to loop through the results in manageable chunks.

5. **HTTP Request – Scraper**
   - Sends a GET request to each link to retrieve the raw HTML content.

6. **Code Node – HTML Cleaner**
   - Strips unnecessary tags (`<script>`, `<style>`, etc.)
   - Extracts plain readable text content.

7. **Batching for Gemini API**
   - Groups cleaned results into batches for efficient summarization.

8. **Gemini API – Summarization**
   - Summarizes cleaned article content using Gemini.

9. **Code Node – HTML Converter**
   - Converts each summary into a structured HTML block.

10. **Output**
    - Saves the final HTML content as a `.html` file or sends it to a storage service (like Google Drive).

---

Example Output

Real Estate Listing (Cairo Apartments)

```text
City       | Price
-----------|----------
Cairo      | 1500000
Giza       | 950000
Nasr City  | 1200000
New Cairo  | 1700000
Heliopolis | 1400000

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



