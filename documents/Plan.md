# План автоматизации тестирования приложения "Путешествие дня"

**Цель:** Автоматизировать сценарии (как позитивные, так и негативные) покупки тура через Приложение.

## 1. Перечень автоматизируемых сценариев

**Карты, предоставленные для тестирования в файле data.json:**

4444 4444 4444 4441, status "APPROVED"

4444 4444 4444 4442, status "DECLINED"

**Характеристика вводимых валидных тестовых данных:**

поле "Номер карты": 16 цифр

поле Месяц: текущий месяц

поле Год: текущий год

поле "Владелец": допустимые значения из латинских букв, дефисов, пробелов

поле "CVC/CCV": три цифры

### Позитивные сценарии:

### Позитивный сценарий №1

1. Открываем страницу http://localhost:8080/;
2. Нажимаем кнопку "Купить";
2. Ввести номер карты со статусом APPROVED: 4444 4444 4444 4441;
1. Остальные поля заполнить корректными значениями;
1. Нажимаем кнопку "Продолжить";
1. Появляется сообщение "Успешно. Операция одобрена Банком."в БД в payment_entity появилась запись со статусом APPROVED

### Позитивный сценарий №2

1. Открываем страницу http://localhost:8080/;
1. Нажимаем кнопку "Купить в кредит";
1. Ввести номер карты со статусом APPROVED: 4444 4444 4444 4441;
1. Остальные поля заполнить корректными значениями;
1. Нажимаем кнопку "Продолжить";
1. Появляется сообщение "Успешно. Операция одобрена Банком." в БД в credit_request_entity появилась запись со статусом
   APPROVED

### Позитивный сценарий №3

1. Открываем страницу http://localhost:8080/;
1. Нажимаем кнопку "Купить";
1. Ввести номер карты со статусом DECLINED: 4444 4444 4444 4442;
1. Остальные поля заполнить корректными значениями;
1. Нажимаем кнопку "Продолжить";
1. Появляется сообщение "Ошибка! Банк отказал в проведении операции." в БД в payment_entity появилась запись со статусом
   DECLINED

### Позитивный сценарий №4

1. Открываем страницу http://localhost:8080/;
1. Нажимаем кнопку "Купить в кредит";
1. Ввести номер карты со статусом DECLINED: 4444 4444 4444 4442;
1. Остальные поля заполнить корректными значениями;
1. Нажимаем кнопку "Продолжить";
1. Появляется сообщение "Ошибка! Банк отказал в проведении операции."в БД в credit_request_entity появилась запись со
   статусом DECLINED

### Негативные сценарии:

### Негативный сценарий №1("Оплата по карте" Отправка формы со всеми пустыми полями)

1. поле "Номер карты" "оставить пустым"
2. поле "Год" "оставить пустым"
3. поле "Месяц" "оставить пустым"
4. поле "Владелец" "оставить пустым"
5. поле "CVC/CVV" "оставить пустым"
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: уведомление об ошибках под всеми полями. Форма не отправлена. в БД в payment_entity новая запись
не появилась*

### Негативный сценарий №2("Оплата по карте" Отправки формы с пустым полем "Номер карты")

1. В поле "Номер карты" "оставить пустым".
2. В поле "Год" ввести "Текущий год "
3. В поле "Месяц" ввести "Текущий месяц "
4. В поле "Владелец" вводятся данные
5. В поле "CVC/CVV" вводятся данные
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: В поле "Номер карты" отображается сообщение "Поле обязательно для заполнения" в БД в
payment_entity новая запись не появилась*

### Негативный сценарий №3("Оплата по карте" Отправки формы с пустым полем "Год")

1. В поле "Номер карты" ввести "4444 4444 4444 441".
2. В поле "Год" "Оставить поле пустым"
3. В поле "Месяц" ввести "Текущий месяц"
4. В поле "Владелец" вводятся данные
5. В поле "CVC/CVV" вводятся данные
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: В поле "Год" отображается сообщение "Поле обязательно для заполнения" в БД в payment_entity новая
запись не появилась*

### Негативный сценарий №4("Оплата по карте" Отправки формы с пустым полем "Месяц")

1. В поле "Номер карты" ввести "4444 4444 4444 441".
2. В поле "Год" ввести "Текущий год"
3. В поле "Месяц" "Оставить поле пустым"
4. В поле "Владелец" вводятся данные
5. В поле "CVC/CVV" вводятся данные
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: В поле "Месяц" отображается сообщение "Поле обязательно для заполнения" в БД в payment_entity
новая запись не появилась*

