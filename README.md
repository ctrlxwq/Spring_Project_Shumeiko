# Система інтернет магазину
## Функціональні вимоги: 

1. **Реєстрація та авторизація користувачів:** Користувачі можуть авторизуватись, або ж зареєструватись та відновити пароль з потреби
2. **Профіль користувача:** Користувачі можуть переглядати та редагувати особисті дані, можуть переглядати історію та статус замовлень
3. **Кошик та оформлення замовлень:**
Користувачі мають змогу додавати продукти до кошику, видаляти їх звідти, оформлення замовлень та підтвердження даних замовлення.
4. **Головна сторінка:**
На ній має бути доступна інформація про компанію, список останніх подій та новин, контактна інформація, список продукції
5. **Сторінка продукту:**
Опис обраного продукту, фото продукту, можливість додати продукт до кошику, відгуки та оцінка користувачів
6. **Сторінка продукції:**
Каталог продуктів, фільтрація по категоріям, пошук по ключовим словам

# REST API ENDPOINTS
## Користувачі (Users)

### Реєстрація користувача:

- POST /api/users/register
- Тіло запиту: { "username": "user", "email": "user@example.com", "password": "password" }
- Опис: Реєстрація нового користувача.

### Авторизація користувача:

- POST /api/users/login
- Тіло запиту: { "email": "user@example.com", "password": "password" }
- Опис: Авторизація користувача і повернення токена.

### Отримати профіль користувача:

- GET /api/users/profile
- Опис: Отримати інформацію про поточного користувача (вимагає авторизації).

### Оновити профіль користувача:

- PUT /api/users/profile
- Тіло запиту: { "username": "newusername", "email": "newemail@example.com" }
- Опис: Оновити інформацію профілю користувача (вимагає авторизації).

## Продукти (Products)

### Отримати список продуктів:

- GET /api/products
- Опис: Отримати список всіх продуктів з можливістю фільтрації та пошуку.

### Отримати продукт за ID:

- GET /api/products/{id}
- Опис: Отримати інформацію про продукт за його ID.

### Додати новий продукт:

- POST /api/products
- Тіло запиту: { "name": "Product Name", "description": "Product Description", "price": 9.99, "category_id": 1 }
- Опис: Додати новий продукт (вимагає авторизації адміністратора).

### Оновити продукт:

- PUT /api/products/{id}
- Тіло запиту: { "name": "Updated Product Name", "description": "Updated Description", "price": 10.99, "category_id": 2 }
- Опис: Оновити інформацію про продукт за його ID (вимагає авторизації адміністратора).

### Видалити продукт:

- DELETE /api/products/{id}
- Опис: Видалити продукт за його ID (вимагає авторизації адміністратора).

## Категорії (Categories)

### Отримати список категорій:

- GET /api/categories
- Опис: Отримати список всіх категорій.

### Додати нову категорію:

- POST /api/categories
- Тіло запиту: { "name": "Category Name" }
- Опис: Додати нову категорію (вимагає авторизації адміністратора).

### Оновити категорію:

- PUT /api/categories/{id}
- Тіло запиту: { "name": "Updated Category Name" }
- Опис: Оновити назву категорії (вимагає авторизації адміністратора).

### Видалити категорію:

- DELETE /api/categories/{id}
- Опис: Видалити категорію за її ID (вимагає авторизації адміністратора).

## Замовлення (Orders)

### Отримати список замовлень користувача:

- GET /api/orders
- Опис: Отримати список замовлень поточного користувача (вимагає авторизації).

### Отримати замовлення за ID:

- GET /api/orders/{id}
- Опис: Отримати інформацію про замовлення за його ID (вимагає авторизації).

### Створити нове замовлення:

- POST /api/orders
- Тіло запиту: { "items": [{ "product_id": 1, "quantity": 2 }, { "product_id": 2, "quantity": 1 }], "total_price": 29.97 }
- Опис: Створити нове замовлення (вимагає авторизації).

### Оновити статус замовлення:

- PUT /api/orders/{id}
- Тіло запиту: { "status": "Shipped" }
- Опис: Оновити статус замовлення (вимагає авторизації адміністратора).

## Відгуки (Reviews)

### Отримати відгуки про продукт:

- GET /api/products/{id}/reviews
- Опис: Отримати список відгуків для певного продукту.

### Додати відгук про продукт:

- POST /api/products/{id}/reviews
- Тіло запиту: { "rating": 5, "comment": "Great product!" }
- Опис: Додати відгук для певного продукту (вимагає авторизації).

### Оновити відгук:

PUT /api/reviews/{id}
Тіло запиту: { "rating": 4, "comment": "Good product!" }
Опис: Оновити відгук за його ID (вимагає авторизації).

### Видалити відгук:

- DELETE /api/reviews/{id}
- Опис: Видалити відгук за його ID (вимагає авторизації).

## Новини (News)

### Отримати список новин:

- GET /api/news
- Опис: Отримати список всіх новин.

### Отримати новину за ID:

- GET /api/news/{id}
- Опис: Отримати інформацію про новину за її ID.

### Додати нову новину:

- POST /api/news
- Тіло запиту: { "title": "News Title", "content": "News content." }
- Опис: Додати нову новину (вимагає авторизації адміністратора).

### Оновити новину:

- PUT /api/news/{id}
- Тіло запиту: { "title": "Updated News Title", "content": "Updated content." }
- Опис: Оновити новину за її ID (вимагає авторизації адміністратора).

### Видалити новину:

- DELETE /api/news/{id}
- Опис: Видалити новину за її ID (вимагає авторизації адміністратора).

