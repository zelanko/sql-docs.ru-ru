---
title: "Создание СЕЛЕКТИВНОГО XML-ИНДЕКСА (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 1d769f62-f646-4057-b93a-bf5f90e935ed
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 29a2a6eaec3ebbbafef0fcead331835921c7da44
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="create-selective-xml-index-transact-sql"></a>CREATE SELECTIVE XML INDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Создает новый селективный XML-индекс для указанной таблицы и XML-столбца. Селективные XML-индексы повышают производительность индексирования и выполнения XML-запросов, индексируя только подмножества узлов, к которым обычно выполняются запросы. Кроме того, вы можете создавать вторичные селективные XML-индексы. Сведения см. в разделе [Create, Alter и Drop вторичного селективного XML-индексы](../../relational-databases/xml/create-alter-and-drop-secondary-selective-xml-indexes.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
CREATE SELECTIVE XML INDEX index_name  
    ON <table_object> (xml_column_name)  
    [WITH XMLNAMESPACES (<xmlnamespace_list>)]  
    FOR (<promoted_node_path_list>)  
    [WITH (<index_options>)]  
  
<table_object> ::=  
 { [database_name. [schema_name ] . | schema_name. ] table_name }  
  
<promoted_node_path_list> ::=   
<named_promoted_node_path_item> [, <promoted_node_path_list>]  
  
<named_promoted_node_path_item> ::=   
<path_name> = <promoted_node_path_item>  
  
<promoted_node_path_item>::=  
<xquery_node_path_item> | <sql_values_node_path_item>  
  
<xquery_node_path_item> ::=   
<node_path> [AS XQUERY <xsd_type_or_node_hint>] [SINGLETON]  
  
<xsd_type_or_node_hint> ::=   
[<xsd_type>] [MAXLENGTH(x)] | node()  
  
<sql_values_node_path_item> ::=  
<node_path> AS SQL <sql_type> [SINGLETON]  
  
<node_path> ::=   
character_string_literal  
  
<xsd_type> ::=   
character_string_literal  
  
<sql_type> ::=   
identifier  
  
<path_name> ::=   
identifier  
  
<xmlnamespace_list> ::=   
<xmlnamespace_item> [, <xmlnamespace_list>]  
  
<xmlnamespace_item> ::=   
<xmlnamespace_uri> AS <xmlnamespace_prefix>  
  
<xml_namespace_uri> ::=   
character_string_literal  
  
<xml_namespace_prefix> ::=   
identifier  
  
<index_options> ::=   
(   
  | PAD_INDEX  = { ON | OFF }  
  | FILLFACTOR = fillfactor  
  | SORT_IN_TEMPDB = { ON | OFF }  
  | IGNORE_DUP_KEY = OFF  
  | DROP_EXISTING = { ON | OFF }  
  | ONLINE = OFF  
  | ALLOW_ROW_LOCKS = { ON | OFF }  
  | ALLOW_PAGE_LOCKS = { ON | OFF }  
  | MAXDOP = max_degree_of_parallelism  
)  
```  
  
##  <a name="Arguments"></a> Аргументы  
 *index_name*  
 Имя создаваемого нового индекса. Имена индексов должны быть уникальными в пределах таблицы, но не обязательно должны быть уникальными в пределах базы данных. Имена индексов должны соответствовать правилам [идентификаторы](../../relational-databases/databases/database-identifiers.md).  
  
 *\<table_object >* таблица, которая содержит XML-столбец для индекса. Используйте один из следующих форматов:  
  
-   `database_name.schema_name.table_name`  
  
-   `database_name..table_name`  
  
-   `schema_name.table_name`  
  
-   `table_name`  
  
 *xml_column_name*  
 Имя XML-столбца, содержащего индексируемые пути.  
  
 [WITH XMLNAMESPACES **(**\<xmlnamespace_list >**)**] — список пространств имен, используемых пути для индексирования. Сведения о синтаксисе предложения WITH XMLNAMESPACES см. в разделе [WITH XMLNAMESPACES &#40; Transact-SQL &#41; ](../../t-sql/xml/with-xmlnamespaces.md).  
  
 ДЛЯ **(**\<promoted_node_path_list >**)** список пути для индексирования с указаниями по оптимизации. Сведения о пути и указания по оптимизации, которые можно указать в инструкции CREATE или ALTER см. в разделе [укажите путь и указания по оптимизации для селективного XML-индексов](../../relational-databases/xml/specify-paths-and-optimization-hints-for-selective-xml-indexes.md).  
  
 С  *\<index_options >* сведения о параметрах индекса см. в разделе [CREATE XML INDEX &#40; Выборочные XML-индексы &#41; ](../../t-sql/statements/create-xml-index-selective-xml-indexes.md).  
  
## <a name="best-practices"></a>Рекомендации  
 Создание селективного XML-индекса вместо обычного XML-индекса в большинстве случаев приводит к повышению производительности и более эффективному использованию хранилища. Однако селективный XML-индекс не рекомендуется использовать при наличии следующих условий.  
  
-   Необходимо сопоставить большое количество путей узлов.  
  
-   Необходимо поддерживать запросы на неизвестные элементы или элементы в неизвестных расположениях.  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
 Сведения об ограничениях см. в разделе [выборочные XML-индексы &#40; SXI &#41; ](../../relational-databases/xml/selective-xml-indexes-sxi.md).  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Разрешения  
 Необходимо разрешение ALTER для таблицы или представления. Пользователь должен быть членом предопределенной роли сервера **sysadmin** или предопределенных ролей базы данных **db_ddladmin** и **db_owner** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере показан синтаксис для создания селективного XML-индекса. Он также содержит несколько вариантов синтаксиса для описания индексируемых путей с указаниями по оптимизации.  
  
```  
CREATE TABLE Tbl ( id INT PRIMARY KEY, xmlcol XML );  
GO  
CREATE SELECTIVE XML INDEX sxi_index  
ON Tbl(xmlcol)  
FOR(  
    pathab   = '/a/b' as XQUERY 'node()',  
    pathabc  = '/a/b/c' as XQUERY 'xs:double',   
    pathdtext = '/a/b/d/text()' as XQUERY 'xs:string' MAXLENGTH(200) SINGLETON,  
    pathabe = '/a/b/e' as SQL NVARCHAR(100)  
);  
```  
  
 В следующем примере содержится предложение WITH XMLNAMESPACES.  
  
```  
CREATE SELECTIVE XML INDEX on T1(C1)  
WITH XMLNAMESPACES ('http://www.tempuri.org/' as myns)  
FOR ( path1 = '/myns:book/myns:author/text()' );  
```  
  
## <a name="see-also"></a>См. также:  
 [Выборочный XML-индекс (SXI)](../../relational-databases/xml/selective-xml-indexes-sxi.md)   
 [Создание, изменение и удаление селективного XML-индексов](../../relational-databases/xml/create-alter-and-drop-selective-xml-indexes.md)   
 [Задание путей и указания по оптимизации для селективных XML-индексов](../../relational-databases/xml/specify-paths-and-optimization-hints-for-selective-xml-indexes.md)  
  
  


