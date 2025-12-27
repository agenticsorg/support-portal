# Agentics Foundation Support Portal

A public-facing support ticket system for [Agentics Foundation](https://agentics.org/). This portal enables users to submit support requests and track their ticket status.

**Live Site:** [https://agentics-org.github.io/support-portal](https://agentics-org.github.io/support-portal)

## Features

- **Submit Support Tickets** - Users can create tickets with name, email, subject, priority level, and detailed description
- **Track Ticket Status** - Look up existing tickets using ticket ID and email verification
- **Priority Levels** - Support for Low, Medium, High, and Urgent priority classifications
- **Real-time Updates** - View ticket status changes and support team responses
- **Responsive Design** - Mobile-friendly interface that works across all devices

## Tech Stack

- **Frontend:** Pure HTML, CSS, and JavaScript (no build step required)
- **Backend:** Supabase Edge Functions for ticket submission
- **Database:** Supabase (PostgreSQL)
- **Hosting:** GitHub Pages with automated deployment

## Pages

| Page | Description |
|------|-------------|
| [index.html](index.html) | Main ticket submission form |
| [view-ticket.html](view-ticket.html) | Ticket lookup and status tracking |

## Setup

### Prerequisites

- A [Supabase](https://supabase.com/) project with:
  - A `tickets` table for storing ticket data
  - A `ticket_updates` table for tracking ticket history
  - An Edge Function for ticket submission

### Configuration

1. Clone the repository:
   ```bash
   git clone https://github.com/agentics-org/support-portal.git
   cd support-portal
   ```

2. Update the Supabase configuration in both HTML files:

   In `index.html`:
   ```javascript
   const SUPABASE_URL = 'https://your-project.supabase.co/functions/v1/submit-ticket';
   ```

   In `view-ticket.html`:
   ```javascript
   const SUPABASE_URL = 'https://your-project.supabase.co';
   const SUPABASE_KEY = 'your-anon-key';
   ```

3. Deploy to GitHub Pages or any static hosting provider.

### Database Schema

**tickets table:**
| Column | Type | Description |
|--------|------|-------------|
| ticket_id | text | Unique ticket identifier (e.g., TKT-2024-0001) |
| name | text | Submitter's name |
| email | text | Submitter's email |
| subject | text | Ticket subject |
| description | text | Detailed description |
| priority | text | low, medium, high, urgent |
| status | text | open, in_progress, closed |
| created_at | timestamp | Creation timestamp |

**ticket_updates table:**
| Column | Type | Description |
|--------|------|-------------|
| ticket_id | text | Reference to ticket |
| author_name | text | Name of person adding update |
| update_type | text | Type of update (status_change, comment) |
| content | text | Update content |
| old_status | text | Previous status (for status changes) |
| new_status | text | New status (for status changes) |
| created_at | timestamp | Update timestamp |

## Deployment

This project uses GitHub Actions for automatic deployment to GitHub Pages. Any push to the `main` branch triggers a deployment.

The workflow configuration is located in [.github/workflows/static.yml](.github/workflows/static.yml).

## Local Development

Since this is a static site, you can run it locally using any static file server:

```bash
# Using Python
python -m http.server 8000

# Using Node.js (npx)
npx serve .

# Using PHP
php -S localhost:8000
```

Then open `http://localhost:8000` in your browser.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is maintained by the [Agentics Foundation](https://agentics.org/).

## Support

For issues with this portal, please [open an issue](https://github.com/agentics-org/support-portal/issues) on GitHub.
