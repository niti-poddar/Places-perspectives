# Vercel Deployment Guide

## Prerequisites
- ✅ Build tested successfully
- ✅ Supabase project configured
- ✅ Environment variables ready

## Step 1: Initialize Git Repository

If you haven't already, initialize git in your project:

```bash
cd "/Users/karthik/Desktop/places & perspectives"
git init
git add .
git commit -m "Initial commit - Places & Perspectives app"
```

## Step 2: Push to GitHub (Recommended)

1. Create a new repository on GitHub (https://github.com/new)
   - Name it: `places-perspectives` (or any name you prefer)
   - Make it **Public** or **Private** (your choice)
   - **Don't** initialize with README, .gitignore, or license

2. Push your code:
```bash
git remote add origin https://github.com/YOUR_USERNAME/places-perspectives.git
git branch -M main
git push -u origin main
```

## Step 3: Deploy to Vercel

### Option A: Deploy via Vercel Dashboard (Easiest)

1. Go to https://vercel.com and sign in (or create an account)

2. Click **"Add New..."** → **"Project"**

3. Import your GitHub repository:
   - If you pushed to GitHub, you'll see your repo in the list
   - Click **"Import"** next to your repository

4. Configure your project:
   - **Framework Preset**: Next.js (should auto-detect)
   - **Root Directory**: `./` (leave as default)
   - **Build Command**: `npm run build` (auto-filled)
   - **Output Directory**: `.next` (auto-filled)
   - **Install Command**: `npm install` (auto-filled)

5. **Add Environment Variables** (IMPORTANT!):
   Click **"Environment Variables"** and add:
   
   ```
   NEXT_PUBLIC_SUPABASE_URL=https://iekxxyneoluqzrsrzouu.supabase.co
   NEXT_PUBLIC_SUPABASE_ANON_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6Imlla3h4eW5lb2x1cXpyc3J6b3V1Iiwicm9sZSI6ImFub24iLCJpYXQiOjE3NjUzMDA2NTgsImV4cCI6MjA4MDg3NjY1OH0.FaQKbR4NtWgNRamMmFd2LcJ8q78IoLMvZHu4MtFmO-A
   ```
   
   Make sure to select **Production**, **Preview**, and **Development** environments.

6. Click **"Deploy"**

7. Wait for deployment to complete (usually 1-3 minutes)

8. Your app will be live at: `https://your-project-name.vercel.app`

### Option B: Deploy via Vercel CLI

1. Install Vercel CLI:
```bash
npm i -g vercel
```

2. Login to Vercel:
```bash
vercel login
```

3. Deploy:
```bash
cd "/Users/karthik/Desktop/places & perspectives"
vercel
```

4. Follow the prompts:
   - Set up and deploy? **Yes**
   - Which scope? (select your account)
   - Link to existing project? **No**
   - Project name? (press Enter for default)
   - Directory? `./` (press Enter)
   - Override settings? **No**

5. Add environment variables:
```bash
vercel env add NEXT_PUBLIC_SUPABASE_URL
# Paste: https://iekxxyneoluqzrsrzouu.supabase.co
# Select: Production, Preview, Development

vercel env add NEXT_PUBLIC_SUPABASE_ANON_KEY
# Paste: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6Imlla3h4eW5lb2x1cXpyc3J6b3V1Iiwicm9sZSI6ImFub24iLCJpYXQiOjE3NjUzMDA2NTgsImV4cCI6MjA4MDg3NjY1OH0.FaQKbR4NtWgNRamMmFd2LcJ8q78IoLMvZHu4MtFmO-A
# Select: Production, Preview, Development
```

6. Redeploy with environment variables:
```bash
vercel --prod
```

## Step 4: Verify Deployment

1. Visit your deployment URL (provided by Vercel)
2. Test the globe loads correctly
3. Test form submission
4. Check browser console for any errors

## Step 5: Custom Domain (Optional)

1. Go to your project settings on Vercel
2. Click **"Domains"**
3. Add your custom domain
4. Follow DNS configuration instructions

## Troubleshooting

### Build Fails
- Check that all environment variables are set correctly
- Ensure `package.json` has correct build script
- Check Vercel build logs for specific errors

### Environment Variables Not Working
- Make sure variables start with `NEXT_PUBLIC_` for client-side access
- Redeploy after adding environment variables
- Check Vercel dashboard → Settings → Environment Variables

### Supabase Connection Issues
- Verify Supabase project is active
- Check Supabase dashboard for API URL and anon key
- Ensure RLS policies allow public read/insert

### Images Not Loading
- Verify Supabase storage bucket `perspectives` exists and is public
- Check storage policies allow public reads
- Verify `next.config.ts` has correct image domain configuration

## Post-Deployment Checklist

- [ ] App loads without errors
- [ ] Globe renders correctly
- [ ] Form submission works
- [ ] Images upload successfully
- [ ] Perspective pages load correctly
- [ ] Leaflet overlay map works
- [ ] All environment variables are set
- [ ] Custom domain configured (if applicable)

## Need Help?

- Vercel Docs: https://vercel.com/docs
- Next.js Deployment: https://nextjs.org/docs/deployment
- Vercel Support: https://vercel.com/support
