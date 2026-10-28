# PlazaDorm

Reviews for University of Maryland residence halls. Browse every on-campus dorm, filter and sort by area, type, and rating, view halls on an interactive 3D map, read resident reviews, and post your own.

**Site link:** https://plazadorm.com/

## Architecture

- **Frontend** - vanilla HTML/CSS/JS with no build step, [MapLibre GL](https://maplibre.org/) is used for the 3D campus map
- **Backend** - We use [Supabase](https://supabase.com/) to store reviews and helpful votes in Postgres, and Edge Functions (`supabase/functions/`) to handle review submission (hCaptcha-verified, server-side validation). We also use rate-limiting and other safety techniques.
- **Data** - We obtain our dorm dataset (names, areas, coordinates, photos) from public sources and store it in the frontend in `assets/js/data.js`; user-generated reviews live in the database

## Structure

```
├── index.html            # main hall browser (list, filters, 3D map)
├── dorm-reviews.html     # per-hall reviews page
├── about.html, privacy.html, terms.html
├── assets/
│   ├── css/styles.css    # site-wide styles and design tokens
│   ├── js/script.js      # hall browser logic
│   ├── js/data.js        # dorm dataset (~40 halls)
│   ├── js/supabase.js    # Supabase client (public anon key)
│   └── img/
└── supabase/             # Edge Functions + SQL migrations
                          # (secrets live in the Supabase dashboard, not here)
```
