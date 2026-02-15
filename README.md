# Atliq-Hospitality-Revenue-Booking-Analysis-Power-BI-Project-
This project analyzes hotel booking and revenue performance for Atliq Hospitality using Power BI. The goal was to build an end-to-end interactive dashboard to track KPIs, identify revenue trends, and support data-driven decision making to improve market share.

Business Problem

Atliq Grand, a chain of five-star hotels, observed a decline in market share and revenue performance.
Management required a centralized dashboard to monitor revenue, occupancy, cancellations, and customer behavior across cities and platforms.
- Track revenue & occupancy KPIs
- Monitor cancellations & no-shows
- Compare city and platform performance
- Identify revenue leakage opportunities

Objectives
- Create a clean and reliable analytical data model
- Define business KPIs using DAX
- Build an executive-level interactive dashboard
- Generate actionable business insights
- Enable slice-and-dice analysis using filters

  Tools & Technologies
- *Power BI*
- *Power Query* – Data Cleaning & Transformation
- *Power Pivot* – Data Modeling
- *DAX* – KPI Measures
- *Excel Data Sources**
- Star Schema Modeling

  Dataset Overview

**Fact Tables**
- fact_bookings
- fact_aggregated_bookings

**Dimension Tables**
- dim_hotels
- dim_rooms
- dim_date

**Key Fields**
- booking_id
- property_id
- booking_status
- platform
- check-in / check-out dates
- ratings
- capacity
- successful_bookings

Data Cleaning (Power Query)

- Promoted headers & standardized column names
- Corrected data types (date, numeric, text)
- Removed null & error rows
- Validated column uniqueness
- Standardized date formats
- Prepared aggregated booking metrics
- Performed column profiling & quality checks

---

#Data Modeling

- Designed **Star Schema**
- Created one-to-many relationships
- Linked fact tables with hotel, room, and date dimensions
- Built separate measure table
- Optimized filter directions for accurate KPI calculations

   DAX Measures Implemented

```DAX
Revenue = SUM(bookings[revenue_realized])

Total Bookings = COUNT(bookings[booking_id])

Avg Rating = AVERAGE(bookings[ratings_given])

Total Capacity = SUM(fact_aggregated_bookings[capacity])

Successful Bookings = SUM(fact_aggregated_bookings[successful_bookings])

Occupancy Rate = DIVIDE([Successful Bookings], [Total Capacity])

Cancelled Bookings =
CALCULATE(COUNT(bookings[booking_id]),
bookings[status] = "cancelled")

Cancellation Rate =
DIVIDE([Cancelled Bookings], [Total Bookings])

Avg Stay Duration = AVERAGE(bookings[stay_days])
