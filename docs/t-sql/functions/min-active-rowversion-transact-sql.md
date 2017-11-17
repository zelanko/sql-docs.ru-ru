---
title: "MIN_ACTIVE_ROWVERSION (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
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
- MIN_ACTIVE_ROWVERSION
- MIN_ACTIVE_ROWVERSION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MIN_ACTIVE_ROWVERSION function [Transact-SQL]
ms.assetid: 87c89547-8ea1-4820-b75e-36be683e4e10
caps.latest.revision: 11
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ed1254e0e35aa108d9866f30da49962b886a39ae
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="minactiverowversion-transact-sql"></a>MIN_ACTIVE_ROWVERSION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает наименьшее активное значение **rowversion** в текущей базе данных. Значение **rowversion** является активным, если оно используется в незафиксированной транзакции. Дополнительные сведения см. в разделе [rowversion &#40; Transact-SQL &#41; ](../../t-sql/data-types/rowversion-transact-sql.md).  
  
> [!NOTE]  
>  **Rowversion** тип данных, также называемая **timestamp**.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
MIN_ACTIVE_ROWVERSION  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 Возвращает **binary(8)** значение.  
  
## <a name="remarks"></a>Замечания  
 MIN_ACTIVE_ROWVERSION является является недетерминированной функцией, которая возвращает наименьшее активное **rowversion** значение в текущей базе данных. Новое значение **rowversion** обычно формируется, когда в таблице, содержащей столбец с типом **rowversion**, производится операция вставки или обновления. Если отсутствуют активные значения в базе данных, то функция MIN_ACTIVE_ROWVERSION возвращает то же значение, что и @@DBTS + 1.  
  
 Функция MIN_ACTIVE_ROWVERSION полезна для сценариев, например синхронизацию данных, использующих **rowversion** значения для группирования наборов изменений. Если приложение использует@DBTS а не MIN_ACTIVE_ROWVERSION, существует возможность пропуска изменения, которые активны во время синхронизации.  
  
 Функция MIN_ACTIVE_ROWVERSION не затрагивается изменениями на уровнях изоляции транзакции.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается **rowversion** значения с помощью `MIN_ACTIVE_ROWVERSION` и `@@DBTS`. Обратите внимание, что при отсутствии в базе данных активных транзакций эти значения будут другими.  
  
```  
-- Create a table that has a ROWVERSION column in it.  
CREATE TABLE RowVersionTestTable (rv ROWVERSION)  
GO  
  
-- Print the current values for the database.  
PRINT ''  
PRINT 'DBTS'  
PRINT @@DBTS  
PRINT 'MIN_ACTIVE_ROWVERSION'  
PRINT MIN_ACTIVE_ROWVERSION()   
GO  
---------------- Results ----------------  
--DBTS  
--0x00000000000007E2  
--MIN_ACTIVE_ROWVERSION  
--0x00000000000007E3  
  
-- Insert a row.  
INSERT INTO RowVersionTestTable VALUES (DEFAULT)  
SELECT * FROM RowVersionTestTable  
GO  
---------------- Results ----------------  
--rv  
--0x00000000000007E3  
  
-- Print the current values for the database.  
PRINT ''  
PRINT 'DBTS'  
PRINT @@DBTS  
PRINT 'MIN_ACTIVE_ROWVERSION'  
PRINT MIN_ACTIVE_ROWVERSION()  
GO  
---------------- Results ----------------  
--DBTS  
--0x00000000000007E3  
--MIN_ACTIVE_ROWVERSION  
--0x00000000000007E4  
  
-- Insert a new row inside a transaction but do not commit.  
BEGIN TRAN  
INSERT INTO RowVersionTestTable VALUES (DEFAULT)  
SELECT * FROM RowVersionTestTable  
GO  
---------------- Results ----------------  
--rv  
--0x00000000000007E3  
--0x00000000000007E4  
  
-- Print the current values for the database.  
PRINT ''  
PRINT 'DBTS'  
PRINT @@DBTS  
PRINT 'MIN_ACTIVE_ROWVERSION'  
PRINT MIN_ACTIVE_ROWVERSION()   
GO  
---------------- Results ----------------  
--DBTS  
--0x00000000000007E4  
--MIN_ACTIVE_ROWVERSION  
--0x00000000000007E4  
  
-- Commit the transaction.  
COMMIT  
GO  
  
-- Print the current values for the database.  
PRINT ''  
PRINT 'DBTS'  
PRINT @@DBTS  
PRINT 'MIN_ACTIVE_ROWVERSION'  
PRINT MIN_ACTIVE_ROWVERSION()  
GO  
---------------- Results ----------------  
--DBTS  
--0x00000000000007E4  
--MIN_ACTIVE_ROWVERSION  
--0x00000000000007E5  
```  
  
## <a name="see-also"></a>См. также:  
 [@@DBTS &#40;Transact-SQL&#41;](../../t-sql/functions/dbts-transact-sql.md)   
 [rowversion (Transact-SQL)](../../t-sql/data-types/rowversion-transact-sql.md)  
  
  

