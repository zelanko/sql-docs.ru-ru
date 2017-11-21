---
title: "SCOPE_IDENTITY (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SCOPE_IDENTITY
- SCOPE_IDENTITY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- identity columns [SQL Server], SCOPE_IDENTITY function
- SCOPE_IDENTITY function
- last-inserted identity values
- identity values [SQL Server], last-inserted
ms.assetid: eef24670-059b-4f10-91d4-a67bc1ed12ab
caps.latest.revision: 36
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1950d65a35d6fab52025d069e0338493ee7c639d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="scopeidentity-transact-sql"></a>SCOPE_IDENTITY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает последнее значение идентификатора, вставленное в столбец идентификаторов в той же области. Областью является модуль, что подразумевает хранимую процедуру, триггер, функцию или пакет. Таким образом Если две инструкции принадлежат одной хранимой процедуры, функции или пакета, они находятся в той же области.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
SCOPE_IDENTITY()  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **numeric(38,0)**  
  
## <a name="remarks"></a>Замечания  
 SCOPE_IDENTITY, IDENT_CURRENT и @@IDENTITY , аналогичные функции, так как они возвращают значения, вставленные в столбцы идентификаторов.  
  
 Функция IDENT_CURRENT не ограничена областью действия и сеансом, но ограничена указанной таблицей. Функция IDENT_CURRENT возвращает значение, созданное для указанной таблицы в любом сеансе и области. Дополнительные сведения см. в разделе [IDENT_CURRENT &#40; Transact-SQL &#41; ](../../t-sql/functions/ident-current-transact-sql.md).  
  
 SCOPE_IDENTITY и @@IDENTITY возвращают последние значения идентификатора, сформированное в любой таблице в текущем сеансе. Однако функция SCOPE_IDENTITY возвращает значения, вставленные только в пределах текущей области; @@IDENTITY не ограничена определенной области.  
  
 Например, существует две таблицы, T1 и T2, и для таблицы T1 определен триггер INSERT. Когда в таблицу T1 вставляется строка, триггер срабатывает и добавляет строку в таблицу T2. В этом сценарии показано две области: вставка в таблицу T1 и вставка триггером в таблицу T2.  
  
 Предположим, что T1 и T2 имеют столбцы идентификаторов@IDENTITY и SCOPE_IDENTITY возвращают разные значения в конце инструкции INSERT в T1. @@IDENTITY возвращает последнее значение столбца identity, вставленное во всех областях в текущем сеансе. Это значение, вставленное в таблицу T2. Функция SCOPE_IDENTITY() возвращает значение идентификатора, вставленное в таблицу T1. Это было последним добавлением, произошедшим в заданной области. Функция SCOPE_IDENTITY() возвращает значение null, если функция вызывается для любой инструкции INSERT в столбец идентификаторов в области.  
  
 Неудачно завершившиеся инструкции и транзакции могут изменить текущий идентификатор таблицы и создать пропуски в значениях столбца идентификаторов. Для значения идентификатора никогда не производится откат, несмотря на то, что транзакция, пытавшаяся вставить в таблицу значение, не была зафиксирована. Например, если инструкция INSERT привела к ошибке из-за нарушения ограничения IGNORE_DUP_KEY, текущее значение идентификатора для таблицы все равно увеличивается.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-identity-and-scopeidentity-with-triggers"></a>A. С помощью@IDENTITY и SCOPE_IDENTITY с триггерами  
 В следующем примере показано создание двух таблиц, `TZ` и `TY`, и триггера INSERT для таблицы `TZ`. Когда в таблицу `TZ` добавляется строка, триггер (`Ztrig`) срабатывает и добавляет строку в таблицу `TY`.  
  
```sql  
USE tempdb;  
GO  
CREATE TABLE TZ (  
   Z_id  int IDENTITY(1,1)PRIMARY KEY,  
   Z_name varchar(20) NOT NULL);  
  
INSERT TZ  
   VALUES ('Lisa'),('Mike'),('Carla');  
  
SELECT * FROM TZ;  
```     
Результирующий набор: это, как выглядит таблица TZ.  
  
```  
Z_id   Z_name  
-------------  
1      Lisa  
2      Mike  
3      Carla  
```  
```sql 
CREATE TABLE TY (  
   Y_id  int IDENTITY(100,5)PRIMARY KEY,  
   Y_name varchar(20) NULL);  
  
INSERT TY (Y_name)  
   VALUES ('boathouse'), ('rocks'), ('elevator');  
  
SELECT * FROM TY;  
```   
Результирующий набор: это внешний вид TY:  
```  
Y_id  Y_name  
---------------  
100   boathouse  
105   rocks  
110   elevator  
```  

Создайте триггер, который вставляет строку в таблице за этот год при вставке строки в таблице TZ.  
```sql  
CREATE TRIGGER Ztrig  
ON TZ  
FOR INSERT AS   
   BEGIN  
   INSERT TY VALUES ('')  
   END;  
```  
ЗАПУСТИТЬ триггер и определить, какие значения идентификаторов, можно получить с помощью @@IDENTITY и функции SCOPE_IDENTITY.   
```sql
INSERT TZ VALUES ('Rosalie');  
  
SELECT SCOPE_IDENTITY() AS [SCOPE_IDENTITY];  
GO  
SELECT @@IDENTITY AS [@@IDENTITY];  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
```
/*SCOPE_IDENTITY returns the last identity value in the same scope. This was the insert on table TZ.*/`  
SCOPE_IDENTITY  
4  

/*@@IDENTITY returns the last identity value inserted to TY by the trigger. 
  This fired because of an earlier insert on TZ.*/
@@IDENTITY  
115  
```  
  
### <a name="b-using-identity-and-scopeidentity-with-replication"></a>Б. С помощью@IDENTITY и SCOPE_IDENTITY() с репликацией  
 В следующем примере показано, как использовать системную переменную `@@IDENTITY` и функцию `SCOPE_IDENTITY()`, чтобы вставить данные в базу данных, опубликованную для репликации слиянием. Обе таблицы из примера находятся в образце базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]: таблица `Person.ContactType` не опубликована, а таблица `Sales.Customer` опубликована. При репликации слиянием в опубликованные таблицы добавляются триггеры. Таким образом, инструкция `@@IDENTITY` может возвращать значение из вставки в системную таблицу репликации, а не в пользовательскую таблицу.  
  
 `Person.ContactType` Таблица имеет максимальное значение идентификатора равное 20. При вставке строки в таблицу `@@IDENTITY` и `SCOPE_IDENTITY()` возвращают одно и тоже значение.  
  
