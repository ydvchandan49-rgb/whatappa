# Deploying WhatsApp Bridge to Vercel

## Quick Deployment Guide

### 1. Prepare Your Project

Make sure you have the following files in your project root:
- `vercel.json` - Vercel configuration
- `api/` directory - Serverless API functions
- `dist/` directory - Built frontend (created after build)

### 2. Install Vercel CLI

```bash
npm install -g vercel
```

### 3. Deploy to Vercel

```bash
# Login to Vercel
vercel login

# Deploy the project
vercel

# For production deployment
vercel --prod
```

### 4. Environment Variables

Set these environment variables in your Vercel dashboard:

- `WHATSAPP_ACCESS_TOKEN` - Your WhatsApp Business API token
- `WHATSAPP_PHONE_NUMBER_ID` - Your WhatsApp Business phone number ID
- `WHATSAPP_API_ENDPOINT` - https://graph.facebook.com/v17.0
- `HUBSPOT_WEBHOOK_SECRET` - Your HubSpot webhook secret (optional)
- `NODE_ENV` - production

### 5. Configure Custom Domain (Optional)

In your Vercel dashboard:
1. Go to your project settings
2. Navigate to "Domains"
3. Add your custom domain
4. Update DNS settings as instructed

### 6. HubSpot Webhook Configuration

After deployment, configure HubSpot to send webhooks to:
```
https://your-app-name.vercel.app/api/webhook/hubspot
```

### 7. WhatsApp Business API Setup

In your deployed app:
1. Navigate to `/configuration`
2. Enter your WhatsApp Business API credentials
3. Test the connection
4. Create message templates

## Alternative: Deploy via GitHub

1. **Push to GitHub**:
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/username/whatsapp-bridge.git
   git push -u origin main
   ```

2. **Connect to Vercel**:
   - Go to vercel.com
   - Click "New Project"
   - Import your GitHub repository
   - Configure environment variables
   - Deploy

## Vercel Configuration Files

The project includes these Vercel-specific files:

- `vercel.json` - Main configuration
- `api/*.ts` - Serverless functions for API endpoints
- Build configuration in existing `vite.config.ts`

## Production Considerations

For production deployment, consider:

1. **Database**: Replace in-memory storage with PostgreSQL
2. **Environment Variables**: Secure all API keys
3. **Rate Limiting**: Implement API rate limiting
4. **Monitoring**: Add error tracking (Sentry, LogRocket)
5. **Caching**: Configure CDN caching for static assets
6. **Security**: Add CORS headers and input validation

## Troubleshooting

**Build Errors**: 
- Check that all dependencies are in `package.json`
- Verify TypeScript compilation

**API Errors**:
- Check environment variables are set correctly
- Verify API endpoints are responding

**Webhook Issues**:
- Ensure webhook URL is accessible
- Check HubSpot webhook configuration
- Verify payload format

## Support

For deployment issues:
- Check Vercel deployment logs
- Review function logs in Vercel dashboard
- Test API endpoints individually