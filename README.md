# Beer Distribution Game

The Beer Distribution Game is a simulation of a supply chain that delivers beer from a brewery to end consumers. It was originally developed in the late 1950s by Jay Forrester at MIT to demonstrate the concepts of dynamic systems.

## Overview

The game simulates a supply chain with four main actors:
- Brewery (produces the beer)
- Distributor (distributes beer from brewery)
- Wholesaler (supplies distributors)
- Retailer (sells to end consumers)

Each actor must manage their inventory and orders to optimize the supply chain performance while dealing with:
- Order delays
- Delivery delays
- Inventory costs
- Backorder costs

## Implementation

This is an Agent-based Model (ABM) implementation of the beer game where each supply chain actor is represented by an autonomous agent. The implementation includes:

- Base supply chain agent with common functionality (`supplyChainAgent.py`)
- Specific agents for each role (brewery, distributor, wholesaler, retailer)
- Consumer agent that generates demand
- Controller for monitoring game performance
- Configurable order strategies

## Directory Structure

```
beer_game/
├── src/
│   └── abm/
│       └── base/
│           ├── beergame.py         # Main game model
│           ├── brewery.py          # Brewery agent
│           ├── consumer.py         # Consumer agent
│           ├── controlling.py      # Game controller
│           ├── distributor.py      # Distributor agent
│           ├── orderStrategy.py    # Order strategy implementation
│           ├── retailer.py         # Retailer agent
│           ├── supplyChainAgent.py # Base supply chain agent
│           └── wholesaler.py       # Wholesaler agent
├── scenarios/
│   └── beergame.json    # Game scenarios and configuration
└── requirements.txt     # Python dependencies
```

## Setup

1. Create a Python virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

## Usage

The game can be run with different scenarios defined in `scenarios/beergame.json`. The default scenario simulates a steady-state supply chain with:

- Consumer ordering 100 units per week
- Initial inventory of 400 units for each supply chain actor
- Configurable costs for inventory and backorders
- Delivery and order delays

## Game Mechanics

Each week (time step), every agent:
1. Receives deliveries from their supplier
2. Receives orders from their customer
3. Fulfills orders from inventory (creates backorders if insufficient)
4. Places orders with their supplier

The goal is to minimize total costs while maintaining sufficient inventory to meet demand. 