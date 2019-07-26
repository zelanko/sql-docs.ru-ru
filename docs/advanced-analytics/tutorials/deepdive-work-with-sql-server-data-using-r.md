---
title: Создание базы данных и разрешений для учебников по RevoScaleR
description: Пошаговое руководство по созданию базы данных SQL Server для учебников по R.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: f8ed06135c7e97d0ba66a36615e7379e41c65e8b
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469689"
---
# <a name="create-a-database-and-permissions-sql-server-and-revoscaler-tutorial"></a>Создание базы данных и разрешений (учебник по SQL Server и RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Это занятие является частью [учебника RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) по использованию [функций RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

Урок 1 посвящен настройке базы данных SQL Server и разрешений, необходимых для работы с этим руководством. Используйте [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) или другой редактор запросов для выполнения следующих задач:

> [!div class="checklist"]
> * Создание новой базы данных для хранения данных для обучения и оценки двух моделей R
> * Создание имени входа пользователя базы данных с разрешениями на создание и использование объектов базы данных
  
## <a name="create-the-database"></a>Создайте базу данных

Для работы с этим руководством требуется база данных для хранения данных и кода. Если вы не являетесь администратором, попросите администратора создать базу данных и войти в нее. Вам понадобятся разрешения на запись и чтение данных, а также на выполнение скриптов R.

1. В SQL Server Management Studio подключитесь к экземпляру базы данных с поддержкой R.

2. Щелкните правой кнопкой мыши элемент **базы данных**и выберите пункт **создать базу данных**.
  
2. Введите имя новой базы данных: Реводипдиве.
  

## <a name="create-a-login"></a>Создает вход
  
1. Щелкните **Создать запрос**и измените контекст базы данных на master.
  
2. В новом окне **Запрос** выполните приведенные ниже команды, чтобы создать учетные записи пользователей и назначить их базе данных, используемой в этом учебнике. При необходимости измените имя базы данных.

3. Чтобы проверить имя входа, выберите новую базу данных, разверните узел **Безопасность**и разверните узел **Пользователи**.
  
**пользователя Windows**
  
```sql
 -- Create server user based on Windows account
USE master
GO
CREATE LOGIN [<DOMAIN>\<user_name>] FROM WINDOWS WITH DEFAULT_DATABASE=[RevoDeepDive]

 --Add the new user to tutorial database
USE [RevoDeepDive]
GO
CREATE USER [<user_name>] FOR LOGIN [<DOMAIN>\<user_name>] WITH DEFAULT_SCHEMA=[db_datareader]
```

**Имя входа SQL**

```sql
-- Create new SQL login
USE master
GO
CREATE LOGIN [DDUser01] WITH PASSWORD='<type password here>', CHECK_EXPIRATION=OFF, CHECK_POLICY=OFF;

-- Add the new SQL login to tutorial database
USE RevoDeepDive
GO
CREATE USER [DDUser01] FOR LOGIN [DDUser01] WITH DEFAULT_SCHEMA=[db_datareader]
```

## <a name="assign-permissions"></a>Назначение разрешений

В этом руководстве демонстрируются сценарии R и DDL, включая создание и удаление таблиц и хранимых процедур, а также выполнение сценария R во внешнем процессе на SQL Server. На этом шаге Назначьте права, чтобы разрешить эти задачи.

В этом примере предполагается наличие имени входа SQL (DDUser01), но если вы создали имя входа Windows, используйте вместо него.

```sql
USE RevoDeepDive
GO

EXEC sp_addrolemember 'db_owner', 'DDUser01'
GRANT EXECUTE ANY EXTERNAL SCRIPT TO DDUser01
GO
```

## <a name="troubleshoot-connections"></a>Устранение неполадок подключений

В этом разделе перечислены некоторые распространенные проблемы, которые могут возникнуть в процессе настройки базы данных.

- **Как проверить подключение к базе данных и запросы SQL?**
  
    Перед выполнением кода на языке R с помощью сервера может потребоваться проверить, доступна ли база данных из среды разработки R. [Обозреватель сервера Visual Studio](https://docs.microsoft.com/previous-versions/x603htbk(v=vs.140)) и [среда SQL Server Management Studio](../../ssms/download-sql-server-management-studio-ssms.md) являются бесплатными средствами с эффективными возможностями подключения к базам данных и функциями управления.
  
    Если вы не хотите устанавливать дополнительные средства управления базами данных, то можете создать тестовое подключение к экземпляру SQL Server с помощью компонента [Администратор источников данных ODBC](https://docs.microsoft.com/sql/odbc/admin/odbc-data-source-administrator?view=sql-server-2017) на панели управления. Если база данных настроена правильно и вы ввели верные имя пользователя и пароль, то вы увидите созданную базу данных и сможете выбрать ее в качестве базы данных по умолчанию.
  
    Распространенные причины ошибок подключения, включая удаленные подключения, не включены для сервера, а протокол именованных каналов не включен. Дополнительные советы по устранению неполадок можно найти в этой статье: [Устранение неполадок при подключении к ядро СУБД SQL Server](https://docs.microsoft.com/sql/database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine).
  
- **Почему имя таблицы имеет префикс datareader?**
  
    При указании схемы по умолчанию для этого пользователя в качестве **db_datareader**всем таблицам и другим новым объектам, созданным этим пользователем, предваряется имя *схемы* . Схема напоминает папку, которую можно добавить к базе данных для упорядочения объектов. Схема также определяет права пользователя в базе данных.
  
    Если схема связана с одним конкретным именем пользователя, пользователь является _владельцем схемы_. Когда вы создаете объект, он всегда создается в вашей собственной схеме, если вы специально не укажете, что он должен быть создан в другой схеме.
  
    Например, если создается таблица с именем **TestData**, а схемой по умолчанию является **db_datareader**, то таблица создается с именем `<database_name>.db_datareader.TestData`.
  
    По этой причине база данных может содержать несколько таблиц с одинаковыми именами, если они относятся к разным схемам.
   
    Если вы ищете таблицу и не указываете схему, сервер базы данных ищет схему, которой вы владеете. Поэтому нет необходимости указывать имя схемы при доступе к таблицам в схеме, связанной в вашим именем входа.
  
- **У меня нет прав DDL. Могу ли я работать с учебником?**
  
    Да, но следует попросить кому-либо предварительно загрузить данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы и перейти к следующему занятию. В любом случае функции, требующие полномочий DDL, по возможности вызываются из учебника.

    Кроме того, попросите администратора предоставить вам разрешение, выполнить любой внешний сценарий. Он необходим для выполнения скрипта R, как удаленно, так `sp_execute_external_script`и с помощью.

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Создание объектов данных SQL Server с помощью функции RxSqlServerData](../../advanced-analytics/tutorials/deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)