---
title: DROP XML SCHEMA COLLECTION (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 11/25/2015
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP XML SCHEMA COLLECTION
- DROP_XML_SCHEMA_COLLECTION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- deleting XML schema collections
- XML schema collections [SQL Server], removing
- schema collections [SQL Server], removing
- removing XML schema collections
- dropping XML schema collections
- DROP XML SCHEMA COLLECTION statement
ms.assetid: d686f2f5-e03a-4ffe-a566-6036628f46f1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c2a02ae5bc9572265cc33392a02c596cfcfec0ff
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68072012"
---
# <a name="drop-xml-schema-collection-transact-sql"></a>DROP XML SCHEMA COLLECTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Удаляет всю коллекцию XML-схем и все ее компоненты.  
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DROP XML SCHEMA COLLECTION [ relational_schema. ]sql_identifier  
```  
  
## <a name="arguments"></a>Аргументы  
*relational_schema*  
Определяет имя реляционной схемы. Если не задано, предполагается использование реляционной схемы по умолчанию.  
  
*sql_identifier*  
Имя удаляемой коллекции схем XML.  
  
## <a name="remarks"></a>Remarks  
Удаление коллекции XML-схем является транзакционной операцией. Если удалить коллекцию схем XML внутри транзакции, а потом сделать откат, коллекция XML-схем не будет удалена.  
  
Коллекцию XML-схем нельзя удалить, если она используется. Таким образом, удаляемая коллекция не может быть в любом из следующих состояний:  
  
-   ассоциированной с любым параметром типа **xml** или столбцом;  
  
-   указанной в ограничениях любой из таблиц;  
  
-   той, на которую ссылается привязанная к схеме функция или хранимая процедура. Например, следующая функция блокирует коллекцию XML-схем `MyCollection`, так как функция включает `WITH SCHEMABINDING`. Если удалить ее, блокировки на XML SCHEMA COLLECTION не будет.  
  
    ```  
    CREATE FUNCTION dbo.MyFunction()  
    RETURNS int  
    WITH SCHEMABINDING  
    AS  
    BEGIN  
       ...  
       DECLARE @x XML(MyCollection)  
       ...  
    END;  
    ```  
  
## <a name="permissions"></a>Разрешения  
Для удаления XML SCHEMA COLLECTION необходимо обладать разрешением DROP для коллекции.  
  
## <a name="examples"></a>Примеры  
Следующий пример демонстрирует удаление коллекции XML-схем.  
  
```  
DROP XML SCHEMA COLLECTION ManuInstructionsSchemaCollection;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE XML SCHEMA COLLECTION (Transact-SQL)](../../t-sql/statements/create-xml-schema-collection-transact-sql.md)   
 [ALTER XML SCHEMA COLLECTION (Transact-SQL)](../../t-sql/statements/alter-xml-schema-collection-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [Сравнение типизированного и нетипизированного XML](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Требования и ограничения для коллекций схем XML на сервере](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
