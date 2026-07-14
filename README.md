# Savour Foods Bill Management System (Java OOP)

A console-based desktop automation system designed to streamline, compute, and manage billing transactions for restaurant orders. Built purely in Java, the application showcases solid Object-Oriented Programming (OOP) foundations, specifically leveraging **Single Inheritance**, **Encapsulation**, and **Method-based computation** to handle menu-driven billing logic cleanly and efficiently.

---

## 📖 Project Overview
In high-volume food service environments like Savour Foods, manual bill calculation is prone to human error and delays. This project automates the order-to-billing pipeline by categorizing the menu into dedicated functional areas (Rice & Sweets), processing order quantities, calculating individual item totals, and compiling a unified final receipt. 

The architecture is highly structured, using class-level inheritance to separate menu data declarations from calculation logic.

---

## 🛠️ Software Architecture & Class Design

The system is engineered using a hierarchical class structure to maximize code organization and enforce clean object-oriented boundaries.

              ┌────────────────────────┐
              │       Main Class       │
              │  (Executes Program &   │
              │   Compiles Final Bill) │
              └───────────┬────────────┘
                          │ Instantiates
                          ▼
    ┌───────────────────────────────────────────┐
    │                                           │
┌──────┴──────────────┐                     ┌──────┴──────────────┐
│  Rice_Menu Class    │                     │  Sweets_Menu Class  │
│ (Parent: Declares   │                     │ (Parent: Declares   │
│  30 State Variables)│                     │  30 State Variables)│
└──────┬──────────────┘                     └──────┬──────────────┘
│                                           │
│ Inherits                                  │ Inherits
▼                                           ▼
┌──────┴──────────────┐                     ┌──────┴──────────────┐
│ Rice_Bill Class     │                     │ Sweets_Bill Class   │
│ (Child: Implements  │                     │ (Child: Implements  │
│  Computation logic) │                     │  Computation logic) │
└─────────────────────┘                     └─────────────────────┘


### 1. Menu Structure (Parent Classes: `Rice_Menu` & `Sweets_Menu`)
The system hosts a selection of **10 signature items** divided equally across two main dining profiles. To maintain strict data tracking, **30 precise variables** are declared in the parent classes to isolate item pricing, requested quantities, and computed line-item totals:
* **Item Variables:** Each of the 10 items declares a distinct set of variables:
  * `price_itemName` (Base cost per unit)
  * `qty_itemName` (Customer ordered volume)
  * `total_itemName` (Aggregated cost for this line-item)

### 2. Billing Processors (Child Classes: `Rice_Bill` & `Sweets_Bill`)
By inheriting properties from the parent classes, the child classes focus purely on execution and computation logic without redeclaring variables, ensuring clean code reuse:
* **Mathematical Model:** Individual item totals are resolved through a dedicated method implementing:
  $$total\_itemName = qty\_itemName \times price\_itemName$$
* Once individual line-item calculations are executed, they are summarized to generate segment-specific subtotals.

### 3. Execution Controller (Engine: `Main` Class)
The orchestration layer of the application:
1. Instantiates operational objects for the `Rice_Bill` and `Sweets_Bill` child classes.
2. Prompts user inputs for order quantities.
3. Triggers the internal calculation methods.
4. Aggregates the two individual sub-bills to compute, format, and display the **Final Cumulative Bill** directly to the terminal.

---

## 💻 Core Technical Concepts Highlighted

* **Single Inheritance:** Used to cleanly segregate static database definitions (Menu item specifications in parent classes) from dynamic operational flows (Billing algorithms in child classes).
* **Encapsulation:** Program states, base rates, and quantities are kept safely inside their respective class modules to prevent outside runtime corruption.
* **Modularity:** Organizing the menu into separate classes (`Rice` vs `Sweets`) makes it incredibly easy to add new dishes or modify pricing in the future without breaking the billing engine.