### Негативный сценарий №5("Оплата по карте" Отправки формы с пустым полем "Владелец")

1. В поле "Номер карты" ввести "4444 4444 4444 441".
2. В поле "Год" ввести "Текущий год"
3. В поле "Месяц" ввести "Текущий месяц"
4. В поле "Владелец" "Оставить поле пустым"
5. В поле "CVC/CVV" вводятся данные
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: В поле "Владелец" отображается сообщение "Поле обязательно для заполнения" в БД в payment_entity
новая запись не появилась*

### Негативный сценарий №6("Оплата по карте" Отправки формы с пустым полем "CVC/CVV")

1. В поле "Номер карты" ввести "4444 4444 4444 441".
2. В поле "Год" ввести "Текущий год"
3. В поле "Месяц" ввести "Текущий месяц"
4. В поле "Владелец" вводятся данные
5. В поле "CVC/CVV" "Оставить поле пустым"
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: В поле "CVC/CVV" отображается сообщение "Поле обязательно для заполнения" в БД в payment_entity
новая запись не появилась*

### Негативный сценарий №7("Кредит по карте" Отправка формы со всеми пустыми полями)

1. поле "Номер карты" "оставить пустым"
2. поле "Год" "оставить пустым"
3. поле "Месяц" "оставить пустым"
4. поле "Владелец" "оставить пустым"
5. поле "CVC/CVV" "оставить пустым"
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: уведомление об ошибках под всеми полями. Форма не отправлена. в БД в credit_request_entity новая
запись не появилась*

### Негативный сценарий №8("Кредит по карте" Отправки формы с пустым полем "Номер карты")

1. В поле "Номер карты" "оставить пустым".
2. В поле "Год" ввести "Текущий год "
3. В поле "Месяц" ввести "Текущий месяц "
4. В поле "Владелец" вводятся данные
5. В поле "CVC/CVV" вводятся данные
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: В поле "Номер карты" отображается сообщение "Поле обязательно для заполнения" в БД в
credit_request_entity новая
запись не появилась*

### Негативный сценарий №9("Кредит по карте" Отправки формы с пустым полем "Год")

1. В поле "Номер карты" ввести "4444 4444 4444 441".
2. В поле "Год" "Оставить поле пустым"
3. В поле "Месяц" ввести "Текущий месяц"
4. В поле "Владелец" вводятся данные
5. В поле "CVC/CVV" вводятся данные
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: В поле "Год" отображается сообщение "Поле обязательно для заполнения" в БД в credit_request_entity
новая
запись не появилась*

### Негативный сценарий №10("Кредит по карте" Отправки формы с пустым полем "Месяц")

1. В поле "Номер карты" ввести "4444 4444 4444 441".
2. В поле "Год" ввести "Текущий год"
3. В поле "Месяц" "Оставить поле пустым"
4. В поле "Владелец" вводятся данные
5. В поле "CVC/CVV" вводятся данные
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: В поле "Месяц" отображается сообщение "Поле обязательно для заполнения" в БД в
credit_request_entity новая
запись не появилась*

### Негативный сценарий №11("Кредит по карте" Отправки формы с пустым полем "Владелец")

1. В поле "Номер карты" ввести "4444 4444 4444 441".
2. В поле "Год" ввести "Текущий год"
3. В поле "Месяц" ввести "Текущий месяц"
4. В поле "Владелец" "Оставить поле пустым"
5. В поле "CVC/CVV" вводятся данные
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: В поле "Владелец" отображается сообщение "Поле обязательно для заполнения" в БД в
credit_request_entity новая
запись не появилась*

### Негативный сценарий №12("Кредит по карте" Отправки формы с пустым полем "CVC/CVV")

1. В поле "Номер карты" ввести "4444 4444 4444 441".
2. В поле "Год" ввести "Текущий год"
3. В поле "Месяц" ввести "Текущий месяц"
4. В поле "Владелец" вводятся данные
5. В поле "CVC/CVV" "Оставить поле пустым"
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: В поле "CVC/CVV" отображается сообщение "Поле обязательно для заполнения" в БД в
credit_request_entity новая
запись не появилась*

### Негативный сценарий №13(Оплата по несуществующей карте)

