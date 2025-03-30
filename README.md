# Praktika-6-Aksenova-part-2
Цель практической работы: провести тестирование разработанных
программных модулей авторизации и регистрации пользователей с
использованием средств автоматизации Microsoft Visual Studio методом
"белого ящика"

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

Создадим ещё несколько таблиц для данной базы данных и построим модель базы в Visual Studio:
![image](https://github.com/user-attachments/assets/71350759-8f90-40b0-a488-8c11e7a21737)


![image](https://github.com/user-attachments/assets/bc71f2be-51a8-4ed1-a616-84a50078b24b)
![image](https://github.com/user-attachments/assets/0913df56-f378-49ac-ac1c-fec697ee6aa5)

Создадим модульные тесты в Visual Studio:

using Microsoft.VisualStudio.TestTools.UnitTesting;
using System;

namespace UnitTestProject1
{
    [TestClass]
    public class UnitTest1
    {
        [TestMethod]
        public void TestMethod1()
        {
            int res = 2 + 2;
            Assert.AreEqual(res, 4);
            Assert.AreNotEqual(res, 5);
            Assert.IsFalse(res > 5);
            Assert.IsTrue(res < 5);
        }
    }
}
![image](https://github.com/user-attachments/assets/496a1452-2ec7-43e6-aa03-636dd66bc573)

namespace UnitTestProject1
{
    [TestClass]
    public class UnitTest2
    {
        [TestMethod]
        public void AuthTest()
        {
            var page = new Authorization();
            Assert.IsTrue(page.Auth("test", "test"));
            Assert.IsFalse(page.Auth("user1", "12345"));
            Assert.IsFalse(page.Auth("", ""));
            Assert.IsFalse(page.Auth(" ", " "));
        }
    }
}
![image](https://github.com/user-attachments/assets/b4780d1e-8950-44f1-a72a-e3d608106cbd)






