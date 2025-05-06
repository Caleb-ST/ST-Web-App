</H1>ST South Australia App</H1>

The ST South Australia App is a lightweight, browser-based tool designed for Sydney Tools employees in South Australia. It provides quick access to essential resources such as warranty information, representative contacts, gas cylinder details, nail compatibility, and more—all within a simple, mobile-friendly interface.
GitHub

🔧 Features
Modular Navigation: Each tool or resource is accessible via dedicated HTML pages linked from the main menu.

Nail Compatibility Tool: Browse nail compatibility by brand and model, powered by live data from a Google Sheet.

Gas Cylinder Lookup: Quickly find information on various gas types, including new and refill options.

Rep Directory: Easily access contact details for company representatives.

Warranty & Stock Pages: Access warranty information and manage written-off stock efficiently.

Test Area: A sandbox environment for experimenting with new features.

🚀 Getting Started
Clone the Repository:

bash
Copy
Edit
git clone https://github.com/Caleb-ST/ST-Web-App.git
Open the App:
Navigate to the index.html file in your browser to access the main menu.

Alternatively, view the live version at: https://caleb-st.github.io/ST-Web-App/

🛠️ Customization
Data Sources: Update the Google Sheet linked in the nail compatibility tool to reflect current data. Ensure the sheet is published to the web in CSV format.

Styling: Modify CSS files to match your company's branding guidelines.

Content: Edit existing HTML pages or add new ones to expand the app's functionality.

📁 Repository Structure
plaintext
Copy
Edit
├── index.html                  # Main landing page with navigation
├── Nails.html                  # Nail compatibility tool
├── SpeedGas.html               # Gas cylinder lookup
├── Rep Directory.html          # Representative contact information
├── Warranty.html               # Warranty details
├── Written Off Stock.html      # Manage written-off stock
├── Test Area.html              # Sandbox for testing new features
├── assets/                     # Images and other static assets
├── styles/                     # CSS files for styling
├── scripts/                    # JavaScript files for interactivity
└── README.md                   # Project documentation
📌 Notes
The app is entirely static and requires no backend server.

Ensure that any external data sources (like Google Sheets) are properly published and accessible.

For optimal performance, use modern web browsers.