1. В поле "Номер карты" ввести "4444 4444 4444 4443".
2. В поле "Год" ввести "Текущий год "
3. В поле "Месяц" ввести "Текущий месяц "
4. В поле "Владелец" вводятся данные
5. В поле "CVC/CVV" вводятся данные
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: уведомление "Ошибка! Банк отказал в проведении операции", в БД в payment_entity новая запись не
появилась*

### Негативный сценарий №14(Кредит по несуществующей карте)

1. В поле "Номер карты" ввести "4444 4444 4444 4443".
2. В поле "Год" ввести "Текущий год "
3. В поле "Месяц" ввести "Текущий месяц "
4. В поле "Владелец" вводятся данные
5. В поле "CVC/CVV" вводятся данные
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: уведомление "Ошибка! Банк отказал в проведении операции", в БД в credit_request_entity новая
запись не появилась*

### Негативный сценарий №15(Оплата по карте, указан невалидный номер)

1. В поле "Номер карты" ввести "4444 4444 4444 444".
2. В поле "Год" ввести "Текущий год "
3. В поле "Месяц" ввести "Текущий месяц "
4. В поле "Владелец" вводятся данные
5. В поле "CVC/CVV" вводятся данные
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: под полем Номер карты появилось сообщение об ошибке "Неверный формат"в БД в payment_entity новая
запись не появилась*

### Негативный сценарий №16(Кредит по карте, указан невалидный номер)

1. В поле "Номер карты" ввести "4444 4444 4444 444".
2. В поле "Год" ввести "Текущий год "
3. В поле "Месяц" ввести "Текущий месяц "
4. В поле "Владелец" вводятся данные
5. В поле "CVC/CVV" вводятся данные
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: под полем Номер карты появилось сообщение об ошибке "Неверный формат", в БД в
credit_request_entity новая запись не появилась*

### Негативный сценарий №17(Оплата по карте с истекшим сроком действия (месяц))

1. В поле "Номер карты" ввести "4444 4444 4444 441".
2. В поле "Год" ввести "Текущий год "
3. В поле "Месяц" ввести "Предыдущий месяц"
4. В поле "Владелец" вводятся данные
5. В поле "CVC/CVV" вводятся данные
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: под полем Месяц появилось сообщение об ошибке "Неверно указан срок действия карты"в БД в
payment_entity новая запись не появилась*

### Негативный сценарий №18(Кредит по данным карты с истекшим сроком действия (месяц))

1. В поле "Номер карты" ввести "4444 4444 4444 441".
2. В поле "Год" ввести "Текущий год "
3. В поле "Месяц" ввести "Предыдущий месяц"
4. В поле "Владелец" вводятся данные
5. В поле "CVC/CVV" вводятся данные
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: под полем Месяц появилось сообщение об ошибке "Неверно указан срок действия карты", в БД в
credit_request_entity новая запись не появилась*

### Негативный сценарий №19(Оплата по данным карты, указан невалидный месяц)

1. В поле "Номер карты" ввести "4444 4444 4444 441".
2. В поле "Год" ввести "Текущий год "
3. В поле "Месяц" ввести "00"
4. В поле "Владелец" вводятся данные
5. В поле "CVC/CVV" вводятся данные
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: под полем Месяц появилось сообщение об ошибке "Неверно указан срок действия карты"в БД в
payment_entity новая запись не появилась*

### Негативный сценарий №20(Кредит по данным карты, указан невалидный месяц)

1. В поле "Номер карты" ввести "4444 4444 4444 441".
2. В поле "Год" ввести "Текущий год "
3. В поле "Месяц" ввести "00"
4. В поле "Владелец" вводятся данные
5. В поле "CVC/CVV" вводятся данные
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: под полем Месяц появилось сообщение об ошибке "Неверно указан срок действия карты", в БД в
credit_request_entity новая запись не появилась*

### Негативный сценарий №21(Оплата по карте с истекшим сроком действия (год))

1. В поле "Номер карты" ввести "4444 4444 4444 441".
2. В поле "Год" ввести "Предыдущий год"
3. В поле "Месяц" ввести "Текущий месяц"
4. В поле "Владелец" вводятся данные
5. В поле "CVC/CVV" вводятся данные
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: под полем Год появилось сообщение об ошибке "Истёк срок действия карты"в БД в payment_entity новая
запись не появилась*

