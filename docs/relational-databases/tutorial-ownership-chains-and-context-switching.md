---
title: Руководство. Цепочки владения и переключение контекста | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: quickstart
helpviewer_keywords:
- context switching [SQL Server], tutorials
- ownership chains [SQL Server]
ms.assetid: db5d4cc3-5fc5-4cf5-afc1-8d4edc1d512b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5f010b08f4e9bb7687d45175a70f8d619758e561
ms.sourcegitcommit: 2a06c87aa195bc6743ebdc14b91eb71ab6b91298
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2019
ms.locfileid: "72906994"
---
# <a name="tutorial-ownership-chains-and-context-switching"></a>Руководство. Цепочки владения и переключение контекста
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
В этом учебнике приведен пример, в котором рассматриваются основные понятия безопасности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , включая цепочки владения и переключение контекста.  
  
> [!NOTE]  
> Для запуска кода в этом учебнике необходимо, чтобы был настроен режим смешанной безопасности. Кроме того, необходимо наличие установленной базы данных AdventureWorks2017. Дополнительные сведения о смешанном режиме безопасности см. в разделе [Выбор режима проверки подлинности](../relational-databases/security/choose-an-authentication-mode.md).  
  
## <a name="scenario"></a>Сценарий  
В этом сценарии двум пользователям нужны учетные записи для доступа к данным о заказах на покупку, которые хранятся в базе данных AdventureWorks2017. Требования:  
  
-   Пользователь первой учетной записи (ТестовыйМенеджер) должен видеть все сведения о каждом заказе на покупку.  
-   Пользователь второй учетной записи (ТестовыйСотрудник) должен видеть номера заказов на покупку, даты заказов, даты отгрузки, коды продуктов, а также количество отправленных и полученных экземпляров продукта в заказе по номеру заказа (для заказов, получаемых частичной отгрузкой).  
-   Все другие учетные записи должны сохранять текущие разрешения.   
Чтобы выполнялись требования этого сценария, этот пример разбит на 4 части, в которых проиллюстрированы основные понятия, касающиеся цепочек владения и переключения контекста.  
  
1.  Настройка среды.   
2.  Создание хранимой процедуры для получения доступа к данным по заказам на покупку.   
3.  Доступ к данным через хранимую процедуру.  
4.  Сброс среды.  

