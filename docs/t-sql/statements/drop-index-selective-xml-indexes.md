---
title: "DROP INDEX (Селективные XML-индексы) | Документы Microsoft"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP XML INDEX statement
dev_langs:
- TSQL
ms.assetid: 4779ae84-e5f4-4d04-8fc1-e24a6631b428
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 23cac56c86855978442dd971d69abe1323423d0b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="drop-index-selective-xml-indexes"></a>DROP INDEX (селективные XML-индексы)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Удаляет существующий выборочный XML-индекс или вторичный выборочный XML-индекс в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [Выборочный XML-индекс (SXI)](../../relational-databases/xml/selective-xml-indexes-sxi.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
DROP INDEX index_name ON <object>  
    [ WITH ( <drop_index_option> [ ,...n ] ) ]  
  
<object> ::=  
{  
    [ database_name. [ schema_name ] . | schema_name. ]   
        table_or_view_name  
}  
  
<drop_index_option> ::=  
{  
    MAXDOP = max_degree_of_parallelism  
    | ONLINE = { ON | OFF }  
}  
```  
  
##  <a name="Arguments"></a> Аргументы  
 *index_name*  
 Имя существующего индекса, который требуется удалить.  
  
 *\<Объект >* таблица, которая содержит индексированный XML-столбец. Используйте один из следующих форматов:  
  
-   `database_name.schema_name.table_name`  
  
-   `database_name..table_name`  
  
-   `schema_name.table_name`  
  
-   `table_name`  
  
 *\<drop_index_option >* сведения о параметрах удаления индекса см. в разделе [DROP INDEX &#40; Transact-SQL &#41; ](../../t-sql/statements/drop-index-transact-sql.md).  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Permissions  
 Для использования DROP INDEX требуется разрешение ALTER для таблицы или представления. По умолчанию это разрешение предоставляется предопределенной роли сервера sysadmin и предопределенным ролям базы данных db_ddladmin и db_owner.  
  
## <a name="example"></a>Пример  
 В следующем примере показана инструкция DROP INDEX.  
  
```  
DROP INDEX sxi_index ON tbl;  
```  
  
## <a name="see-also"></a>См. также:  
 [Выборочный XML-индекс (SXI)](../../relational-databases/xml/selective-xml-indexes-sxi.md)   
 [Создание, изменение и удаление селективных XML-индексов](../../relational-databases/xml/create-alter-and-drop-selective-xml-indexes.md)  
  
  


