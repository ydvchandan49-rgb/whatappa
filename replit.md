# Overview

This is a full-stack web application that bridges HubSpot form submissions with WhatsApp messaging. The system automatically processes form submissions from HubSpot and sends personalized WhatsApp messages to contacts using configurable message templates. It features a modern React frontend for managing submissions, messages, and system configuration, with an Express.js backend handling the core business logic.

# User Preferences

Preferred communication style: Simple, everyday language.

# System Architecture

## Frontend Architecture
The client is built with React and TypeScript, using a modern component-based architecture:
- **UI Framework**: React with TypeScript for type safety
- **Styling**: Tailwind CSS with shadcn/ui component library for consistent design
- **State Management**: TanStack Query for server state management and caching
- **Routing**: Wouter for lightweight client-side routing
- **Build System**: Vite for fast development and optimized production builds

The frontend follows a page-based structure with reusable components, organized into:
- Dashboard for system overview and metrics
- Form submissions management
- Message history tracking
- Template configuration
- System settings

## Backend Architecture
The server uses Express.js with TypeScript in a RESTful API design:
- **Framework**: Express.js with middleware for request logging and error handling
- **Database**: PostgreSQL with Drizzle ORM for type-safe database operations
- **Data Access**: Repository pattern with in-memory storage implementation for development
- **API Design**: RESTful endpoints following conventional HTTP methods and status codes

Key services include:
- WhatsApp integration service for message delivery
- Form submission processing workflow
- Template management system
- Configuration management

## Database Design
PostgreSQL schema with four main entities:
- **Form Submissions**: Stores HubSpot form data with processing status
- **WhatsApp Messages**: Tracks message delivery status and metadata
- **Message Templates**: Configurable templates with variable substitution
- **System Configuration**: WhatsApp API settings and system preferences

Uses Drizzle ORM for schema definition and migrations, providing type safety and automatic TypeScript generation.

## Authentication & Security
Currently implements a simple configuration-based approach without user authentication. The system is designed for internal use with environment-based security through:
- API token validation for WhatsApp integration
- Environment variable configuration
- CORS and request validation middleware

## Message Processing Workflow
1. HubSpot webhook receives form submission
2. System validates and stores submission data
3. Active message template is selected and personalized
4. WhatsApp API call is made to send message
5. Delivery status is tracked and updated
6. Dashboard metrics are updated in real-time

# External Dependencies

## Core Integrations
- **WhatsApp Business API**: For sending messages via Facebook Graph API
- **HubSpot**: Webhook integration for form submission events
- **PostgreSQL**: Primary database using Neon serverless hosting

## Third-Party Services
- **Radix UI**: Headless component primitives for accessible UI components
- **TanStack Query**: Server state management and caching
- **Drizzle ORM**: Type-safe database toolkit and query builder

## Development Tools
- **Vite**: Frontend build tool and development server
- **TypeScript**: Type safety across the entire stack
- **Tailwind CSS**: Utility-first CSS framework
- **ESBuild**: Fast JavaScript bundling for production

## Runtime Dependencies
- **Express.js**: Web application framework
- **React**: Frontend library with hooks and modern patterns
- **Node.js**: Server runtime environment
- **Date-fns**: Date manipulation and formatting utilities

# Deployment

## Vercel Deployment
The application is configured for Vercel deployment with:
- `vercel.json` configuration file
- Serverless API functions in `/api` directory
- Static build output optimization
- Environment variable configuration for production

### Required Environment Variables for Vercel:
- `WHATSAPP_ACCESS_TOKEN` - WhatsApp Business API token
- `WHATSAPP_PHONE_NUMBER_ID` - WhatsApp phone number ID
- `WHATSAPP_API_ENDPOINT` - Graph API endpoint
- `HUBSPOT_WEBHOOK_SECRET` - HubSpot webhook secret
- `NODE_ENV=production`

### Deployment Steps:
1. Install Vercel CLI: `npm install -g vercel`
2. Login: `vercel login`
3. Deploy: `vercel --prod`
4. Configure environment variables in Vercel dashboard
5. Update HubSpot webhook URL to production endpoint