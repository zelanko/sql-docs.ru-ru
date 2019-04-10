---
title: Переименование базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 10/02/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server], renaming
- renaming databases
ms.assetid: 44c69d35-abcb-4da3-9370-5e0bc9a28496
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 0e3d57094a6863bb5b6bebd96f05ed57a1fcc25f
ms.sourcegitcommit: 1a4aa8d2bdebeb3be911406fc19dfb6085d30b04
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/03/2019
ms.locfileid: "58872024"
---
# <a name="rename-a-database"></a>Переименование базы данных

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  В этом разделе описывается, как переименовать пользовательскую базу данных в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] или базу данных SQL Azure с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Имя базы данных может содержать все символы, соответствующие правилам для идентификаторов.  
  
## <a name="in-this-topic"></a>В этом разделе
  
- Перед началом работы  
  
     [Ограничения](#limitations-and-restrictions)  
  
     [безопасность](#security)  
  
- Переименование базы данных с использованием следующих средств:  
  
     [SQL Server Management Studio](#rename-a-database-using-sql-server-management-studio)  
  
     [Transact-SQL](#rename-a-database-using-transact-sql)  
  
- **Дальнейшие действия.**  [После переименования базы данных](#backup-after-renaming-a-database)  

> [!NOTE]
> Чтобы переименовать базу данных в хранилище данных SQL Azure или в Parallel Data Warehouse, используйте инструкцию [RENAME (Transact-SQL)](../../t-sql/statements/rename-transact-sql.md).
  
## <a name="before-you-begin"></a>Перед началом
  
### <a name="limitations-and-restrictions"></a>Ограничения  
  
- Системные базы данных не могут быть переименованы.
- Имя базы данных невозможно изменить, пока другие пользователи обращаются к этой базе данных. 
  - В SQL Server можно установить для базы данных однопользовательский режим, чтобы закрыть все открытые соединения. Дополнительные сведения см. в разделе [Установка однопользовательского режима базы данных](../../relational-databases/databases/set-a-database-to-single-user-mode.md).
  - В базе данных SQL Azure необходимо убедиться, что отсутствуют открытые подключения других пользователей к базе данных, которую требуется переименовать.
  
### <a name="security"></a>безопасность  
  
#### <a name="permissions"></a>Разрешения

Необходимо разрешение ALTER на базу данных.  
  
## <a name="rename-a-database-using-sql-server-management-studio"></a>Переименование базы данных с помощью SQL Server Management Studio

Чтобы переименовать базу данных SQL Server или SQL Azure с помощью SQL Server Management Studio, выполните следующие действия.
  
1. В **обозревателе объектов** установите соединение с экземпляром SQL.  
  
2. Убедитесь, что отсутствуют открытые подключения к базе данных. Если используется SQL Server, можно [перевести базу данных в однопользовательский режим](../../relational-databases/databases/set-a-database-to-single-user-mode.md), чтобы закрыть все открытые подключения и запретить подключение других пользователей, пока производится изменение имени этой базы данных.  
  
3. В обозревателе объектов разверните узел **Базы данных**, щелкните правой кнопкой мыши базу данных, которую необходимо переименовать, а затем выберите пункт **Переименовать**.  
  
4. Введите новое имя базы данных и нажмите кнопку **ОК**.  
  
## <a name="rename-a-database-using-transact-sql"></a>Переименование базы данных с помощью Transact-SQL  
  
### <a name="to-rename-a-sql-server-database-by-placing-it-in-single-user-mode"></a>Переименование базы данных SQL Server путем перевода ее в однопользовательский режим

Выполните следующие действия, чтобы переименовать базу данных SQL Server с помощью T-SQL в SQL Server Management Studio, включая действия по переводу базы данных в однопользовательский режим и возврат ее в многопользовательский режим после переименования.
  
1. Подключитесь к базе данных `master` для своего экземпляра.  
2. Откройте окно запроса.  
3. Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере имя базы данных `MyTestDatabase` изменяется на `MyTestDatabaseCopy`.
  
   ```sql
   USE master;  
   GO  
   ALTER DATABASE MyTestDatabase SET SINGLE_USER WITH ROLLBACK IMMEDIATE
   GO
   ALTER DATABASE MyTestDatabase MODIFY NAME = MyTestDatabaseCopy ;
   GO  
   ALTER DATABASE MyTestDatabaseCopy SET MULTI_USER
   GO
   ```  

### <a name="to-rename-an-azure-sql-database-database"></a>Переименование базы данных SQL Azure

Выполните следующие действия, чтобы переименовать базу данных SQL Azure с помощью T-SQL в SQL Server Management Studio.
  
1. Подключитесь к базе данных `master` для своего экземпляра.  
2. Откройте окно запроса.
3. Убедитесь, что больше никто не использует эту базу данных.
4. Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере имя базы данных `MyTestDatabase` изменяется на `MyTestDatabaseCopy`.
  
   ```sql
   ALTER DATABASE MyTestDatabase MODIFY NAME = MyTestDatabaseCopy ;
   ```  

## <a name="backup-after-renaming-a-database"></a>Резервное копирование после переименования базы данных  

После переименования базы данных в SQL Server выполните резервное копирование базы данных `master`. В базе данных SQL Azure это не требуется, так как резервное копирование выполняется автоматически.  
  
## <a name="see-also"></a>См. также:

- [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)
- [Идентификаторы баз данных](../../relational-databases/databases/database-identifiers.md)  