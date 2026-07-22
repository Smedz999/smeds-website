# HJS Residential Customer Portal - Setup Guide

## Overview
The Residential Customer Portal allows customers to:
- Create and manage their account
- Track 3-stage payment progress
- Pay deposits and installments
- Book installation date (unlocks after full payment)
- View project documents

## Files Created
- `/hjs-website/residential-portal.html` - Main portal application
- Updated `/hjs-website/pages/residential.html` - Added payment terms section + portal links

## How It Works

### 1. Customer Registration
- Customer fills out: Name, Email, Phone, Address, Password
- Account stored in browser localStorage
- Demo mode - no backend required

### 2. Payment Stages
Default project setup (can be customized per customer):
- **Stage 1: Deposit** - 33% (£1,500) - Secures slot & orders equipment
- **Stage 2: Mid-Point** - 33% (£1,500) - Due when installation begins
- **Stage 3: Completion** - 34% (£1,500) - Final payment on completion
- **Total: £4,500** (example amount)

### 3. Installation Booking
- Locked until all 3 stages are paid
- Calendar interface to select date
- Confirmation shows date and arrival time (8-9 AM)

### 4. Customer Dashboard
- Project status overview
- Payment progress bar
- Stage cards (color-coded: pending/current/paid)
- Quick pay button for next due stage

## For Real Implementation

### To customize for each customer:
1. Open `residential-portal.html`
2. Find `defaultProject` object in JavaScript
3. Modify:
   - `totalCost` - Total project value
   - `stages` array - Adjust amounts/percentages
   - Add customer-specific details

### To add real payment processing:
Replace the `markStagePaid()` function with:
- Stripe integration
- PayPal API
- Bank transfer confirmation
- Or manual admin approval

### To add backend:
Currently uses localStorage (demo). For production:
- Connect to Firebase/Supabase
- Or build Node.js/Python backend
- Store users in database
- Add admin panel for HJS staff

## Access URLs
- **Portal**: `https://www.hjs-group.com/residential-portal.html`
- **From Residential Page**: Click "Customer Portal" or "Access Customer Portal" buttons

## Admin Features to Add (Future)
- [ ] Admin login to view all customers
- [ ] Mark payments as received (bank transfer)
- [ ] Upload documents (quotes, invoices, certificates)
- [ ] Send notifications to customers
- [ ] Manage installation calendar
- [ ] Export payment reports

## Security Note
Current version is client-side only (localStorage). For production:
- Add server-side authentication
- Encrypt sensitive data
- Use HTTPS only
- Add CSRF protection
- Implement session management