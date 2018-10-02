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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 320c11c78f95f644e373b1cd410858a81e72edad
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47804492"
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
  
-   ассоциированной с любым параметром типа **xml** или столбцом;  
  
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
  
## <a name="see-also"></a>См. также:  
 [CREATE XML SCHEMA COLLECTION (Transact-SQL)](../../t-sql/statements/create-xml-schema-collection-transact-sql.md)   
 [ALTER XML SCHEMA COLLECTION (Transact-SQL)](../../t-sql/statements/alter-xml-schema-collection-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [Сравнение типизированного и нетипизированного XML](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Требования и ограничения для коллекций схем XML на сервере](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
