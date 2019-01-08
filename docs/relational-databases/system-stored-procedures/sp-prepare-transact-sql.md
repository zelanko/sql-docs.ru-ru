---
title: sp_prepare (Transact SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 02/28/2018
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursor_prepare_TSQL
- sp_cursor_prepare
dev_langs:
- TSQL
helpviewer_keywords:
- sp_prepare
ms.assetid: f328c9eb-8211-4863-bafa-347e1bf7bb3f
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9b52f71577bed8a0433c8d516cdc9cbd877066e4
ms.sourcegitcommit: f46fd79fd32a894c8174a5cb246d9d34db75e5df
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/26/2018
ms.locfileid: "53785935"
---
# <a name="spprepare-transact-sql"></a>sp_prepare (Transact SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

Подготавливает параметризованную [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции и возвращает инструкцию *обрабатывать* для выполнения.  `sp_prepare` вызывается при указании ID = 11 в пакете потока табличных данных.  
  
 ![Значок ссылки на статью](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на статью") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sp_prepare handle OUTPUT, params, stmt, options  
```  
  
## <a name="arguments"></a>Аргументы  
 *Дескриптор*  
 Сформированный SQL Server *подготовленный дескриптор* идентификатор. *обрабатывать* является обязательным параметром с **int** возвращаемое значение.  
  
 *params*  
 Указывает параметризованные инструкции. *Params* определения переменных подставляется вместо маркеров параметров в инструкции. *params* является обязательным параметром, который вызывает для **ntext**, **nchar**, или **nvarchar** входного значения. Если инструкция не параметризована, необходимо ввести значение NULL.  
  
 *stmt*  
 Определяет результирующий набор курсора. *Stmt* параметр является обязательным и требует **ntext**, **nchar**, или **nvarchar** входного значения.  
  
 *Параметры*  
 Необязательный параметр, возвращающий описание столбцов результирующего набора курсора. *Параметры* требует следующих входного значения int:  
  
|Значение|Описание|  
|-----------|-----------------|  
|0x0001|RETURN_METADATA|  
  
## <a name="examples"></a>Примеры  
A. В следующем примере подготавливается и выполняется простая инструкция.  
  
```sql  
DECLARE @P1 int;  
EXEC sp_prepare @P1 output,   
    N'@P1 nvarchar(128), @P2 nvarchar(100)',  
    N'SELECT database_id, name FROM sys.databases WHERE name=@P1 AND state_desc = @P2';  
EXEC sp_execute @P1, N'tempdb', N'ONLINE';  
EXEC sp_unprepare @P1;  
```

Б. В следующем примере приложение подготавливает инструкцию в базе данных AdventureWorks2016 и более поздней версии выполняется с помощью дескриптора.

```sql
-- Prepare query
DECLARE @P1 int;  
EXEC sp_prepare @P1 output,   
    N'@Param int',  
    N'SELECT *
FROM Sales.SalesOrderDetail AS sod
INNER JOIN Production.Product AS p ON sod.ProductID = p.ProductID
WHERE SalesOrderID = @Param
ORDER BY Style DESC;';  

-- Return handle for calling application
SELECT @P1;
GO
```
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]

```
-----------
1

(1 row affected)
```

Затем приложение выполняет запрос, используя дескриптор значение 1, удалялись подготовленного плана.

```sql
EXEC sp_execute 1, 49879;  
GO

EXEC sp_execute 1, 48766;
GO

EXEC sp_unprepare 1; 
GO
```
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  