Каждый блок кода в этом примере объясняется по порядку. Чтобы скопировать весь пример, см. раздел [Пример целиком](#CompleteExample) в конце этого учебника.

## <a name="prerequisites"></a>предварительные требования
Для работы с этим учебником требуется среда SQL Server Management Studio, доступ к серверу SQL Server и база данных AdventureWorks.

- Установите [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
- Установите выпуск [SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads).
- Скачайте [примеры баз данных AdventureWorks2017](https://docs.microsoft.com/sql/samples/adventureworks-install-configure).

Инструкции по восстановлению базы данных в SQL Server Management Studio см. в разделе [Восстановление базы данных](https://docs.microsoft.com/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms).   
  
## <a name="1-configure-the-environment"></a>1. Настройка среды  
С помощью среды [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] и приведенного ниже кода откройте базу данных `AdventureWorks2017`, затем с помощью инструкции `CURRENT_USER` [!INCLUDE[tsql](../includes/tsql-md.md)] проверьте, отображается ли пользователь dbo в качестве контекста.  
  
```sql
USE AdventureWorks2017;  
GO  
SELECT CURRENT_USER AS 'Current User Name';  
GO  
```  
  
Дополнительные сведения об инструкции CURRENT_USER см. в разделе [CURRENT_USER (Transact-SQL)](../t-sql/functions/current-user-transact-sql.md).  
  
От имени пользователя dbo создайте с помощью этого кода двух пользователей на сервере и в базе данных AdventureWorks2017.  
  
```sql
CREATE LOGIN TestManagerUser   
    WITH PASSWORD = '340$Uuxwp7Mcxo7Khx';  
GO  
CREATE USER TestManagerUser   
   FOR LOGIN TestManagerUser  
   WITH DEFAULT_SCHEMA = Purchasing;  
GO   
  
CREATE LOGIN TestEmployeeUser  
    WITH PASSWORD = '340$Uuxwp7Mcxo7Khy';  
GO  
CREATE USER TestEmployeeUser   
   FOR LOGIN TestEmployeeUser;  
GO   
```  
  
Дополнительные сведения об инструкции CREATE USER см. в разделе [CREATE USER (Transact-SQL)](../t-sql/statements/create-user-transact-sql.md). Дополнительные сведения об инструкции CREATE LOGIN см. в разделе [CREATE LOGIN (Transact-SQL)](../t-sql/statements/create-login-transact-sql.md).  
  
Изменить владельца схемы `Purchasing` на учетную запись `TestManagerUser` можно с помощью приведенного ниже кода. Это позволит учетной записи использовать все инструкции доступа языка обработки данных DML (например, разрешения `SELECT` или `INSERT` ) для объектов, которые содержит эта схема. `TestManagerUser` также предоставляет возможность создавать хранимые процедуры.  
  
```sql
/* Change owner of the Purchasing Schema to TestManagerUser */  
ALTER AUTHORIZATION   
   ON SCHEMA::Purchasing   
   TO TestManagerUser;  
GO  
  
GRANT CREATE PROCEDURE   
   TO TestManagerUser   
   WITH GRANT OPTION;  
GO  
```  
  
Дополнительные сведения об инструкции GRANT см. в разделе [GRANT (Transact-SQL)](../t-sql/statements/grant-transact-sql.md). Дополнительные сведения о хранимых процедурах см. в разделе [Хранимые процедуры (компонент Database Engine)](../relational-databases/stored-procedures/stored-procedures-database-engine.md). Плакат со всеми разрешениями [!INCLUDE[ssDE](../includes/ssde-md.md)] см. по ссылке [https://aka.ms/sql-permissions-poster](https://aka.ms/sql-permissions-poster).  
  
## <a name="2-create-a-stored-procedure-to-access-data"></a>2. Создание хранимой процедуры для доступа к данным  
Для переключения контекста внутри базы данных используйте инструкцию EXECUTE AS. Инструкции EXECUTE AS требуются разрешения IMPERSONATE.  
  
С помощью инструкции `EXECUTE AS` в приведенном ниже коде измените контекст на `TestManagerUser` и создайте хранимую процедуру, показывающую только те данные, которые должны быть видны пользователю `TestEmployeeUser`. Для соответствия требованиям хранимая процедура принимает одну переменную для номера заказа на покупку и не показывает финансовую информацию, а предложение WHERE ограничивает результаты для частичных отгрузок.  
  
```sql
EXECUTE AS LOGIN = 'TestManagerUser'  
GO  
SELECT CURRENT_USER AS 'Current User Name';  
GO  
  
/* Note: The user that calls the EXECUTE AS statement must have IMPERSONATE permissions on the target principal */  
CREATE PROCEDURE usp_ShowWaitingItems @ProductID int  
AS  
BEGIN   
   SELECT a.PurchaseOrderID, a.OrderDate, a.ShipDate  
      , b.ProductID, b.OrderQty, b.ReceivedQty  
   FROM Purchasing.PurchaseOrderHeader a  
      INNER JOIN Purchasing.PurchaseOrderDetail b  
         ON a.PurchaseOrderID = b.PurchaseOrderID  
   WHERE b.OrderQty > b.ReceivedQty  
      AND @ProductID = b.ProductID  
   ORDER BY b.ProductID ASC  
END  
GO  
```  
  
В данный момент пользователь `TestEmployeeUser` не имеет доступа к объектам базы данных. Следующий код (все еще в контексте `TestManagerUser` ) предоставляет учетной записи пользователя возможность запрашивать информацию из базовой таблицы через хранимую процедуру.  
  
```sql
GRANT EXECUTE  
   ON OBJECT::Purchasing.usp_ShowWaitingItems  
   TO TestEmployeeUser;  
GO  
```  
  
Хотя схема не была указана явно, хранимая процедура является частью схемы `Purchasing` , поскольку пользователь `TestManagerUser` по умолчанию связан со схемой `Purchasing` . Для поиска объектов можно использовать информацию из системного каталога, как показано в следующем коде.  
  
```sql
SELECT a.name AS 'Schema'  
   , b.name AS 'Object Name'  
   , b.type AS 'Object Type'  
FROM sys.schemas a  
   INNER JOIN sys.objects b  
      ON a.schema_id = b.schema_id   
WHERE b.name = 'usp_ShowWaitingItems';  
GO  
```  
  
После завершения этого раздела примера код переключает контекст обратно на dbo с помощью инструкции `REVERT`.  
  
```sql
REVERT;  
GO  
```  
  
Дополнительные сведения об инструкции REVERT см. в разделе [REVERT (Transact-SQL)](../t-sql/statements/revert-transact-sql.md).  
  
## <a name="3-access-data-through-the-stored-procedure"></a>3. Доступ к данным через хранимую процедуру  
`TestEmployeeUser` не обладает разрешениями на объекты базы данных [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] , кроме разрешения на вход в систему и прав, присвоенных роли базы данных public. Следующий код возвращает ошибку при попытке обращения `TestEmployeeUser` к базовым таблицам.  
  
```sql
EXECUTE AS LOGIN = 'TestEmployeeUser'  
GO  
SELECT CURRENT_USER AS 'Current User Name';  
GO  
/* This won't work */  
SELECT *  
FROM Purchasing.PurchaseOrderHeader;  
GO  
SELECT *  
FROM Purchasing.PurchaseOrderDetail;  
GO  
```  

Возвращается следующая ошибка:
```
Msg 229, Level 14, State 5, Line 6
The SELECT permission was denied on the object 'PurchaseOrderHeader', database 'AdventureWorks2017', schema 'Purchasing'.
```
  
Поскольку объекты, на которые ссылается процедура, созданная в предыдущем разделе, принадлежат `TestManagerUser` по причине владения схемой `Purchasing` , `TestEmployeeUser` может получить доступ к базовым таблицам через хранимую процедуру. Следующий код, все еще в контексте `TestEmployeeUser` , проводит заказ на покупку 952 как параметр.  
  
```sql
EXEC Purchasing.usp_ShowWaitingItems 952  
GO  
```  
  
## <a name="4-reset-the-environment"></a>4. Сброс среды  
Следующий код с помощью команды `REVERT` изменяет контекст текущей учетной записи обратно на `dbo`и затем выполняет сброс среды.  
  
```sql
REVERT;  
GO  
ALTER AUTHORIZATION   
ON SCHEMA::Purchasing TO dbo;  
GO  
DROP PROCEDURE Purchasing.usp_ShowWaitingItems;  
GO  
DROP USER TestEmployeeUser;  
GO  
DROP USER TestManagerUser;  
GO  
DROP LOGIN TestEmployeeUser;  
GO  
DROP LOGIN TestManagerUser;  
GO  
```  
  
## <a name="CompleteExample"></a>Пример целиком  
В этом разделе приведен полный код примера.  
  
> [!NOTE]  
> В этот код не включены две ошибки, которые иллюстрировали невозможность `TestEmployeeUser` получить данные из базовых таблиц.  
  
```sql
/*   
Script:       UserContextTutorial.sql  
Author:       Microsoft  
Last Updated: Books Online  
Conditions:   Execute as DBO or sysadmin in the AdventureWorks database  
Section 1:    Configure the Environment   
*/  
USE AdventureWorks2017;  
GO  
SELECT CURRENT_USER AS 'Current User Name';  
GO  
/* Create server and database users */  
CREATE LOGIN TestManagerUser   
    WITH PASSWORD = '340$Uuxwp7Mcxo7Khx';  
  
GO  
  
CREATE USER TestManagerUser   
   FOR LOGIN TestManagerUser  
   WITH DEFAULT_SCHEMA = Purchasing;  
GO   
  
CREATE LOGIN TestEmployeeUser  
    WITH PASSWORD = '340$Uuxwp7Mcxo7Khy';  
GO  
CREATE USER TestEmployeeUser   
   FOR LOGIN TestEmployeeUser;  
GO   
  
/* Change owner of the Purchasing Schema to TestManagerUser */  
ALTER AUTHORIZATION   
   ON SCHEMA::Purchasing   
   TO TestManagerUser;  
GO  
  
GRANT CREATE PROCEDURE   
   TO TestManagerUser   
   WITH GRANT OPTION;  
GO  
  
/*   
Section 2: Switch Context and Create Objects  
*/  
EXECUTE AS LOGIN = 'TestManagerUser';  
GO  
SELECT CURRENT_USER AS 'Current User Name';  
GO  
  
/* Note: The user that calls the EXECUTE AS statement must have IMPERSONATE permissions on the target principal */  
CREATE PROCEDURE usp_ShowWaitingItems @ProductID int  
AS  
BEGIN   
   SELECT a.PurchaseOrderID, a.OrderDate, a.ShipDate  
      , b.ProductID, b.OrderQty, b.ReceivedQty  
   FROM Purchasing.PurchaseOrderHeader AS a  
      INNER JOIN Purchasing.PurchaseOrderDetail AS b  
         ON a.PurchaseOrderID = b.PurchaseOrderID  
   WHERE b.OrderQty > b.ReceivedQty  
      AND @ProductID = b.ProductID  
   ORDER BY b.ProductID ASC  
END;  
GO  
  
/* Give the employee the ability to run the procedure */  
GRANT EXECUTE   
   ON OBJECT::Purchasing.usp_ShowWaitingItems  
   TO TestEmployeeUser;  
GO   
  
/* Notice that the stored procedure is located in the Purchasing   
schema. This also demonstrates system catalogs */  
SELECT a.name AS 'Schema'  
   , b.name AS 'Object Name'  
   , b.type AS 'Object Type'  
FROM sys.schemas AS a  
   INNER JOIN sys.objects AS b  
      ON a.schema_id = b.schema_id   
WHERE b.name = 'usp_ShowWaitingItems';  
GO  
  
/* Go back to being the dbo user */  
REVERT;  
GO  
  
/*  
Section 3: Switch Context and Observe Security   
*/  
EXECUTE AS LOGIN = 'TestEmployeeUser';  
GO  
SELECT CURRENT_USER AS 'Current User Name';  
GO  
EXEC Purchasing.usp_ShowWaitingItems 952;  
GO  
  
/*   
Section 4: Clean Up Example  
*/  
REVERT;  
GO  
ALTER AUTHORIZATION   
ON SCHEMA::Purchasing TO dbo;  
GO  
DROP PROCEDURE Purchasing.usp_ShowWaitingItems;  
GO  
DROP USER TestEmployeeUser;  
GO  
DROP USER TestManagerUser;  
GO  
DROP LOGIN TestEmployeeUser;  
GO  
DROP LOGIN TestManagerUser;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
[Центр обеспечения безопасности для базы данных Azure SQL и SQL Server Database Engine](../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
  
  
