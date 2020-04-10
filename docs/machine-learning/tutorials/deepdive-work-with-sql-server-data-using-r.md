---
title: Учебные материалы по RevoScaleR
description: Учебник по RevoScaleR, часть 1. Сведения о том, как создать базу данных SQL Server для учебников по R.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: d37603f77aab747fc637bfbeac6335fa32c9c48b
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2020
ms.locfileid: "81116707"
---
# <a name="create-a-database-and-permissions-sql-server-and-revoscaler-tutorial"></a>Создание базы данных и разрешений (учебник по SQL Server и RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Эта часть 1 входит в состав [серии учебников по RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md), посвященной использованию [функций RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) в SQL Server.

В этом учебнике описано, как создать базу данных SQL Server и установить разрешения, необходимые для выполнения других учебников в этой серии. Используйте [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) или другой редактор запросов для выполнения следующих задач.

> [!div class="checklist"]
> * Создание базы данных, в которой будут храниться данные для обучения и оценки двух моделей R
> * Создание имени входа для пользователя базы данных с разрешениями на создание и использование объектов базы данных
  
## <a name="create-the-database"></a>Создание базы данных

При работе с этим учебником требуется база данных для хранения данных и кода. Если вы не являетесь администратором, попросите администратора базы данных создать для вас нужную базу данных и учетную запись. Вам потребуются разрешения на запись и чтение данных, а также на выполнение скриптов R.

1. В среде SQL Server Management Studio подключитесь к ядру СУБД с поддержкой R.

2. Щелкните правой кнопкой мыши узел **Базы данных** и выберите команду **Создать базу данных**.
  
2. Введите имя новой базы данных. RevoDeepDive.
  
## <a name="create-a-login"></a>Создает вход
  
1. Щелкните **Создать запрос**и измените контекст базы данных на master.
  
2. В новом окне **Запрос** выполните приведенные ниже команды, чтобы создать учетные записи пользователей и назначить их базе данных, используемой в этом учебнике. При необходимости измените имя базы данных.

3. Чтобы проверить учетную запись, выберите новую базу данных, а затем разверните узлы **Безопасность** и **Пользователи**.
  
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

В этом руководстве демонстрируются операции со скриптами R и DDL, включая создание и удаление таблиц и хранимых процедур, а также выполнение скрипта R во внешнем процессе на SQL Server. На этом шаге назначьте права, чтобы разрешить эти задачи.

В этом примере предполагается наличие имени входа SQL (DDUser01), но если вы создали имя входа Windows, используйте его.

```sql
USE RevoDeepDive
GO

EXEC sp_addrolemember 'db_owner', 'DDUser01'
GRANT EXECUTE ANY EXTERNAL SCRIPT TO DDUser01
GO
```

## <a name="troubleshoot-connections"></a>Устранение проблем с подключениями

В этом разделе перечислены некоторые распространенные проблемы, которые могут возникнуть в процессе настройки базы данных.

- **Как проверить подключение к базе данных и запросы SQL?**
  
    Перед выполнением кода на языке R с помощью сервера может потребоваться проверить, доступна ли база данных из среды разработки R. [Обозреватель сервера Visual Studio](https://docs.microsoft.com/previous-versions/x603htbk(v=vs.140)) и [среда SQL Server Management Studio](../../ssms/download-sql-server-management-studio-ssms.md) являются бесплатными средствами с эффективными возможностями подключения к базам данных и функциями управления.
  
    Если вы не хотите устанавливать дополнительные средства управления базами данных, то можете создать тестовое подключение к экземпляру SQL Server с помощью компонента [Администратор источников данных ODBC](https://docs.microsoft.com/sql/odbc/admin/odbc-data-source-administrator?view=sql-server-2017) на панели управления. Если база данных настроена правильно и вы ввели верные имя пользователя и пароль, то вы увидите созданную базу данных и сможете выбрать ее в качестве базы данных по умолчанию.
  
    Распространенные причины ошибок подключения — то, что удаленные подключения не включены для сервера или не включен протокол именованных каналов. Дополнительные советы по устранению неполадок можно найти в этой статье: [Устранение неполадок при соединении с ядром СУБД SQL Server](https://docs.microsoft.com/sql/database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine).
  
- **Почему имя таблицы имеет префикс datareader?**
  
    При указании схемы по умолчанию **db_datareader**для пользователя все таблицы и другие объекты, создаваемые этим пользователем, будут иметь префикс в виде имени этой *схемы*. Схема напоминает папку, которую можно добавить к базе данных для упорядочения объектов. Схема также определяет права пользователя в базе данных.
  
    Если схема связана с одним именем пользователя, этот пользователь называется _владельцем схемы_. Когда вы создаете объект, он всегда создается в вашей собственной схеме, если вы специально не укажете, что он должен быть создан в другой схеме.
  
    Например, если вы создаете таблицу с именем **TestData** и ваша схема по умолчанию — **db_datareader**, таблица будет создана с именем `<database_name>.db_datareader.TestData`.
  
    По этой причине база данных может содержать несколько таблиц с одинаковыми именами, если они относятся к разным схемам.
   
    Если вы ищете таблицу, но не указали схему, сервер базы данных будет вести поиск в вашей собственной схеме. Поэтому нет необходимости указывать имя схемы при доступе к таблицам в схеме, связанной в вашим именем входа.
  
- **У меня нет прав DDL. Могу ли я работать с учебником?**
  
    Да, но следует попросить кого-либо предварительно загрузить данные в таблицы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и перейти к следующему учебнику. Функции, требующие прав DDL, в этом учебнике по мере возможности опущены.

    Кроме того, попросите администратора предоставить вам разрешение EXECUTE ANY EXTERNAL SCRIPT. Оно необходимо для выполнения скриптов R, будь то удаленно или через `sp_execute_external_script`.

## <a name="next-steps"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Создание объектов данных SQL Server с помощью функции RxSqlServerData](../../machine-learning/tutorials/deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)