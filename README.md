# AI Startup News to Slack - n8n Workflow

An n8n workflow export that collects recent AI startup headlines from NewsAPI, formats the results, and sends a daily summary to Slack.

## Workflow

1. A schedule trigger starts the workflow.
2. A code node calculates the previous day's date range.
3. An HTTP Request node fetches matching NewsAPI articles.
4. A code node formats article titles, sources, dates, and links.
5. A Slack node posts the summary to a configured channel.

## Requirements

- An n8n instance
- A NewsAPI account
- A Slack credential configured in n8n

## Import into n8n

1. Open n8n and create a new workflow.
2. Select **Import from File**.
3. Import `HV_Capital_Kokorev.json`.
4. Replace the NewsAPI credential configuration with your own.
5. Select your own Slack credential and destination channel.
6. Run the workflow manually before enabling its schedule.

## Environment variables

When adapting the workflow to use environment-backed credentials, use placeholders such as:

```env
NEWSAPI_KEY=replace-with-your-newsapi-key
SLACK_WEBHOOK_URL=replace-with-your-slack-webhook-url
```

Do not commit real API keys, webhook URLs, or exported credentials.

## Validation

- Execute each node manually and inspect its output.
- Confirm the HTTP Request node returns an `articles` array.
- Confirm the formatting node handles an empty result.
- Send a test message to a non-production Slack channel.

## Limitations

- The workflow is an n8n export, not a standalone Python application.
- Article relevance depends on the configured NewsAPI query.
- Deduplication is limited to the articles returned in one execution.
- Credentials and destination settings must be reviewed after import.

## Status

Small automation workflow created as a practical integration exercise. Review the exported workflow configuration before public reuse.