### Негативный сценарий №22(Кредит по данным карты с истекшим сроком действия (год))

1. В поле "Номер карты" ввести "4444 4444 4444 441".
2. В поле "Год" ввести "Предыдущий год"
3. В поле "Месяц" ввести "Текущий месяц"
4. В поле "Владелец" вводятся данные
5. В поле "CVC/CVV" вводятся данные
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: под полем Год появилось сообщение об ошибке "Истёк срок действия карты", в БД в
credit_request_entity новая запись не появилась*

### Негативный сценарий №23(Оплата по данным карты, указан невалидный год)

1. В поле "Номер карты" ввести "4444 4444 4444 441".
2. В поле "Год" ввести "Последние две цифры текущего года + 6"
3. В поле "Месяц" ввести "Текущий месяц"
4. В поле "Владелец" вводятся данные
5. В поле "CVC/CVV" вводятся данные
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: под полем Год появилось сообщение об ошибке "Неверно указан срок действия карты"в БД в
payment_entity новая запись не появилась*

### Негативный сценарий №24(Кредит по данным карты, указан невалидный год)

1. В поле "Номер карты" ввести "4444 4444 4444 441".
2. В поле "Год" ввести "Последние две цифры текущего года + 6"
3. В поле "Месяц" ввести "Текущий месяц"
4. В поле "Владелец" вводятся данные
5. В поле "CVC/CVV" вводятся данные
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: под полем Год появилось сообщение об ошибке "Неверно указан срок действия карты", в БД в
credit_request_entity новая запись не появилась*

### Негативный сценарий №25(Оплата по данным карты, указано некорректное значение(спец.символы) в поле Владелец)

1. В поле "Номер карты" ввести "4444 4444 4444 441".
2. В поле "Год" ввести "Текущий год"
3. В поле "Месяц" ввести "Текущий месяц"
4. В поле "Владелец" вводятся данные ""lefhl"
5. В поле "CVC/CVV" вводятся данные
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: под полем Владелец появилось сообщение об ошибке, в БД в payment_entity новая запись не появилась*

### Негативный сценарий №26(Оплата по данным карты, указано некорректное значение(мало символов) в поле Владелец)

1. В поле "Номер карты" ввести "4444 4444 4444 441".
2. В поле "Год" ввести "Текущий год"
3. В поле "Месяц" ввести "Текущий месяц"
4. В поле "Владелец" вводятся данные "Ed"
5. В поле "CVC/CVV" вводятся данные
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: под полем Владелец появилось сообщение об ошибке, в БД в payment_entity новая запись не появилась*

### Негативный сценарий №27(Оплата по данным карты, указано некорректное значение(превышает количество символов) в поле Владелец)

1. В поле "Номер карты" ввести "4444 4444 4444 441".
2. В поле "Год" ввести "Текущий год"
3. В поле "Месяц" ввести "Текущий месяц"
4. В поле "Владелец" вводятся данные "Eddddddddddddddddddduuuuuuuuuuuuuuuuuuuuaaaaaaaaaaaaaaaaaaaaaaaad Ibragimov"
5. В поле "CVC/CVV" вводятся данные
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: под полем Владелец появилось сообщение об ошибке, в БД в payment_entity новая запись не появилась*

### Негативный сценарий №28(Оплата по данным карты, указано некорректное значение(цифровое) в поле Владелец)

1. В поле "Номер карты" ввести "4444 4444 4444 441".
2. В поле "Год" ввести "Текущий год"
3. В поле "Месяц" ввести "Текущий месяц"
4. В поле "Владелец" вводятся данные "12345"
5. В поле "CVC/CVV" вводятся данные
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: под полем Владелец появилось сообщение об ошибке, в БД в payment_entity новая запись не появилась*

### Негативный сценарий №29(Оплата по данным карты, указано некорректное значение(кириллица) в поле Владелец)

1. В поле "Номер карты" ввести "4444 4444 4444 441".
2. В поле "Год" ввести "Текущий год"
3. В поле "Месяц" ввести "Текущий месяц"
4. В поле "Владелец" вводятся данные "Вася Васька"
5. В поле "CVC/CVV" вводятся данные
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: под полем Владелец появилось сообщение об ошибке, в БД в payment_entity новая запись не появилась*

### Негативный сценарий №30(Оплата по данным карты, указано некорректное значение(Значение состоит из одного слова) в поле Владелец)

