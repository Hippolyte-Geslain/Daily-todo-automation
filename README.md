# Daily Todo Automation

This repository automates the summarization of daily tasks, meetings, and events using Google Gmail and Google Calendar via n8n workflow automation.

## Setup

### Prerequisites
- Node.js (v20 or later)
- n8n CLI
- Google Calendar OAuth2 API credentials
- Gmail OAuth2 API credentials
- OpenAI API credentials

### Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/Daily-todo-automation.git
   cd Daily-todo-automation
   ```

2. Install dependencies:
   ```bash
   npm install -g n8n
   ```

3. Set up your credentials:
   - Create a `.env` file in the root directory.
   - Add your Google Calendar, Gmail, and OpenAI API credentials to the `.env` file:
     ```env
     GOOGLE_CALENDAR_OAUTH2_API_CREDENTIALS=your-google-calendar-credentials
     GMAIL_OAUTH2_API_CREDENTIALS=your-gmail-credentials
     OPENAI_API_CREDENTIALS=your-openai-credentials
     ```

### Running the Workflow Locally
To test the workflow locally, run:
```bash
n8n execute --file=workflow.json
```

### GitHub Actions Workflow
The workflow is configured to run automatically every day at 8 AM. You can also trigger it manually via the GitHub Actions interface.

### Workflow Description
1. **Google Calendar Node**: Fetches all events from Google Calendar.
2. **Gmail Node**: Fetches all emails from Gmail.
3. **Summarize Node**: Uses OpenAI to summarize the fetched events and emails.
4. **End Node**: Marks the end of the workflow.

### Optimization for Free-Tier Usage
- The workflow is optimized for free-tier usage by running on a public repository, which provides unlimited minutes.
- Inputs are handled via JSON files to avoid limitations with CLI flags.

### Handling Sensitive Data
- Sensitive data such as API credentials are stored in GitHub Secrets and passed to the workflow via environment variables.

## License
This project is licensed under the MIT License.