# Supabase Setup Guide

This project uses Supabase as the backend database.

## Step 1: Create a Supabase Account

1. Go to https://supabase.com
2. Sign up or log in.
3. Click **New Project**.
4. Enter:
   - Organization
   - Project Name
   - Database Password
   - Region
5. Click **Create Project**.
6. Wait until the project is fully provisioned.

---

## Step 2: Open Project Settings

1. Open your Supabase project.
2. From the left sidebar click:

Settings → API Keys

---

## Step 3: Copy the Publishable API Key

Under **Publishable key**

You will see something similar to:

```
sb_publishable_xxxxxxxxxxxxxxxxxxxxxxxxx
```

Click the **Copy** icon.

This key is safe to use in frontend applications.

---

## Step 4: Copy the Project URL

Go to:

Settings → General

Copy the **Project ID** or Project URL.

The URL will look like:

```
https://your-project-id.supabase.co
```

Example:

```
https://spfyseexdmrffncyutno.supabase.co
```

---

## Step 5: (Optional) Copy Secret Key

Go back to:

Settings → API Keys

Scroll down to **Secret keys**

Copy:

```
sb_secret_xxxxxxxxxxxxxxxxxxxxx
```

⚠ Never expose this key in frontend code.

Use it only on the backend.

---

## Step 6: Create Environment File

Create a `.env` file in the project root.

### Vite

```env
VITE_SUPABASE_URL=https://your-project-id.supabase.co
VITE_SUPABASE_ANON_KEY=sb_publishable_xxxxxxxxxxxxxxxxx
```

### Next.js

```env
NEXT_PUBLIC_SUPABASE_URL=https://your-project-id.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=sb_publishable_xxxxxxxxxxxxxxxxx
```

### Node.js Backend

```env
SUPABASE_URL=https://your-project-id.supabase.co
SUPABASE_SERVICE_ROLE_KEY=sb_secret_xxxxxxxxxxxxxxxxx
```

---

## Step 7: Install Supabase Client

```bash
npm install @supabase/supabase-js
```

---

## Step 8: Create Supabase Client

```javascript
import { createClient } from "@supabase/supabase-js";

export const supabase = createClient(
  import.meta.env.VITE_SUPABASE_URL,
  import.meta.env.VITE_SUPABASE_ANON_KEY
);
```

---

## Security Notes

✅ Publishable Key → Frontend

❌ Secret Key → Backend Only

Never commit `.env` files to Git.

Always add `.env` to `.gitignore`.
