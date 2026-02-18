# Outstanding-Stuff
eCommerce Application

Project Overview
The project is designed to manage a diverse marketplace across four primary categories: Pantry, Home and Furniture, Appliances, and Liquor.

Main Features:
Dual-Role Registration: Users select Buyer or Vendor during registration to access role-specific dashboards.

Storefront Management: Vendors can create and manage multiple stores and their respective product inventories.

Session-Based Cart: Utilizes Django Sessions to track items while browsing, ensuring a fast and responsive user experience.

Automated Email Invoicing: Upon checkout, the system:

Calculates the total using tabulate for clean formatting.

Generates a digital invoice and emails it to the Buyer.

Clears the session-based cart and removes products from inventory.

Verified Review System: Reviews are labeled "Verified" if the MySQL database confirms a prior purchase; otherwise, they are marked "Unverified."

Secure Account Recovery: Token-based password resets with time-sensitive, expiring URLs sent via email.

 Dependencies
The project relies on the following Python packages:

Django (6.0.2): The core web framework.

djangorestframework: Required for application API logic.

Pillow: Used for processing and saving product images.

mysqlclient: Required for connecting Django to your MySQL database.

tabulate: Used to format the itemized tables inside the emailed invoices.

sqlparse: Required for SQL formatting and database operations.

 Installation Instructions
1. Navigate to Project Root
Open your terminal and enter the main project directory:

PowerShell
cd "Outstanding Stuff"
2. Set Up Virtual Environment
Create a fresh environment and activate it:

PowerShell
python -m venv .venv
.\.venv\Scripts\activate
(You should see (.venv) appear in your terminal prompt.)

3. Install Dependencies
Install all required libraries at once:

PowerShell
pip install django djangorestframework mysqlclient Pillow tabulate sqlparse
4. Database Configuration
Ensure XAMPP/MySQL is running.

Create a database named outstanding_db (or as specified in your settings.py).

Ensure your DATABASES setting in settings.py reflects your local credentials (typically USER: 'root' and PASSWORD: '').

 Running the Project
1. Database Migrations
Sync your MySQL database with the Django models:

PowerShell
cd outstanding_stuff
python manage.py makemigrations
python manage.py migrate
2. Start the Server
PowerShell
python manage.py runserver
Access the application at: http://127.0.0.1:8000/

 Usage Instructions
User Roles: Choose "Buyer" to shop or "Vendor" to manage stores.

Shopping: Browse categories and add items to the cart (managed via request.session).

Checkout: Clicking checkout triggers the invoice email and clears the current session cart.

Verified Reviews: The "Verified" badge only appears if the user has a completed purchase record for that specific product in the MySQL database.

Password Reset: Use the "Forgot Password" link on the login page to receive a secure, one-time-use reset token via email.

 Additional Notes
Template Pathing: This project uses a flat directory structure. All .html files must reside directly in the root /templates/ folder. Do not create subfolders within the templates directory.

Session Management: Sessions are used to isolate Vendor screens from Buyers and to keep the cart persistent during the browsing session.

Environment: Always ensure the .venv is activated before running management commands to avoid ModuleNotFoundError.
