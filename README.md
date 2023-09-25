# Simple Query Share

This application allows you to securely share data from a query with others.

1. Fork this repo
1. Paste your SQL Query into `sources/query.sql`
1. Start the development server with `npm install` and `npm run dev`
1. Open `http://localhost:3000/settings` to connect to your database.
1. Sign in to Evidence Cloud, click Deploy Evidence Project, and select your repo.
1. Add emails of users you want to share the query with.
1. Share the URL with your team!

## Why is this better than a CSV?
1. The query is next to the data - you'll never lose track of what SQL you ran to generate the table.
1. It's searchable and filterable.
1. You can schedule the data to refresh automatically.
1. You won't lose the CSV somewhere on your computer.