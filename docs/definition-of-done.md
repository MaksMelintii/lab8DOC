# Definition of Done for Documentation

## Призначення
Definition of Done визначає, яка документація повинна бути оновлена для кожного типу змін у проєкті.

## Загальні правила
Будь-яка зміна функціональності, API, UI або інфраструктури вважається завершеною лише тоді, коли відповідна документація оновлена та успішно проходить автоматизовані перевірки.

## Таблиця Definition of Done

| Тип зміни | Обов'язкові дії | Перевірка |
|---|---|---|
| Додано новий API endpoint | Оновити OpenAPI specification | OpenAPI validation |
| Змінено request/response | Оновити `openapi.yaml`, переглянути Swagger UI | CI validation + manual review |
| Breaking API change | Підвищити major version документації | Version check |
| Додано UI-компонент | Додати Storybook story | Storybook build |
| Змінено стан UI-компонента | Оновити stories | Storybook build |
| Змінено навігацію документації | Оновити README та MkDocs | MkDocs build |
| Змінено pipeline документації | Оновити `ci-cd-docs.md` | Manual review |
| Змінено критерії готовності | Оновити `definition-of-done.md` | Manual review |

## Перевірювані критерії готовності

### Для API-змін
- існує оновлений `docs/api/openapi.yaml`
- Swagger UI збирається без помилок
- усі нові endpoint'и мають request/response опис
- присутні коди помилок

### Для UI-змін
- існує story для нового або зміненого компонента
- описані базовий і альтернативний стани
- Storybook build проходить без помилок

### Для загальної документації
- README містить актуальні посилання
- MkDocs build проходить без помилок
- структура документації не містить битих посилань

## Текстова форма DoD
- Any API change must be reflected in the OpenAPI specification
- Swagger UI must be regenerated successfully
- UI changes require updated or new Storybook stories
- Documentation build must pass without errors
- Documentation version must remain consistent with product version

## Висновок
Documentation DoD дозволяє формалізувати вимогу: зміна не завершена, поки її не відображено в документації та не перевірено автоматично.