# WhatsApp Bridge - HubSpot Integration

A full-stack web application that automatically sends WhatsApp messages when HubSpot forms are submitted. Built with React, Express.js, and TypeScript.

## Features

✅ **Dashboard** - Real-time metrics and system overview  
✅ **HubSpot Integration** - Webhook endpoint for form submissions  
✅ **WhatsApp Messaging** - Automated message sending via WhatsApp Business API  
✅ **Message Templates** - Configurable templates with variable substitution  
✅ **Message History** - Track delivery status and errors  
✅ **System Configuration** - Easy setup of API credentials  

## Architecture

### Frontend (React + TypeScript)
- **Framework**: React 18 with Vite for fast development
- **UI Library**: Tailwind CSS + shadcn/ui components
- **State Management**: TanStack Query for server state
- **Routing**: Wouter for lightweight client-side routing
- **Type Safety**: Full TypeScript support

### Backend (Express.js + TypeScript)
- **Framework**: Express.js with TypeScript
- **Data Storage**: In-memory storage (MemStorage) for development
- **Database Schema**: Drizzle ORM with PostgreSQL support
- **API Design**: RESTful endpoints with validation

### Database Schema
- **form_submissions**: HubSpot form submission data
- **whatsapp_messages**: Message delivery tracking
- **message_templates**: Configurable message templates
- **system_config**: WhatsApp and HubSpot API configuration

## Getting Started

### Prerequisites
- Node.js 20+
- WhatsApp Business API access
- HubSpot account with webhook capability

### Installation

1. **Clone and install dependencies**
   ```bash
   git clone <repository-url>
   cd whatsapp-bridge
   npm install
   ```

2. **Start the development server**
   ```bash
   npm run dev
   ```
   The app will be available at `http://localhost:5000`

### Configuration

1. **Navigate to Configuration page** in the app
2. **WhatsApp Business API Setup**:
   - API Endpoint: `https://graph.facebook.com/v17.0`
   - Access Token: Your WhatsApp Business API token
   - Phone Number ID: Your WhatsApp Business phone number ID

3. **HubSpot Webhook Setup**:
   - Copy the webhook URL from the configuration page
   - Add it to your HubSpot workflow or form settings
   - Set webhook events to trigger on form submissions

### Message Templates

Create custom message templates with variables:
- `{{contactName}}` - Contact's name from form
- `{{contactEmail}}` - Contact's email address  
- `{{formName}}` - Name of the submitted form

Example template:
```
Hi {{contactName}}! Thanks for your interest in our services. 
We received your {{formName}} submission and will contact you soon at {{contactEmail}}.
```

## API Endpoints

### Dashboard
- `GET /api/dashboard/metrics` - Get dashboard metrics
- `GET /api/status` - System status

### Form Submissions  
- `GET /api/submissions` - List all submissions
- `GET /api/submissions/recent` - Recent submissions
- `POST /api/webhook/hubspot` - HubSpot webhook endpoint

### Messages
- `GET /api/messages` - Message history
- `POST /api/test/whatsapp` - Test WhatsApp connection

### Templates
- `GET /api/templates` - List templates
- `POST /api/templates` - Create template
- `PUT /api/templates/:id` - Update template
- `DELETE /api/templates/:id` - Delete template

### Configuration
- `GET /api/config` - Get system config
- `POST /api/config` - Update system config

## Project Structure

```
├── client/                 # React frontend
│   ├── src/
│   │   ├── components/     # Reusable UI components
│   │   ├── pages/         # Page components
│   │   ├── hooks/         # Custom React hooks
│   │   └── lib/           # Utilities and helpers
├── server/                # Express backend
│   ├── index.ts          # Server entry point
│   ├── routes.ts         # API routes
│   ├── storage.ts        # Data storage layer
│   └── vite.ts           # Vite integration
├── shared/               # Shared types and schemas
│   └── schema.ts        # Database schema and types
└── package.json         # Dependencies and scripts
```

## Technology Stack

**Frontend**:
- React 18 + TypeScript
- Tailwind CSS + shadcn/ui
- TanStack Query
- Wouter (routing)
- Lucide React (icons)

**Backend**:
- Express.js + TypeScript  
- Drizzle ORM
- Zod validation
- WhatsApp Business API

**Development**:
- Vite (build tool)
- TSX (TypeScript execution)
- ESLint + Prettier

## Deployment

The app is ready for deployment on platforms like:
- Replit (recommended)
- Vercel
- Railway
- Heroku

For production, consider:
- PostgreSQL database instead of in-memory storage
- Environment variable management
- Rate limiting and security headers
- Error monitoring and logging

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## License

MIT License - see LICENSE file for details