1. В поле "Номер карты" ввести "4444 4444 4444 441".
2. В поле "Год" ввести "Текущий год"
3. В поле "Месяц" ввести "Текущий месяц"
4. В поле "Владелец" вводятся данные "Edward"
5. В поле "CVC/CVV" вводятся данные
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: под полем Владелец появилось сообщение об ошибке, в БД в payment_entity новая запись не появилась*

### Негативный сценарий №31(Кредит по данным карты, указано некорректное значение(мало символов) в поле Владелец)

1. В поле "Номер карты" ввести "4444 4444 4444 441".
2. В поле "Год" ввести "Текущий год"
3. В поле "Месяц" ввести "Текущий месяц"
4. В поле "Владелец" вводятся данные "Ed"
5. В поле "CVC/CVV" вводятся данные
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: под полем Владелец появилось сообщение об ошибке, в БД в credit_entity новая запись не появилась*

### Негативный сценарий №32(Кредит по данным карты, указано некорректное значение(превышает количество символов) в поле Владелец)

1. В поле "Номер карты" ввести "4444 4444 4444 441".
2. В поле "Год" ввести "Текущий год"
3. В поле "Месяц" ввести "Текущий месяц"
4. В поле "Владелец" вводятся данные "Eddddddddddddddddddduuuuuuuuuuuuuuuuuuuuaaaaaaaaaaaaaaaaaaaaaaaad Ibragimov"
5. В поле "CVC/CVV" вводятся данные
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: под полем Владелец появилось сообщение об ошибке, в БД в credit_entity новая запись не появилась*

### Негативный сценарий №33(Кредит по данным карты, указано некорректное значение(спец.символы) в поле Владелец)

1. В поле "Номер карты" ввести "4444 4444 4444 441".
2. В поле "Год" ввести "Текущий год"
3. В поле "Месяц" ввести "Текущий месяц"
4. В поле "Владелец" вводятся данные ""lefhl"
5. В поле "CVC/CVV" вводятся данные
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: под полем Владелец появилось сообщение об ошибке, в БД в credit_request_entity новая запись не
появилась*

### Негативный сценарий №34(Кредит по данным карты, указано некорректное значение(цифровое) в поле Владелец)

1. В поле "Номер карты" ввести "4444 4444 4444 441".
2. В поле "Год" ввести "Текущий год"
3. В поле "Месяц" ввести "Текущий месяц"
4. В поле "Владелец" вводятся данные "12345
5. В поле "CVC/CVV" вводятся данные
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: под полем Владелец появилось сообщение об ошибке, в БД в credit_request_entity новая запись не
появилась*

### Негативный сценарий №35(Кредит по данным карты, указано некорректное значение(кириллица) в поле Владелец)

1. В поле "Номер карты" ввести "4444 4444 4444 441".
2. В поле "Год" ввести "Текущий год"
3. В поле "Месяц" ввести "Текущий месяц"
4. В поле "Владелец" вводятся данные "Вася Васька
5. В поле "CVC/CVV" вводятся данные
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: под полем Владелец появилось сообщение об ошибке, в БД в credit_request_entity новая запись не
появилась*

### Негативный сценарий №36(Кредит по данным карты, указано некорректное значение(Значение состоит из одного слова) в поле Владелец)

1. В поле "Номер карты" ввести "4444 4444 4444 441".
2. В поле "Год" ввести "Текущий год"
3. В поле "Месяц" ввести "Текущий месяц"
4. В поле "Владелец" вводятся данные "Edward"
5. В поле "CVC/CVV" вводятся данные
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: под полем Владелец появилось сообщение об ошибке, в БД в credit_request_entity новая запись не
появилась*

### Негативный сценарий №37(Оплата по данным карты, указано некорректное значение в поле CVC/CVV)

1. В поле "Номер карты" ввести "4444 4444 4444 441".
2. В поле "Год" ввести "Текущий год"
3. В поле "Месяц" ввести "Текущий месяц"
4. В поле "Владелец" вводятся данные
5. В поле "CVC/CVV" указать "0"
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: под полем CVC/CVV появилось сообщение об ошибке "Неверный формат", в БД в payment_entity новая
запись не появилась*

### Негативный сценарий №38(Оплата по данным карты, указано некорректное значение в поле CVC/CVV)

