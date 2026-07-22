# Supabase Setup Guide

This project uses Supabase as the backend database.

---

# Step 1: Create a Supabase Account

1. Go to https://supabase.com
2. Sign up or log in.
3. Click **New Project**.
4. Enter:
   - Organization Name
   - Project Name
   - Database Password (Save this password securely. It will be required later.)
   - Region
5. Click **Create Project**.
6. Wait until the project status changes to **Healthy**.

---

# Step 2: Get the Supabase API Keys

1. Open your project.
2. Go to:

```
Settings → API Keys
```

3. Copy the **Publishable Key**.

It looks similar to:

```
sb_publishable_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

This key is used in frontend applications.

---

# Step 3: Get the Project URL

Go to:

```
Settings → General
```

Copy the **Project URL**.

Example:

```
https://spfyseexdmrffncyutno.supabase.co
```

---

# Step 4: Get PostgreSQL Database Connection Strings

From the top navigation bar, click:

```
Connect
```

A popup window will open.

Select:

```
ORMs
```

Scroll down to **Connection String**.

You'll find two connection strings.

### Transaction Pooler (Recommended for Applications)

```env
DATABASE_URL="postgresql://postgres.spfyseexdmrffncyutno:[YOUR-PASSWORD]@aws-1-ap-northeast-2.pooler.supabase.com:6543/postgres?pgbouncer=true"
```

### Session Pooler (Recommended for Migrations)

```env
DIRECT_URL="postgresql://postgres.spfyseexdmrffncyutno:[YOUR-PASSWORD]@aws-1-ap-northeast-2.pooler.supabase.com:5432/postgres"
```

> **Important:** Replace `[YOUR-PASSWORD]` with the database password you entered while creating the Supabase project.

---

# Step 5: Get the Secret Key (Backend Only)

Go to:

```
Settings → API Keys
```

Scroll to:

```
Secret Keys
```

Copy the Secret Key.

Example:

```
sb_secret_xxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

⚠️ Never expose this key in frontend applications.

---

# Step 6: Create the Environment File

Create a `.env` file in the project root.

### Vite

```env
VITE_SUPABASE_URL=https://your-project-id.supabase.co
VITE_SUPABASE_ANON_KEY=sb_publishable_xxxxxxxxxxxxxxxxx
```

### Node.js / Express / NestJS

```env
SUPABASE_URL=https://your-project-id.supabase.co
SUPABASE_SERVICE_ROLE_KEY=sb_secret_xxxxxxxxxxxxxxxxx

DATABASE_URL="postgresql://postgres.your-project-id:[YOUR-PASSWORD]@aws-1-region.pooler.supabase.com:6543/postgres?pgbouncer=true"

DIRECT_URL="postgresql://postgres.your-project-id:[YOUR-PASSWORD]@aws-1-region.pooler.supabase.com:5432/postgres"
```

---

# Step 7: Install Supabase Client

```bash
npm install @supabase/supabase-js
```

---

# Step 8: Create the Supabase Client

```javascript
import { createClient } from "@supabase/supabase-js";

export const supabase = createClient(
  import.meta.env.VITE_SUPABASE_URL,
  import.meta.env.VITE_SUPABASE_ANON_KEY
);
```

---

# Security Notes

- ✅ Publishable Key → Safe for frontend applications.
- ❌ Secret Key → Backend only. Never commit it to Git.
- ❌ Never commit your `.env` file.
- ✅ Add `.env` to `.gitignore`.
- 🔒 Store your database password securely, as it is required for `DATABASE_URL` and `DIRECT_URL`.
