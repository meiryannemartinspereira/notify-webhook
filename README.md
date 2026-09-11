# Notify Webhook

Backend service built with Django and Django REST Framework to receive, store, and process webhook events.

The project was created to practice webhook integration, event persistence, notifications, and backend service organization.

## Features

* Receive webhook events through an API
* Store webhook events in the database
* Process order information
* Calculate order totals and profit
* Send notifications through WhatsApp
* Send email notifications
* Handle notification failures without stopping the webhook processing

## Technologies

* Python
* Django
* Django REST Framework
* SQLite
* WhatsApp API integration
* Email

## Project Structure

```text
notify-webhook/
├── app/
├── services/
├── webhooks/
├── manage.py
├── requirements.txt
└── .gitignore
```

## Installation

Clone the repository:

```bash
git clone https://github.com/meiryannemartinspereira/notify-webhook.git
cd notify-webhook
```

Create a virtual environment:

```bash
python -m venv venv
```

Activate the virtual environment:

### Linux / macOS

```bash
source venv/bin/activate
```

### Windows

```bash
venv\Scripts\activate
```

Install the dependencies:

```bash
pip install -r requirements.txt
```

Run the migrations:

```bash
python manage.py migrate
```

Start the development server:

```bash
python manage.py runserver
```

The API will be available at:

```text
http://127.0.0.1:8000/
```

## Webhook

The application provides an endpoint to receive webhook events.

Example request:

```http
POST /webhook/order/
Content-Type: application/json
```

Example payload:

```json
{
    "event_type": "order.created",
    "products": [
        {
            "name": "Product",
            "quantity": 2,
            "price": 50.00
        }
    ]
}
```

The received event is stored in the database and processed by the application.

## Notifications

After processing the webhook, the application can send notifications through external services such as WhatsApp and email.

Notification failures are handled separately so that an external service failure does not prevent the webhook event from being stored.

## Purpose

This project is a practical backend exercise focused on:

* REST APIs
* Webhook integration
* Event processing
* Database persistence
* External service integration
* Error handling
* Django project organization


