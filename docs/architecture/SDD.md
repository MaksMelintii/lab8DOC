# SDD — Software Design Document

## 1. Архітектурний стиль
Система реалізована у стилі мікросервісів.

## 2. Основні компоненти
- API Gateway
- Auth Service
- Flight Service
- Booking Service
- Payment Service
- Notification Service
- PostgreSQL

## 3. Взаємодія компонентів
Клієнт надсилає запит до API Gateway, після чого запит маршрутизується до відповідного сервісу.

## 4. API / Інтерфейси
- `POST /auth/register`
- `POST /auth/login`
- `GET /flights/search`
- `POST /bookings`
- `POST /payments`