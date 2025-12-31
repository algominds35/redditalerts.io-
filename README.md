# Reddit Brand Monitor - Landing Page

A clean, modern landing page for a Reddit brand monitoring SaaS tool.

## Features

- 📧 Email waitlist collection with Supabase integration
- 📱 Fully responsive design
- 🎨 Modern dark theme with gradient effects
- ⚡ Fast loading - single HTML file
- 💾 LocalStorage fallback if Supabase is not configured

## Quick Start

1. Clone this repository
2. Set up Supabase (see below)
3. Update Supabase credentials in `index.html`
4. Deploy to your hosting platform

## Supabase Setup

### 1. Create a Supabase Project

1. Go to [supabase.com](https://supabase.com)
2. Click "Start your project"
3. Create a new project

### 2. Create the Waitlist Table

Run this SQL in your Supabase SQL Editor:

```sql
-- Create waitlist table
CREATE TABLE waitlist (
  id BIGSERIAL PRIMARY KEY,
  email TEXT UNIQUE NOT NULL,
  created_at TIMESTAMPTZ DEFAULT NOW()
);

-- Enable Row Level Security
ALTER TABLE waitlist ENABLE ROW LEVEL SECURITY;

-- Create policy to allow inserts from anyone
CREATE POLICY "Allow public inserts" ON waitlist
  FOR INSERT
  TO anon
  WITH CHECK (true);

-- Create policy to allow reading own data
CREATE POLICY "Allow reading all" ON waitlist
  FOR SELECT
  TO authenticated
  USING (true);
```

### 3. Get Your Supabase Credentials

1. Go to Project Settings > API
2. Copy your **Project URL** (SUPABASE_URL)
3. Copy your **anon/public key** (SUPABASE_ANON_KEY)

### 4. Update index.html

Replace these lines in `index.html`:

```javascript
const SUPABASE_URL = 'YOUR_SUPABASE_URL';
const SUPABASE_ANON_KEY = 'YOUR_SUPABASE_ANON_KEY';
```

With your actual credentials:

```javascript
const SUPABASE_URL = 'https://your-project.supabase.co';
const SUPABASE_ANON_KEY = 'your-anon-key-here';
```

## Deployment

### GitHub Pages

1. Push to GitHub
2. Go to Settings > Pages
3. Select branch (main) and folder (root)
4. Your site will be live at `https://yourusername.github.io/redditalerts.io-/`

### Vercel

```bash
npm i -g vercel
vercel
```

### Netlify

```bash
npm i -g netlify-cli
netlify deploy
```

## Tech Stack

- HTML5
- CSS3 (with modern features like Grid, Flexbox, gradients)
- Vanilla JavaScript
- Supabase for backend
- Google Fonts (Inter)

## License

MIT

## Support

For issues or questions, please open an issue on GitHub.
