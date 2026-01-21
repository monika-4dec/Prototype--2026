# ClaimGuard - Healthcare Claims Adjudication Platform

## Overview
ClaimGuard is a prototype healthcare claims adjudication platform that automates claims processing, implements fraud detection, and provides comprehensive analytics. The application demonstrates automated claim adjudication based on eligibility and coverage rules, real-time fraud detection for suspicious claims, and data export capabilities.

## Current State
The MVP is complete with the following features:
- Claims submission with patient, provider, and payer information
- Automated claim adjudication based on eligibility and coverage rules
- Fraud detection for duplicates, excessive charges, and high-frequency claims
- Dashboard with real-time metrics and charts
- Simulated email notification system
- CSV/JSON data export functionality

## Architecture

### Frontend
- **Framework**: React with TypeScript
- **Routing**: wouter
- **State Management**: TanStack Query v5
- **UI Components**: shadcn/ui with Tailwind CSS
- **Charts**: Recharts

### Backend
- **Framework**: Express.js with TypeScript
- **Storage**: In-memory storage (MemStorage)
- **Data Validation**: Zod schemas

### Key Files
- `shared/schema.ts` - Data models and TypeScript types for Claims, FraudFlags, Notifications
- `server/storage.ts` - In-memory storage implementation with sample data
- `server/routes.ts` - API endpoints including fraud detection and adjudication logic
- `client/src/pages/` - All page components (Dashboard, Claims, Fraud Alerts, etc.)
- `client/src/components/` - Reusable UI components

## API Endpoints
- `GET /api/dashboard/metrics` - Dashboard statistics
- `GET /api/dashboard/claim-types` - Claim distribution by type
- `GET /api/claims` - List all claims with fraud flags
- `GET /api/claims/:id` - Get single claim details
- `POST /api/claims` - Submit new claim (triggers adjudication and fraud detection)
- `POST /api/claims/:id/process` - Manually approve/reject a claim
- `GET /api/claims/counts` - Claim counts by status
- `GET /api/fraud-flags` - List all fraud alerts
- `GET /api/claims/:id/fraud-flags` - Get fraud flags for a specific claim
- `GET /api/notifications` - List all notifications
- `GET /api/export?format=csv|json&status=approved,rejected,flagged` - Export claims data
- `GET /api/import/template?format=csv|json` - Download claims import template
- `POST /api/import` - Bulk import claims from CSV/JSON file

## Fraud Detection Rules
1. **Excessive Charge**: Flags claims exceeding threshold (3x average) for claim type
2. **Duplicate Claims**: Detects same patient/provider/date/procedure combinations
3. **High Frequency**: Flags patients with 5+ claims in 30 days

## Adjudication Logic
- Claims are auto-rejected if patient is not eligible
- Claims are auto-rejected if service is not covered
- Eligible covered claims are approved at 90% of claimed amount

## Design Theme
- Professional healthcare/medical theme with blue primary colors
- Light and dark mode support
- Clean, modern interface following shadcn design patterns

## Recent Changes
- January 2026: Initial MVP implementation
- Added real-time claim type distribution endpoint
- Implemented simulated notification system
- Added data import feature with CSV/JSON template downloads
- Added bulk claims upload with automatic adjudication and fraud detection
- Updated branding to EXL logo
