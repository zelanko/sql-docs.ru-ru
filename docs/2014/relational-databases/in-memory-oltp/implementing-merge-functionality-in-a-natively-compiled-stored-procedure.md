---
title: Реализация функций слияния | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: d4bcdc36-3302-4abc-9b35-64ec2b920986
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: e762c1999a4206d5277050934e82b5d5d5c59371
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82715128"
---
# <a name="implementing-merge-functionality"></a>Реализация функции MERGE
  В зависимости от того, есть ли уже в базе данных такая строка, необходимо выполнить ее вставку или обновление.  
  
 Кроме использования инструкции `MERGE`, в [!INCLUDE[tsql](../../includes/tsql-md.md)] можно применить следующий подход:  
  
```sql  
UPDATE mytable SET col=@somevalue WHERE myPK = @parm  
IF @@ROWCOUNT = 0  
    INSERT mytable (columns) VALUES (@parm, @other values)  
```  
  
 Другой метод [!INCLUDE[tsql](../../includes/tsql-md.md)] для реализации слияния:  
  
```sql  
IF EXISTS (SELECT 1 FROM mytable WHERE myPK = @parm)  
    UPDATE....  
ELSE  
    INSERT  
```  
  
 Для скомпилированной в собственном коде хранимой процедуры  
  
```sql  
DECLARE @i  int  = 0  -- or whatever your PK data type is  
UPDATE mytable SET @i=myPK, othercolums = other values WHERE myPK = @parm  
IF @i = 0  
   INSERT....  
```  
  
## <a name="see-also"></a>См. также:  
 [Проблемы миграции, связанные с хранимыми процедурами, скомпилированными в собственном коде](migration-issues-for-natively-compiled-stored-procedures.md)   
 [Конструкции языка Transact-SQL, не поддерживаемые в выполняющейся в памяти OLTP](transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
