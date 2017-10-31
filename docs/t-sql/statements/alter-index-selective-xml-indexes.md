---
title: "Инструкция ALTER INDEX (Селективные XML-индексы) | Документы Microsoft"
ms.custom: 
ms.date: 05/01/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: cca96a8f-7737-42d2-bbcc-03d5f858dcc1
caps.latest.revision: 13
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e7854dd1d9365f97628341c4160c368f97308302
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="alter-index-selective-xml-indexes"></a>ALTER INDEX (селективные XML-индексы)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Изменяет существующий селективный XML-индекс. Инструкция ALTER INDEX изменяет один или несколько из следующих элементов:  
  
-   Список индексированных путей (предложение FOR).  
  
-   Список пространств имен (предложение WITH XMLNAMESPACES).  
  
-   Параметры индекса (предложение WITH).  
  
 Нельзя изменить вторичные селективные XML-индексы. Дополнительные сведения см. в разделе [Create, Alter и Drop вторичного селективного XML-индексы](../../relational-databases/xml/create-alter-and-drop-secondary-selective-xml-indexes.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
ALTER INDEX index_name  
    ON <table_object>   
    [WITH XMLNAMESPACES ( <xmlnamespace_list> )]  
    FOR ( <promoted_node_path_action_list> )  
    [WITH ( <index_options> )]  
  
<table_object> ::=   
{ [database_name. [schema_name ] . | schema_name. ] table_name }  
<promoted_node_path_action_list> ::=   
<promoted_node_path_action_item> [, <promoted_node_path_action_list>]  
  
<promoted_node_path_action_item>::=   
<add_node_path_item_action> | <remove_node_path_item_action>  
  
<add_node_path_item_action> ::=  
ADD <path_name> = <promoted_node_path_item>  
  
<promoted_node_path_item>::=  
<xquery_node_path_item> | <sql_values_node_path_item>  
  
<remove_node_path_item_action> ::= REMOVE <path_name>   
  
<path_name_or_typed_node_path>::=   
<path_name> | <typed_node_path>  
  
<typed_node_path> ::=   
<node_path> [[AS XQUERY <xsd_type_ext>] | [AS SQL <sql_type>]]  
  
<xquery_node_path_item> ::=   
<node_path> [AS XQUERY <xsd_type_or_node_hint>] [SINGLETON]  
  
<xsd_type_or_node_hint> ::=   
[<xsd_type>] [MAXLENGTH(x)] | 'node()'  
  
<sql_values_node_path_item> ::=   
<node_path> AS SQL <sql_type> [SINGLETON]  
  
<node_path> ::=   
character_string_literal  
  
<xsd_type_ext> ::=   
character_string_literal  
  
<sql_type> ::=   
identifier  
  
<path_name> ::=   
identifier  
  
<xmlnamespace_list> ::=   
<xmlnamespace_item> [, <xmlnamespace_list>]  
  
<xmlnamespace_item> ::=   
<xmlnamespace_uri> AS <xmlnamespace_prefix>  
  
<xml_namespace_uri> ::= character_string_literal  
<xml_namespace_prefix> ::= identifier  
  
<index_options> ::=   
(   
  | PAD_INDEX  = { ON | OFF }  
  | FILLFACTOR = fillfactor  
  | SORT_IN_TEMPDB = { ON | OFF }  
  | IGNORE_DUP_KEY =OFF  
  | DROP_EXISTING = { ON | OFF }  
  | ONLINE =OFF  
  | ALLOW_ROW_LOCKS = { ON | OFF }  
  | ALLOW_PAGE_LOCKS = { ON | OFF }  
  | MAXDOP = max_degree_of_parallelism  
)  
```  
  
##  <a name="Arguments"></a> Аргументы  
 *index_name*  
 Имя существующего индекса, который требуется изменить.  
  
 *\<table_object >*  
 Таблица, которая содержит индексируемый XML-столбец. Используйте один из следующих форматов:  
  
-   `database_name.schema_name.table_name`  
  
-   `database_name..table_name`  
  
-   `schema_name.table_name`  
  
-   `table_name`  
  
 [WITH XMLNAMESPACES **(** \<xmlnamespace_list > **)**]  
 Список пространств имен, используемых индексируемыми путями. Сведения о синтаксисе предложения WITH XMLNAMESPACES см. в разделе [WITH XMLNAMESPACES &#40; Transact-SQL &#41; ](../../t-sql/xml/with-xmlnamespaces.md).  
  
 ДЛЯ **(** \<promoted_node_path_action_list > **)**  
 Список индексированных путей, который необходимо добавить или удалить.  
  
-   **ДОБАВЬТЕ путь.** Кода вы добавляете путь через ADD, вы используете такой же синтаксис, который использовался для создания путей посредством выражения CREATE SELECTIVE XML INDEX. Сведения о путях, указанных в инструкции CREATE или ALTER см. в разделе [укажите путь и указания по оптимизации для селективного XML-индексов](../../relational-databases/xml/specify-paths-and-optimization-hints-for-selective-xml-indexes.md).  
  
-   **Удаление контура.** Когда вы удаляете путь через REMOVE, вы предоставляете имя, которое было дано пути при его создании.  
  
 [С **(** \<index_options > **)**]  
 Можно указать только \<index_options > при использовании инструкции ALTER INDEX без предложения FOR. Если для добавления или удаления пути в индексе используется ALTER INDEX, то параметры индекса являются недопустимыми аргументами. Сведения о параметрах индекса см. в разделе [CREATE XML INDEX &#40; Выборочные XML-индексы &#41; ](../../t-sql/statements/create-xml-index-selective-xml-indexes.md).  
  
## <a name="remarks"></a>Замечания  
  
> [!IMPORTANT]  
>  При выполнении инструкции ALTER INDEX селективный XML-индекс всегда перестраивается. Необходимо учитывать влияние этого процесса на ресурсы сервера.  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Permissions  
 Для использования ALTER INDEX требуется разрешение ALTER для таблицы или представления.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показана инструкция ALTER INDEX. Эта инструкция добавляет путь `'/a/b/m'` в часть XQuery индекса и удаляет путь `'/a/b/e'` из части SQL индекса, созданного в примере в разделе [CREATE SELECTIVE XML INDEX (Transact-SQL)](../../t-sql/statements/create-selective-xml-index-transact-sql.md). Путь для удаления определяется по имени, указанному при его создании.  
  
```tsql  
ALTER INDEX sxi_index  
ON Tbl  
FOR   
(  
    ADD pathm = '/a/b/m' as XQUERY 'node()' ,  
    REMOVE pathabe  
);  
```  
  
 В следующем примере показана инструкция ALTER INDEX с параметром индекса. Параметры индекса недопустимы, так как инструкция не использует предложение FOR для добавления или удаления пути.  
  
```tsql  
ALTER INDEX sxi_index  
ON Tbl  
PAD_INDEX = ON;  
```  
  
## <a name="see-also"></a>См. также:  
 [Выборочный XML-индекс (SXI)](../../relational-databases/xml/selective-xml-indexes-sxi.md)   
 [Создание, изменение и удаление селективного XML-индексов](../../relational-databases/xml/create-alter-and-drop-selective-xml-indexes.md)   
 [Задание путей и указания по оптимизации для селективных XML-индексов](../../relational-databases/xml/specify-paths-and-optimization-hints-for-selective-xml-indexes.md)  
  
  

