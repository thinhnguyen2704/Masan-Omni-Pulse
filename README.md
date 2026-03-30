# Masan Omni-Pulse (MOP): Agentic Retail & Supply Chain Synchronization
## Project Vision
Masan Omni-Pulse is a proof-of-concept multi-agent system designed to bridge the gap between physical retail shelves (WinMart) and the digital supply chain (Supra Logistics). By leveraging Vision-Language models and Agentic RAG, MOP automates the "Direct Coverage" model, transforming manual store checks into real-time inventory and marketing actions.

## Tech Stack & Architecture
Vision Engine: PaddleOCR (Optimized for Vietnamese SKU recognition) + Sentence-Transformers for semantic SKU mapping.

Agent Orchestration: LangChain / LangGraph for stateful decision-making.

Intelligence: GPT-4o (Strategist) with RAG (Retrieval-Augmented Generation) for business rule enforcement.

Backend: FastAPI (Asynchronous processing) + SQL Server (Simulated Store DB).

Data Integrity: Vector Similarity Search to handle OCR noise and packaging glare.

## System Design: The Three-Agent Loop
###    1. The Eye (Vision Agent)
Challenge: OCR often struggles with distorted packaging or low-light shelf conditions in retail environments.

Solution: Implemented a Fuzzy-Vector Mapping layer. Instead of literal string matching, OCR outputs are embedded into a vector space and compared against a Master SKU list (Chin-Su, Omachi, MEATDeli).

Impact: Reduced SKU identification errors by ~25% compared to standard regex-based matching.

###    2. The Strategist (Business Logic Agent)
Function: Acts as the "Digital Store Manager." It consumes the inventory state and queries a RAG Knowledge Base containing Masan’s Q3 promotional strategies and stock thresholds.

Logic: If "Omachi" stock falls below 5 units, it triggers an urgent restock request AND evaluates if a WIN Member loyalty push notification is required to clear near-expiry stock.

###    3. The Executor (Integration Agent)
Function: Translates LLM reasoning into structured, production-ready payloads.

Outputs:

Supra-API: JSON payload for automated warehouse dispatch.

WIN-App-API: Personalized marketing copy for targeted customer segments.

## Masan-Specific Use Cases Demonstrated
The "Point of Life" Integration: Demonstrates how grocery data (WinMart) can trigger Fintech or Loyalty actions (WIN/Techcombank).

Supply Chain Efficiency: Direct alignment with Masan’s Supra logistics goals—reducing "Out-of-Stock" (OOS) events through autonomous monitoring.

Vietnamese Context: Fine-tuned to recognize local brands and handle Vietnamese character recognition in diverse fonts.

## Considerations
Error Handling: Implemented a "Confidence Threshold" for OCR—low-confidence scans are flagged for human-in-the-loop (HITL) review.

Cost Optimization: Uses a tiered LLM approach—lightweight models for SKU mapping and heavy-duty LLMs only for complex strategic reasoning.

Extensibility: Modular agent design allows for the easy addition of a "Pricing Agent" to monitor competitor prices (e.g., Bach Hoa Xanh) via web scraping.
