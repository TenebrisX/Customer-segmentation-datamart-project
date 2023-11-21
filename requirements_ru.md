Требования к витрине RFM-классификации пользователей приложения

Исходные данные:
База данных: de.production

Таблицы:
orders - заказы
products - товары
orderitems - заказанные товары
orderstatuslog - логи статусов
orderstatuses - статусы
users - пользователи

Поля:
orders:
    order_id - int4 NOT NULL
	order_ts - timestamp NOT NULL
	user_id - int4 NOT NULL
	bonus_payment - numeric(19, 5) NOT NULL DEFAULT 0
	payment - numeric(19, 5) NOT NULL DEFAULT 0
	"cost" - numeric(19, 5) NOT NULL DEFAULT 0
	bonus_grant - numeric(19, 5) NOT NULL DEFAULT 0
	status - int4 NOT NULL

products:
    id - int4 NOT NULL
	"name" - varchar(2048) NOT NULL
	price - numeric(19, 5) NOT NULL DEFAULT 0

orderitems:
    id - int4 NOT NULL GENERATED ALWAYS AS IDENTITY( INCREMENT BY 1 MINVALUE 1 MAXVALUE 2147483647 START 1 CACHE 1 NO CYCLE)
	product_id - int4 NOT NULL
	order_id - int4 NOT NULL
	"name" - varchar(2048) NOT NULL
	price - numeric(19, 5) NOT NULL DEFAULT 0
	discount - numeric(19, 5) NOT NULL DEFAULT 0
	quantity - int4 NOT NULL

orderstatuslog:
    id - int4 NOT NULL GENERATED ALWAYS AS IDENTITY( INCREMENT BY 1 MINVALUE 1 MAXVALUE 2147483647 START 1 CACHE 1 NO CYCLE)
	order_id - int4 NOT NULL
	status_id - int4 NOT NULL
	dttm - timestamp NOT NULL

orderstatuses:
    id - int4 NOT NULL
	"key" - varchar(255) NOT NULL

users:
    id - int4 NOT NULL
	"name" - varchar(2048) NULL
	login - varchar(2048) NOT NULL


Выходные данные:
Визуализация: таблица с данными о RFM-сегментах пользователей
Расчёт RFM-сегментов

Recency: количество дней, прошедших с момента последнего заказа
Frequency: количество заказов
Monetary value: сумма затрат

Используемые поля:
orders:
    order_id - идентификатор заказа
    order_ts - дата заказа
    user_id - мдентификатор клиента
    payment - сумма оплаты
    status - статус заказа

Глубина витрины: 2022/01/01 - 2022/12/31
Обновления не нужны
Успешно выполненный заказ это заказ со статусом "Closed"
Разделить пользователей на 5 равных RMF сегментов, если количество заказов одинаковое, без разницы кого ставить выше, кого ниже.