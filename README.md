# Praktika-6-Aksenova-part-2
Для начала создадим в SQL Server пустую базу данных. 

USE PR6Aksenova;
GO

CREATE TABLE [User] (
    ID INT PRIMARY KEY IDENTITY(1,1), -- Первичный ключ, автоинкремент
    Login VARCHAR(255) NOT NULL UNIQUE, -- Логин, обязательное поле, уникальное
    Password VARCHAR(255) NOT NULL, -- Пароль, обязательное поле
    Role VARCHAR(50) NOT NULL, -- Роль, обязательное поле
    FIO VARCHAR(255) NOT NULL, -- ФИО, обязательное поле
    [Пол] VARCHAR(10), -- Пол (например, 'Мужской', 'Женский', можно использовать ENUM или справочник)
    [НомерТелефона] VARCHAR(20), -- Номер телефона
    [ФотоПользователя] VARBINARY(MAX) -- Фотография пользователя (хранится как бинарные данные)
);

INSERT INTO [User] (Login, Password, Role, FIO, [Пол], [НомерТелефона]) VALUES
('user1', 'hashed_password_1', 'User', 'Иванов Иван Иванович', 'Мужской', '+79123456789'),
('user2', 'hashed_password_2', 'User', 'Петров Петр Петрович', 'Мужской', '+79234567890'),
('user3', 'hashed_password_3', 'User', 'Сидоров Сидор Сидорович', 'Мужской', '+79345678901'),
('admin1', 'hashed_password_4', 'Administrator', 'Админов Админ Админович', 'Мужской', '+79456789012'),
('manager1', 'hashed_password_5', 'Manager', 'Менеджеров Менеджер Менеджерович', 'Мужской', '+79567890123'),
('user4', 'hashed_password_6', 'User', 'Смирнов Алексей Сергеевич', 'Мужской', '+79678901234'),
('user5', 'hashed_password_7', 'User', 'Кузнецов Дмитрий Александрович', 'Мужской', '+79789012345'),
('user6', 'hashed_password_8', 'User', 'Попов Андрей Михайлович', 'Мужской', '+79890123456'),
('user7', 'hashed_password_9', 'User', 'Васильев Сергей Петрович', 'Мужской', '+79901234567'),
('user8', 'hashed_password_10', 'User', 'Федоров Иван Николаевич', 'Мужской', '+79012345678'),
('user9', 'hashed_password_11', 'User', 'Соколов Павел Андреевич', 'Мужской', '+79123456789'),
('guest1', 'hashed_password_12', 'Guest', 'Гостев Гость Гостевич', null, null);

![image](https://github.com/user-attachments/assets/bc71f2be-51a8-4ed1-a616-84a50078b24b)


