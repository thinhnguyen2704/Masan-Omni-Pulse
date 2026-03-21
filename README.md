# Masan Omni-Pulse
## Overview
A multi-agent system that bridges the gap between Retail Demand (WinMart) and Supply Chain Logistics (Supra).

## Technical Architecture (The Principal's Blueprint)
Demand Forecaster Agent (Vision-Language): Use a Vision-Language Model (VLM) or time-series agent to analyze "Store Shelf Images" (simulated) and historical sales data to detect stockouts or trend shifts (e.g., Tet holiday surges).

Supra Logistics Optimizer Agent: A tool-calling agent that calculates the "Cost-to-Serve." It takes the demand signal and uses a routing API (like OSRM or Google Maps) to suggest optimal delivery windows from the nearest warehouse cluster.

WIN Member Personalization Agent: A RAG-based agent that looks at a customer's "Point of Life" profile (Grocery habits + Fintech credit score from Trusting Social) to generate a hyper-personalized offer (e.g., "Get 20% off MEATDeli if you pay via Techcombank today").
