# Outstanding-Stuff
eCommerce Application

Project Overview The project is designed to manage a diverse marketplace across four primary categories: Pantry, Home and Furniture, Appliances, and Liquor.

Main Features: Dual-Role Registration: Users select Buyer or Vendor during registration to access role-specific dashboards.

Storefront Management: Vendors can create and manage multiple stores and their respective product inventories.

Session-Based Cart: Utilizes Django Sessions to track items while browsing, ensuring a fast and responsive user experience.

Automated Email Invoicing: Upon checkout, the system:

Calculates the total using tabulate for clean formatting.

Generates a digital invoice.

Emails the invoice to the Buyer.

Clears the session-based cart.

Verified Review System: Reviews are labeled "Verified" if the MySQL database confirms a prior purchase; otherwise, they are marked "Unverified."

Secure Account Recovery: Token-based password resets with time-sensitive, expiring URLs sent via email.

Dependencies The project relies on the following Python packages:

Django (6.0.1): The core web framework.

Pillow (12.1.0): Used for processing and saving product images.

sqlparse (0.5.5): Required for SQL formatting and database operations.

tabulate (0.9.0): Used to format the itemized tables inside the emailed invoices.

asgiref & tzdata: Core utilities for Django's asynchronous support and timezone management.

mysqlclient: (Required for MySQL connectivity).

Installation Instructions Clone the Repository:

Bash git clone https://github.com/your-username/outstanding-stuff.git cd outstanding-stuff Set Up Virtual Environment:

Bash python -m venv venv source venv/bin/activate # On Windows: venv\Scripts\activate Install Dependencies:

Bash pip install -r requirements.txt Database Configuration: Ensure MySQL is running. Create a database named outstanding_db and update the DATABASES setting in settings.py with your local credentials.

Environment Variables: Configure your SMTP settings in settings.py or a .env file to enable the invoice and password reset emails.

Running the Project Migrations: Sync your MySQL database with the Django models:

Bash python manage.py makemigrations python manage.py migrate Start Server:

Bash python manage.py runserver Open your browser to http://127.0.0.1:8000/.

Usage Instructions User Roles Registration: Choose "Buyer" to shop or "Vendor" to sell.

Login: A centralized login screen manages access to both roles.

Key Logic Shopping: Browse by categories (Pantry, Home and Furniture, Appliances, Liquor). Add items to the cart (managed via request.session).

Checkout: Clicking checkout triggers the invoice email and clears the current session.

Reviews: Anyone can leave a review, but the Verified badge only appears if the user has a completed purchase record for that specific product in the database.

Password Reset: Use the "Forgot Password" link on the login page to receive a secure, one-time-use reset token via email.

Additional Notes Template Pathing: This project uses a flat directory structure. All .html files must reside directly in the /templates/ folder.

Security: Password reset tokens are valid for a limited window (defined by PASSWORD_RESET_TIMEOUT).

Session Management: Sessions are used to isolate Vendor screens from Buyers and to keep the cart active during the browsing session.