1. В поле "Номер карты" ввести "4444 4444 4444 441".
2. В поле "Год" ввести "Текущий год"
3. В поле "Месяц" ввести "Текущий месяц"
4. В поле "Владелец" вводятся данные
5. В поле "CVC/CVV" указать "123456"
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: под полем CVC/CVV появилось сообщение об ошибке "Неверный формат", в БД в payment_entity новая
запись не появилась*

### Негативный сценарий №39(Кредит по данным карты, указано некорректное значение в поле CVC/CVV)

1. В поле "Номер карты" ввести "4444 4444 4444 441".
2. В поле "Год" ввести "Текущий год"
3. В поле "Месяц" ввести "Текущий месяц"
4. В поле "Владелец" вводятся данные
5. В поле "CVC/CVV" указать "0"
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: под полем CVC/CVV появилось сообщение об ошибке "Неверный формат", в БД в credit_request_entity
новая запись не появилась*

### Негативный сценарий №40(Кредит по данным карты, указано некорректное значение в поле CVC/CVV)

1. В поле "Номер карты" ввести "4444 4444 4444 441".
2. В поле "Год" ввести "Текущий год"
3. В поле "Месяц" ввести "Текущий месяц"
4. В поле "Владелец" вводятся данные
5. В поле "CVC/CVV" указать "123456"
6. Нажать кнопку "Продолжить"

*Ожидаемый результат: под полем CVC/CVV появилось сообщение об ошибке "Неверный формат", в БД в credit_request_entity
новая запись не появилась*

## 2. Перечень используемых инструментов с обоснованием выбора

1. **Java 11**  
   Универсальный язык, позволяющий работать на большинстве ОС и различном оборудовании.
1. **IntelliJ IDE**  
   Многофункциональная среда разработки, бесплатная. Хорошая интеграция в GitHub, широкая поддержка расширений и
   плагинов для тестирования.
1. **Git**  
   Система контроля версий. Бесплатность, возможность параллельной разработки, хорошая интеграция с IntelliJ IDEA.
1. **JUnit5**  
   Тестовый фреймворк, совместимый с JVM и IntelliJ IDEA, содержит все необходимые аннотации.
1. **Gradle**  
   Система сборки проекта. Имеет простой и понятный код, небольшого объема, в сравнению с Maven. Проще подключать
   внешние зависимости.
1. **Lombok**  
   Плагин для создания аннотаций, заменяющих значительное количество однообразных конструкторов JAVA таких как getters,
   setters и пр.
1. **Selenide**  
   Фреймворк для автоматизированного тестирования веб-приложений на основе Selenium WebDriver. Подключение веб-драйвера
   происходит автоматически, простое написание кода тестов.
1. **JavaFaker**  
   Плагин для генерации случайных данных для тестов. Большое количество настроек, бесплатный, достаточная локализация
   для
   России.
1. **Docker**
   Система контейнеризации. Будет использована для имитации работы IT-системы банка посредством развёртывания БД MySQL,
   PostgreSQL, запуск самого приложения через Node.js.
1. **Appveyor**  
   Система CI. Непрерывный контроль интеграции кода. Бесплатный, простое подключение и настройка, удобная интеграция с
   GitHub.
1. **Allure Report**  
   Система подготовки отчётов. Бесплатное решение. Хорошая информативная визуализация отчётов. Позволяет отслеживать
   данные на протяжении времени

## 3. Перечень и описание возможных рисков при автоматизации

1. Сложности с запуском и настройкой SUT.
1. Сложности с настройкой автотестов при отсутствии уникальных css-селекторов в приложении.
1. Изменение структуры рабочего сайта (правка дизайна с изменением html, css) в будущем приведёт к неработоспособности
   текущих автотестов.

## 4. Интервальная оценка с учётом рисков (в часах)

1. Планирование автоматизации тестирования - 6-10 часов
1. Написание кода тестов - 60-80 часов
1. Подготовка отчётных документов по итогам автоматизированного тестирования - 15-20 часов
1. Подготовка отчётных документов по итогам автоматизации - 8-12 часов

## 5. План сдачи Дипломной работы

1. Готовность авто-тестов — через 10 рабочих дней после утверждения плана тестирования;
1. Подготовка отчетов по результатам прогона тестов — через 4 рабочих дня после прогона тестов;
1. Подготовка отчета по итогам автоматизации — через 3 рабочих дня после отчетов по прогону тестов.