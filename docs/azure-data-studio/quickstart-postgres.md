---
title: Краткое руководство. Подключение и запрос PostgreSQL
titleSuffix: Azure Data Studio
description: В этом кратком руководстве показано, как использовать Studio данных Azure для подключения к PostgreSQL и выполнения запроса
ms.custom: seodec18
ms.date: 03/19/2019
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: quickstart
author: rachel-msft
ms.author: raagyema
ms.openlocfilehash: 9dcbbe621ab237eeceff55cd5f931d7d650dd3b4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67959466"
---
# <a name="quickstart-connect-and-query-postgresql-using-includename-sosincludesname-sos-shortmd"></a>Краткое руководство. Подключение и запрос PostgreSQL с помощью [!INCLUDE[name-sos](../includes/name-sos-short.md)]
В этом кратком руководстве показано, как использовать [!INCLUDE[name-sos](../includes/name-sos-short.md)] для подключения к Postgres и последующее использование инструкций SQL для создания базы данных *tutorialdb* и запрос к ним.

## <a name="prerequisites"></a>предварительные требования

Для работы в этом кратком руководстве, требуется [!INCLUDE[name-sos](../includes/name-sos-short.md)], модуль PostgreSQL для [! ВКЛЮЧИТЬ[имя sos](../includes/name-sos-short.md)и доступ к серверу PostgreSQL.

- [Установка [!INCLUDE[name-sos](../includes/name-sos-short.md)] ](download.md).
- [Установка расширения PostgreSQL для Azure Data Studio](postgres-extension.md).
- [Установка PostgreSQL](https://www.postgresql.org/download/). (Кроме того, можно создать базу данных Postgres в облаке с помощью [az postgres вверх](https://docs.microsoft.com/azure/postgresql/quickstart-create-server-up-azure-cli)). 

## <a name="connect-to-postgresql"></a>Подключение к PostgreSQL

1. Запуск **[!INCLUDE[name-sos](../includes/name-sos-short.md)]** .

2. При первом запуске [!INCLUDE[name-sos](../includes/name-sos-short.md)] **подключения** откроется диалоговое окно. Если **подключения** диалоговое окно не открывается, щелкните **новое подключение** значок в **СЕРВЕРЫ** страницы:

   ![Значок "Создать подключение"](media/quickstart-postgresql/new-connection-icon.png)

3. В форме, которая появится, перейдите в раздел **тип подключения** и выберите **PostgreSQL** из раскрывающегося списка.


4. Заполните оставшиеся поля, используя имя сервера, имя пользователя и пароль для сервера PostgreSQL. 

   ![Новый экран подключения](media/quickstart-postgresql/new-connection-screen.png)  

   | Параметр       | Пример значения | Описание |
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Имя сервера** | localhost | Полное имя сервера |
   | **Имя пользователя** | postgres | Имя пользователя для входа в систему. |
   | **Пароль (имя входа SQL)** | *password* | Пароль для учетной записи, которую вы входите в систему. |
   | **Пароль** | *Проверить* | Установите этот флажок, если вы не хотите вводить пароль каждый раз, при подключении. |
   | **Имя базы данных** | \<Default\> | Заполните эту, если вы хотите, чтобы указать базу данных. |
   | **Группа серверов** | \<Default\> | Этот параметр позволяет назначить конкретную группу серверов, создаваемых этого подключения. | 
   | **Имя (необязательно)** | *Оставьте поле пустым* | Этот параметр позволяет указать понятное имя для вашего сервера. | 

5. Выберите **Подключиться**. 

После успешного подключения откроется ваш сервер в **СЕРВЕРЫ** боковой панели.


## <a name="create-a-database"></a>Создание базы данных

Ниже приведены инструкции по созданию базы данных с именем **tutorialdb**:

1. Щелкните правой кнопкой мыши на сервере PostgreSQL в **СЕРВЕРЫ** боковой панели и выберите **новый запрос**.

2. Вставьте следующую инструкцию SQL в редакторе запросов, которая позволяет открыть.

   ```sql
   CREATE DATABASE tutorialdb;
   ```

3. На панели инструментов выберите **запуска** для выполнения запроса. Уведомления появляются в **сообщений** панели, чтобы Показать ход выполнения запроса.

>[!TIP]
> Можно использовать **F5** на клавиатуре для выполнения инструкции вместо использования **запуска**.

После завершения выполнения запроса, щелкните правой кнопкой мыши **баз данных** и выберите **обновить** для см. в разделе **tutorialdb** в списке **баз данных** узла .


## <a name="create-a-table"></a>Создание таблицы

 Ниже приведены инструкции по созданию таблицы в **tutorialdb**:

1. Изменить контекст подключения к **tutorialdb** с помощью раскрывающегося списка в редакторе запросов. 

   ![Изменение контекста](media/quickstart-postgresql/change-context.png)

2. Вставьте следующую инструкцию SQL в редакторе запросов и нажмите кнопку **запуска**. 

   > [!NOTE]
   > Добавьте это либо перезапишите существующий запрос в редакторе. Щелкнув **запуска** выполняет запрос, который будет выделен. Если ничего не выделено, щелкнув **запуска** выполняет все запросы в редакторе.

   ```sql
   -- Drop the table if it already exists
   DROP TABLE IF EXISTS customers;
   -- Create a new table called 'customers'
   CREATE TABLE customers(
       customer_id SERIAL PRIMARY KEY,
       name VARCHAR (50) NOT NULL,
       location VARCHAR (50) NOT NULL,
       email VARCHAR (50) NOT NULL
   );
   ```

## <a name="insert-rows"></a>Вставка строк

Вставьте следующий фрагмент в окно запроса и нажмите кнопку **запуска**:

   ```sql
   -- Insert rows into table 'customers'
   INSERT INTO customers
       (customer_id, name, location, email)
    VALUES
      ( 1, 'Orlando', 'Australia', ''),
      ( 2, 'Keith', 'India', 'keith0@adventure-works.com'),
      ( 3, 'Donna', 'Germany', 'donna0@adventure-works.com'),
      ( 4, 'Janet', 'United States','janet1@adventure-works.com');
   ```

## <a name="query-the-data"></a>Запрос данных

1. Вставьте следующий фрагмент кода в редакторе запросов и нажмите кнопку **запуска**:
   
   ```sql
   -- Select rows from table 'customers'
   SELECT * FROM customers; 
   ```

2. Результаты запроса отображаются:

   ![Просмотр результатов](media/quickstart-postgresql/view-results.png)

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о [сценариев для Postgres в Azure Data Studio](postgres-extension.md). 