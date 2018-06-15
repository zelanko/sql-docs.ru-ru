---
title: Изменение XML-индексов | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: xml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- XML indexes [SQL Server], modifying
- modifying indexes
ms.assetid: 24d50fe1-c6ec-49e6-91a3-9791851ba53d
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 87e16b7c52a01b3755a5e7fb7d232f937470953c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "33014261"
---
# <a name="modify-xml-indexes"></a>Изменение XML-индексов
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Для изменения существующих XML-индексов и индексов других типов можно использовать DDL-инструкцию [ALTER INDEX (Transact-SQL)](../../t-sql/statements/alter-index-transact-sql.md)[!INCLUDE[tsql](../../includes/tsql-md.md)]. Однако к XML-индексам могут применяться не все параметры ALTER INDEX. В частности, недопустимо использование следующих параметров:  
  
-   Параметр повторного создания и установки IGNORE_DUP_KEY для XML-индексов недопустим. Для вторичных XML-индексов параметр повторного создания ONLINE должен быть установлен в OFF. В инструкции ALTER INDEX недопустим параметр DROP_EXISTING.  
  
-   Изменения ограничения первичного ключа в пользовательской таблице на XML-индексы автоматически не распространяются. Пользователь должен вначале удалить, а затем вновь создать XML-индекс.  
  
-   Инструкция ALTER INDEX ALL применяется как к обычным, так и к XML-индексам. Если заданы параметры индексирования, недопустимые для обоих типов индексов, то вся инструкция завершится ошибкой.  
  
## <a name="example-modifying-an-xml-index"></a>Пример. Изменение XML-индекса  
 В следующем примере создается XML-индекс, после чего производится его изменение — установка параметра `ALLOW_ROW_LOCKS` в значение `OFF`. Когда параметр `ALLOW_ROW_LOCKS` установлен в значение `OFF`, строки не блокируются и доступ к указанным индексам осуществляется при помощи блокировок уровня страницы и таблицы.  
  
```  
CREATE TABLE T (Col1 INT PRIMARY KEY, XmlCol XML)  
GO  
-- Create primary XML index.   
CREATE PRIMARY XML INDEX PIdx_T_XmlCol   
ON T(XmlCol)  
GO  
-- Note the type 3 is index on XML type.  
SELECT *  
FROM sys.xml_indexes  
WHERE object_id = object_id('T')  
AND name='PIdx_T_XmlCol'  
  
-- Modify and set an index option.  
ALTER INDEX PIdx_T_XmlCol on T   
SET (ALLOW_ROW_LOCKS = OFF)  
```  
  
## <a name="example-disabling-and-enabling-an-xml-index"></a>Пример. Отключение и включение XML-индекса  
 По умолчанию XML-индекс включен. Если XML-индекс отключен, то запросы, выполняемые для XML-столбца, не пользуются им. Для включения XML-индекса используется инструкция `ALTER INDEX` с параметром `REBUILD` .  
  
```  
CREATE TABLE T (Col1 INT PRIMARY KEY, XmlCol XML)  
GO  
CREATE PRIMARY XML INDEX PIdx_T_XmlCol ON T(XmlCol)  
GO  
ALTER INDEX PIdx_T_XmlCol on T DISABLE  
Go  
-- Verify index is disabled.  
SELECT *  
FROM sys.xml_indexes  
WHERE object_id = object_id('T')  
AND name='PIdx_T_XmlCol'  
-- Rebuild the index.  
ALTER INDEX PIdx_T_XmlCol on T REBUILD  
Go  
```  
  
## <a name="see-also"></a>См. также:  
 [XML-индексы (SQL Server)](../../relational-databases/xml/xml-indexes-sql-server.md)  
  
  
