---
title: "Удаление КОЛЛЕКЦИИ XML-СХЕМ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 11/25/2015
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 01ee022bf8d9cb03b6f3fb47451c969955b5c255
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
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
 Имя удаляемой коллекции XML-схем.  
  
## <a name="remarks"></a>Remarks  
 Удаление коллекции XML-схем является транзакционной операцией. Это значит, что если удалить коллекцию XML-схем внутри транзакции, а потом сделать откат, коллекция XML-схем не будет удалена.  
  
 Нельзя удалить коллекцию XML-схем, если она используется. Это означает, что удаляемая коллекция не может быть:  
  
-   Связанные с любым **xml** типа параметра или столбца.  
  
-   указанной в ограничениях любой из таблиц;  
  
-   той, на которую ссылается привязанная к схеме функция или хранимая процедура. Например, следующая функция заблокирует коллекцию XML-схем `MyCollection`, так как функция включает `WITH SCHEMABINDING`. Если удалить ее, блокировки на XML SCHEMA COLLECTION не будет.  
  
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
  
## <a name="see-also"></a>См. также  
 [Создание КОЛЛЕКЦИИ XML-СХЕМ &#40; Transact-SQL &#41;](../../t-sql/statements/create-xml-schema-collection-transact-sql.md)   
 [ALTER XML SCHEMA COLLECTION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-xml-schema-collection-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [Сравнение типизированного и нетипизированного XML](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Требования и ограничения для коллекций XML-схем на сервере](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
