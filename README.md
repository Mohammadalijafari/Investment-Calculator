Investment Calculator

A simple React app that projects the growth of an investment over time. Enter your initial investment, annual contribution, expected return, and duration, and instantly see a year-by-year breakdown of investment value and interest earned.

Features
📊 Year-by-year table of investment growth
💰 Tracks total investment value, yearly interest, and cumulative interest
⚡ Instant recalculation as you update your inputs
🎨 Clean, minimal UI
Tech Stack
React — UI library
Vite — build tool & dev server
Project Structure
src/
├── components/
│   ├── Header.jsx      # App title / branding
│   ├── UserInput.jsx   # Form for investment parameters
│   └── Results.jsx     # Renders the year-by-year results table
├── util/
│   └── investment.js   # Calculation logic (calculateInvestmentResults, formatter)
├── App.jsx
└── main.jsx
Getting Started
Prerequisites
Node.js (v18 or later recommended)
npm

Installation
bash
git clone https://github.com/Mohammadalijafari/Investment-Calculator.git
cd investment-calculator
npm install

Run locally
bash
npm run dev

The app will be available at http://localhost:5173 (default Vite port).

Build for production
bash
npm run build
Usage

Fill in the four fields and the results table updates automatically:

Field	Description	Default
Initial Investment	The starting amount you invest	10,000
Annual Investment	How much you add each year	1,200
Expected Return	Expected annual growth rate (%)	6
Duration	Number of years to project	10

If Duration is less than 1, the results table is hidden and a validation message is shown instead.

How It Works
App holds the userInput state (with defaults shown above) and a handleChange function that updates it whenever a field changes.
UserInput renders the four number inputs; each one's onChange calls handleChange with the field name and new value.
App checks that duration >= 1. If not, it shows a validation message instead of results.
If valid, App passes userInput to Results, which calls calculateInvestmentResults(userInput) from util/investment.js. This loops once per year of duration:
Interest for the year = current investment value × (expectedReturn / 100)
Investment value is increased by that interest plus the annualInvestment
Each year's data (year, interest, end-of-year value, annual investment) is collected into an array
Results renders that array as a table, computing total interest to date for each row and formatting all currency values with formatter (USD, no decimal places) from the same file.
