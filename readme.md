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


## 📦 Example Output

### 🏙️ Real Estate Listing (Cairo Apartments)

```text
City       | Price
-----------|----------
Cairo      | 1500000
Giza       | 950000
Nasr City  | 1200000
New Cairo  | 1700000
Heliopolis | 1400000

🛠️ Technologies Used
n8n – Open-source workflow automation

Serper API – Google search result extraction (https://serper.dev)

Gemini API – AI summarization (https://ai.google.dev)

JavaScript – Code nodes for parsing and cleaning

HTML – Final output format

Manual Trigger – To allow full user control over execution



🧪 Use Cases
📰 News aggregation and summarization

📊 Market intelligence from multiple sources

🎓 Educational content simplification

🛒 Product comparison from various sites

📚 Multi-page content extraction and analysis

📁 File Structure
b/n8n-workflows
  └── autounms-scraper-summary.json   # Full n8n workflow (importable)
/scripts
  ├── clean-html.js                   # JavaScript for HTML cleaning
  ├── split-links.js                  # JavaScript for batching links
/README.md


🧰 Setup Instructions
Install n8n (locally or via Docker/cloud).

Import Workflow: Use the .json file to import the AutoUNMS workflow.

Add Credentials:

 Serper API Key – https://serper.dev

 Gemini API Key – https://ai.google.dev

Run the Manual Trigger

Input Query when prompted (e.g., "latest AI trends").

Let the workflow run—scrape, clean, summarize, and generate your HTML report.

📜 License
MIT License
© 2025 Youssef Elzahar – Built with n8n, AI, and automation 💡


