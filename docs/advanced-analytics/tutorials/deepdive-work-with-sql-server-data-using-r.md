---
title: Создание базы данных и разрешений для использования учебников RevoScaleR - машинного обучения SQL Server
description: Руководство по созданию базы данных SQL Server для использования учебников R...
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 15032b604d7ea28ad03acb837f997dac3afa84b8
ms.sourcegitcommit: ee76332b6119ef89549ee9d641d002b9cabf20d2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/20/2018
ms.locfileid: "53645273"
---
# <a name="create-a-database-and-permissions-sql-server-and-revoscaler-tutorial"></a>Создание базы данных и разрешений (руководство по SQL Server и RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Это занятие является частью [руководстве RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) по использованию [функций RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

Занятие, одно — о настройке базы данных SQL Server и разрешения для изучения этого учебника. Используйте [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) или другого редактора запросов, чтобы выполнить следующие задачи:

> [!div class="checklist"]
> * Создать новую базу данных для хранения данных для обучения и оценки двух моделей R
> * Создайте имя входа пользователя базы данных с разрешениями для создания и использования объектов базы данных
  
## <a name="create-the-database"></a>Создайте базу данных

Этот учебник требуется база данных для хранения данных и кода. Если вы не являетесь администратором, попросите администратора баз данных для создания базы данных и имя входа для вас. Потребуются разрешения на запись и чтение данных и для выполнения скриптов R.

1. В SQL Server Management Studio подключитесь к экземпляру базы данных с поддержкой R.

2. Щелкните правой кнопкой мыши **баз данных**и выберите **новую базу данных**.
  
2. Введите имя новой базы данных: RevoDeepDive.
  

## <a name="create-a-login"></a>Создает вход
  
1. Щелкните **Создать запрос**и измените контекст базы данных на master.
  
2. В новом окне **Запрос** выполните приведенные ниже команды, чтобы создать учетные записи пользователей и назначить их базе данных, используемой в этом учебнике. При необходимости измените имя базы данных.

3. Чтобы проверить имя входа, выберите новую базу данных, разверните **безопасности**и разверните **пользователей**.
  
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

В этом учебнике показано, скрипт R и DDL-операции, включая создание и удаление таблиц и хранимых процедур и запуска сценария R во внешнем процессе в SQL Server. На этом шаге назначение прав, чтобы разрешить эти задачи.

В этом примере предполагается, что имя входа SQL (DDUser01), но если вы создали имя входа Windows, используйте ее.

```sql
USE RevoDeepDive
GO

EXEC sp_addrolemember 'db_owner', 'DDUser01'
GRANT EXECUTE ANY EXTERNAL SCRIPT TO DDUser01
GO
```

## <a name="troubleshoot-connections"></a>Устранение неполадок с подключением

В этом разделе перечислены некоторые распространенные проблемы, которые могут возникнуть в процессе настройки базы данных.

- **Как проверить подключение к базе данных и запросы SQL?**
  
    Перед выполнением кода на языке R с помощью сервера может потребоваться проверить, доступна ли база данных из среды разработки R. [Обозреватель сервера Visual Studio](https://msdn.microsoft.com/library/x603htbk.aspx) и [среда SQL Server Management Studio](../../ssms/download-sql-server-management-studio-ssms.md) являются бесплатными средствами с эффективными возможностями подключения к базам данных и функциями управления.
  
    Если вы не хотите устанавливать дополнительные средства управления базами данных, то можете создать тестовое подключение к экземпляру SQL Server с помощью компонента [Администратор источников данных ODBC](https://msdn.microsoft.com/library/ms714024.aspx) на панели управления. Если база данных настроена правильно и вы ввели верные имя пользователя и пароль, то вы увидите созданную базу данных и сможете выбрать ее в качестве базы данных по умолчанию.
  
    Распространенные причины сбоев соединения включают удаленного соединения не разрешены для сервера, а не включен протокол именованных каналов. Дополнительные советы по устранению неполадок можно найти в этой статье: [Устранение неполадок при подключении к SQL Server Database Engine](https://docs.microsoft.com/sql/database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine).
  
- **Почему имя таблицы имеет префикс datareader?**
  
    При указании схемы по умолчанию для этого пользователя как **db_datareader**, все таблицы и другие объекты, созданные этим пользователем начинаются с префикса *схемы* имя. Схема напоминает папку, которую можно добавить к базе данных для упорядочения объектов. Схема также определяет права пользователя в базе данных.
  
    Если схема связана с одного имени определенного пользователя, он _владелец схемы_. Когда вы создаете объект, он всегда создается в вашей собственной схеме, если вы специально не укажете, что он должен быть создан в другой схеме.
  
    Например, если создать таблицу с именем **TestData**, и схема по умолчанию **db_datareader**, создается таблица с именем `<database_name>.db_datareader.TestData`.
  
    По этой причине база данных может содержать несколько таблиц с одинаковыми именами, если они относятся к разным схемам.
   
    Если вы ищете таблицу и не указали схему, сервер базы данных выполняет поиск вашей собственной схеме. Поэтому нет необходимости указывать имя схемы при доступе к таблицам в схеме, связанной в вашим именем входа.
  
- **У меня нет прав DDL. Могу ли я работать с учебником?**
  
    Да, но вам следует попросить кого-нибудь для предварительной загрузки данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблиц и перейти вперед к следующему занятию. Функции, требующие прав DDL, называются в этом руководстве, везде, где это возможно.

    Кроме того попросите администратора предоставить вам разрешения EXECUTE ANY EXTERNAL SCRIPT. Он необходим для выполнения сценариев R, ли удаленный или с помощью `sp_execute_external_script`.

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Создание объектов данных SQL Server с помощью функции RxSqlServerData](../../advanced-analytics/tutorials/deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)