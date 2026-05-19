# AgriLink South Sudan

## Investor-Ready SRS + ERD + Product Blueprint

A digital, data-driven B2B AgriTech platform connecting South Sudan farmers and suppliers with urban retailers in Juba through marketplace, logistics, offline-first mobile access, dynamic pricing, and AI demand planning.

- **Product Type:** B2B AgriTech marketplace + logistics platform
- **Target Market:** Farmers, suppliers, retailers, logistics teams in Juba and South Sudan
- **Platforms:** Next.js web dashboard, Flutter mobile app, REST API, AI forecasting service
- **Core Advantage:** Offline-first ordering, transparent pricing, logistics visibility, demand prediction

## 1. Executive Summary

AgriLink South Sudan is designed to reduce post-harvest loss and improve the movement of fresh agricultural products from farms to retailers. The platform removes unnecessary physical trips, reduces dependence on informal middlemen, gives retailers a clean ordering experience, gives farmers a digital market for ready harvest, and gives administrators a command center for pricing, logistics, inventory, and forecasting.

## 2. Mission and Objectives

The mission is to digitize agricultural supply chains in South Sudan by connecting farmers and urban retailers through a simple, multilingual, offline-first web and mobile platform.

### Key objectives

- Reduce post-harvest loss by improving demand visibility.
- Allow retailers to order fresh products without physical market trips.
- Enable farmers to list daily harvest quantity, price, and quality grade.
- Provide logistics teams with delivery assignment, truck visibility, and inventory control.
- Use AI to forecast demand and improve supply-demand matching.

## 3. User Ecosystem

| User | Needs and Responsibilities |
| --- | --- |
| Retailer / Buyer | Browse products, place orders, set delivery PIN location, track delivery, view order history. |
| Farmer / Supplier | List ready harvest, update price and quantity, view sales, manage payment status. |
| Admin / Logistics | Manage users, prices, orders, inventory, trucks, deliveries, reports, and AI forecasts. |
| Driver | Receive assigned deliveries, update delivery status, share GPS location. |

## 4. Functional Requirements

| Module | Requirement | Priority |
| --- | --- | --- |
| Authentication & Security | Phone/OTP login, JWT sessions, role-based access control, audit logs. | Must Have |
| Retailer Marketplace | Category browsing, product search, cart, checkout, map PIN, order tracking, order history. | Must Have |
| Farmer Supply Portal | Product listing, daily price, available quantity, harvest date, quality grade, earnings view. | Must Have |
| Admin Command Center | Dashboard, user management, dynamic pricing, inventory, order workflow, logistics board, reports. | Must Have |
| Logistics Engine | Truck management, driver assignment, route status, delivery proof, live map view. | Must Have |
| Offline-first Sync | Browse cached products and create orders offline; sync automatically when 3G/4G returns. | Must Have |
| Multi-language UI | English and Arabic, icon-based navigation for low-literacy users. | Must Have |
| Multi-currency Support | SSP, USD, and UGX with admin-managed exchange rates. | Must Have |
| AI Demand Planning | Forecast retailer demand by product, area, season, price, and historical orders. | Phase 3 |

## 5. Non-Functional Requirements

- Mobile-first and fast on low bandwidth.
- Offline storage with conflict-safe sync.
- Secure API with encrypted passwords and protected sessions.
- Scalable architecture for more cities and product categories.
- Simple UI with large buttons, icons, and bilingual labels.
- Reliable audit trail for price changes, order edits, and deliveries.

## 6. System Architecture

| Layer | Recommended technology |
| --- | --- |
| Frontend Web | Next.js for admin, retailer, and farmer portals |
| Mobile App | Flutter offline-first application |
| Backend API | ASP.NET Core or NestJS REST API |
| Database | PostgreSQL with PostGIS for locations |
| Local Mobile DB | SQLite |
| AI Service | Python service using scikit-learn initially |
| Maps | Google Maps or OpenStreetMap depending on cost |

## 7. ERD - Main Database Entities

| Entity | Key Fields |
| --- | --- |
| users | id, name, phone, role, language, status, created_at |
| retailers | id, user_id, shop_name, area, latitude, longitude |
| farmers | id, user_id, farm_name, farm_location, verified_status |
| products | id, farmer_id, name, category, unit, quality_grade, harvest_date |
| inventory_batches | id, product_id, quantity_available, expiry_risk, price, currency |
| orders | id, retailer_id, status, total_amount, currency, delivery_pin_lat, delivery_pin_lng |
| order_items | id, order_id, product_id, quantity, unit_price |
| deliveries | id, order_id, driver_id, truck_id, status, assigned_at, delivered_at |
| trucks | id, plate_number, capacity_kg, current_lat, current_lng, status |
| price_history | id, product_id, price, currency, date, updated_by |
| exchange_rates | id, from_currency, to_currency, rate, effective_date |
| forecast_results | id, product_id, area, forecast_date, predicted_demand_kg, confidence_score |

## 8. ERD Relationships

- User has one Retailer, Farmer, Driver, or Admin profile.
- Farmer has many Products.
- Product has many Inventory Batches and Price History records.
- Retailer has many Orders.
- Order has many Order Items.
- Order has one Delivery.
- Delivery belongs to one Driver and one Truck.
- Forecast Results link product, area, date, and predicted demand.

## 9. UI/UX Design Blueprint

### Retailer UI

- Home with category icons
- Product list with grade and price
- Cart and checkout
- Map PIN screen
- Order tracking timeline
- Reorder from history

### Farmer UI

- Dashboard
- Add ready harvest
- Daily price update
- Quantity and quality grade
- Earnings and payment status

### Admin UI

- KPI dashboard
- Order management board
- Live truck map
- Dynamic price manager
- Inventory overview
- AI forecast dashboard

## 10. AI Demand Prediction Design

The AI model should begin with historical order data and use simple models before moving to advanced forecasting. The first recommended model is **Random Forest Regressor** because it works well with mixed numeric and categorical data and is easier to explain to investors than deep learning.

- **Inputs:** product, retailer area, day of week, season index, price, previous 7-day sales.
- **Output:** predicted demand in kilograms per product and area.
- **Business use:** suggest required stock, alert farmers, guide logistics planning, and support price decisions.
- **Future enhancement:** route optimization and quality-based supplier scoring.

## 11. MVP Roadmap

| Phase | Scope |
| --- | --- |
| Phase 1 - MVP | Retailer ordering, farmer listing, admin dashboard, manual delivery assignment. |
| Phase 2 - Operations | GPS tracking, price manager, multi-language, multi-currency. |
| Phase 3 - Offline + AI | Offline sync, demand prediction, inventory planning. |
| Phase 4 - Scale | More cities, route optimization, mobile payments, advanced analytics. |

## 12. Investor Value Proposition

- Large real-world problem: post-harvest loss and inefficient market access.
- Clear revenue opportunities: commission, delivery fee, premium supplier accounts, market data insights.
- Localized fit: offline-first, Arabic/English, SSP/USD/UGX, low-bandwidth mobile design.
- Scalable product: starts in Juba and can expand to other states and product categories.