```sql  
USE AdventureWorks2012;  
GO  
INSERT INTO Person.ContactType ([Name]) VALUES ('Assistant to the Manager');  
GO  
SELECT SCOPE_IDENTITY() AS [SCOPE_IDENTITY];  
GO  
SELECT @@IDENTITY AS [@@IDENTITY];  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
```  
SCOPE_IDENTITY  
21  
@@IDENTITY  
21
```  
  
 Максимальное значение идентификатора в таблице `Sales.Customer` равно 29483. Если строка вставляется в таблицу, инструкции `@@IDENTITY` и `SCOPE_IDENTITY()` возвращают разные значения. Инструкция `SCOPE_IDENTITY()` возвращает значение из вставки в таблицу пользователя, а инструкция `@@IDENTITY`  — из вставки в системную таблицу репликации. Инструкцию `SCOPE_IDENTITY()` следует применять для приложений, которым требуется доступ к вставленному значению идентификатора.  
  
```sql  
INSERT INTO Sales.Customer ([TerritoryID],[PersonID]) VALUES (8,NULL);  
GO  
SELECT SCOPE_IDENTITY() AS [SCOPE_IDENTITY];  
GO  
SELECT @@IDENTITY AS [@@IDENTITY];  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
 ```
 SCOPE_IDENTITY  
 29484  
 @@IDENTITY  
 89
 ```  
  
## <a name="see-also"></a>См. также:  
 [@@IDENTITY &#40;Transact-SQL&#41;](../../t-sql/functions/identity-transact-sql.md)  
  
  

