# 🚀 Deploy WhatsApp Bridge to Vercel

## Quick Deploy Steps

### 1. Install Vercel CLI
```bash
npm install -g vercel
```

### 2. Login to Vercel
```bash
vercel login
```

### 3. Deploy the Project
```bash
# From your project directory
vercel

# Follow prompts:
# ? Set up and deploy "~/whatsapp-bridge"? [Y/n] y
# ? Which scope do you want to deploy to? [Your Account]
# ? Link to existing project? [y/N] n
# ? What's your project's name? whatsapp-bridge
# ? In which directory is your code located? ./

# For production deployment
vercel --prod
```

## ✅ What's Already Configured

Your project is ready for Vercel with:

- ✅ `vercel.json` - Vercel deployment configuration
- ✅ `api/` folder - Serverless functions for backend
- ✅ `dist/` folder - Frontend build output
- ✅ Vite build configuration
- ✅ All required dependencies installed

## 🔧 Environment Variables

After deployment, add these in your Vercel dashboard:

1. Go to your project in Vercel dashboard
2. Navigate to **Settings** → **Environment Variables**
3. Add these variables:

```
WHATSAPP_ACCESS_TOKEN=your_whatsapp_token_here
WHATSAPP_PHONE_NUMBER_ID=your_phone_number_id
WHATSAPP_API_ENDPOINT=https://graph.facebook.com/v17.0
HUBSPOT_WEBHOOK_SECRET=your_webhook_secret (optional)
NODE_ENV=production
```

## 🎯 Post-Deployment Setup

1. **Test Your Deployment**
   - Visit your deployed URL (e.g., `https://whatsapp-bridge.vercel.app`)
   - Check all pages load correctly

2. **Configure WhatsApp**
   - Go to `/configuration` page
   - Enter your WhatsApp Business API credentials
   - Test the connection

3. **Set Up HubSpot Webhook**
   - Copy your webhook URL: `https://your-app.vercel.app/api/webhook`
   - Add to HubSpot workflow or form settings

4. **Create Message Templates**
   - Navigate to `/templates`
   - Create your first message template
   - Set it as active

## 🌐 Alternative: Deploy via GitHub

1. **Push to GitHub**:
   ```bash
   git init
   git add .
   git commit -m "Initial WhatsApp Bridge deployment"
   git branch -M main
   git remote add origin https://github.com/username/whatsapp-bridge.git
   git push -u origin main
   ```

2. **Connect to Vercel**:
   - Go to [vercel.com](https://vercel.com)
   - Click "New Project"
   - Import your GitHub repository
   - Configure environment variables
   - Deploy automatically

## 📊 API Endpoints Available

After deployment, these endpoints will be available:

- `GET /api/dashboard` - Dashboard metrics
- `GET /api/status` - System status
- `GET /api/submissions` - Form submissions
- `GET /api/messages` - Message history
- `GET /api/templates` - Message templates
- `GET /api/config` - System configuration
- `POST /api/webhook` - HubSpot webhook endpoint

## 🔒 Production Database

The current deployment uses in-memory storage (data resets on serverless function restarts). For production, consider:

1. **Vercel Postgres**:
   ```bash
   vercel storage create postgres
   ```

2. **External Database**:
   - Neon (recommended)
   - PlanetScale
   - Supabase

3. **Update Environment Variables**:
   - `DATABASE_URL` - Your database connection string

## 🏗️ Build Process

The build process:
1. Runs `vite build` to create frontend
2. Creates serverless functions from `/api` folder
3. Optimizes static assets
4. Sets up routing configuration

## 🛠️ Troubleshooting

**Build Fails**:
- Check all dependencies are installed
- Verify TypeScript compilation
- Review build logs in Vercel dashboard

**API Not Working**:
- Check environment variables
- Review function logs in Vercel dashboard
- Test endpoints individually

**WhatsApp Connection Issues**:
- Verify API credentials in environment variables
- Check WhatsApp Business API status
- Test with simple message first

## 🔄 Updates & Redeployments

To update your deployment:
```bash
# Make your changes
git add .
git commit -m "Update message templates"
git push

# Or redeploy directly
vercel --prod
```

## 📞 Support

If you encounter issues:
1. Check Vercel deployment logs
2. Review function logs in dashboard
3. Test API endpoints individually
4. Verify environment variables

Your WhatsApp Bridge is now ready for production use! 🎉