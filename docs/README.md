# Ticket Booking Service Documentation

Ласкаво просимо до документації REST API сервісу для бронювання квитків.

## Основні розділи

### API Documentation
- [OpenAPI Specification](api/openapi.yaml)

### UI Documentation
- [Storybook Notes](ui/storybook-notes.md)

### Documentation Automation
- [CI/CD Documentation Pipeline](ci-cd-docs.md)
- [Definition of Done](definition-of-done.md)

## Призначення API
API є внутрішнім контрактом системи та використовується frontend-застосунком для:
- реєстрації та автентифікації користувачів;
- пошуку рейсів;
- створення бронювання;
- перегляду замовлень;
- скасування бронювання.

## Тип API
- Тип: internal API
- Споживачі: Web frontend, mobile client
- Формат обміну: JSON over HTTPS