# Getting Started with Snowflake Interactive Analytics

## Overview

When it comes to near real-time (or sub-second) analytics, the ideal scenario involves achieving consistent, rapid query performance and managing costs effectively, even with large datasets and high user demand.

Snowflake's new Interactive Warehouses are designed to deliver on these needs. They provide a high-concurrency, low-latency serving layer for near real-time analytics, and can query your existing standard tables directly through zero-copy interactive analytics, with no data conversion required. This allows consistent, sub-second query performance for live dashboards and APIs with great price-for-performance. With this end-to-end solution, you can avoid operational complexities and tool sprawl.

### What You'll Learn
- The core concepts behind Snowflake's Interactive Warehouses and how they provide low-latency analytics.
- How to create and configure an Interactive Warehouse using SQL.
- How zero-copy interactive analytics lets an interactive warehouse query your standard tables directly, with no data conversion required.
- How to attach a table to an Interactive Warehouse to pre-warm the data cache for faster queries.
- A methodology for benchmarking and comparing the query latency and throughput of an interactive warehouse versus a standard warehouse.

### What You'll Build

You will build a complete, functioning interactive analytics environment in Snowflake, including a dedicated Interactive Warehouse configured to query your data directly. You will also create a Python-based performance test that executes queries against both your interactive warehouse and a standard warehouse, culminating in benchmark charts that visually demonstrate the latency and throughput improvements.

# Step-By-Step Guide

For prerequisites, environment setup, step-by-step guide and instructions, please refer to the [QuickStart Guide](https://www.snowflake.com/en/developers/guides/getting-started-with-interactive-analytics/).
