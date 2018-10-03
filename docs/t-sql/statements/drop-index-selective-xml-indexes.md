---
title: DROP INDEX (селективные XML-индексы) | Документы Майкрософт
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP XML INDEX statement
dev_langs:
- TSQL
ms.assetid: 4779ae84-e5f4-4d04-8fc1-e24a6631b428
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: db937bd1a5ce723e071acb5077059235a9261193
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47739460"
---
# <a name="drop-index-selective-xml-indexes"></a>DROP INDEX (селективные XML-индексы)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

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
  
 *\< object>* Таблица, которая содержит индексированный XML-столбец. Используйте один из следующих форматов:  
  
-   `database_name.schema_name.table_name`  
  
-   `database_name..table_name`  
  
-   `schema_name.table_name`  
  
-   `table_name`  
  
 *\<drop_index_option>* Сведения о параметрах удаления индекса см. в разделе [DROP INDEX (Transact-SQL)](../../t-sql/statements/drop-index-transact-sql.md).  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Разрешения  
 Для использования DROP INDEX требуется разрешение ALTER для таблицы или представления. По умолчанию это разрешение предоставляется предопределенной роли сервера sysadmin и предопределенным ролям базы данных db_ddladmin и db_owner.  
  
## <a name="example"></a>Пример  
 В следующем примере показана инструкция DROP INDEX.  
  
```  
DROP INDEX sxi_index ON tbl;  
```  
  
## <a name="see-also"></a>См. также:  
 [Выборочный XML-индекс (SXI)](../../relational-databases/xml/selective-xml-indexes-sxi.md)   
 [Создание, изменение и удаление селективных XML-индексов](../../relational-databases/xml/create-alter-and-drop-selective-xml-indexes.md)  
  
  

