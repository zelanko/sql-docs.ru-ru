---
title: "Создание XML-ИНДЕКСА (Transact-SQL) | Документы Microsoft"
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
f1_keywords:
- XML_TSQL
- CREATE_XML_INDEX_TSQL
- XML INDEX
- CREATE_XML_TSQL
- XML
- CREATE XML
- CREATE XML INDEX
- XML_INDEX_TSQL
- FOR_XML_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE XML INDEX statement
- CREATE INDEX statement
- index creation [SQL Server], XML indexes
- XML indexes [SQL Server], creating
ms.assetid: c510cfbc-68be-4736-b3cc-dc5b7aa51f14
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 133c957937d1c05cd108eeb2deb0847cd7944771
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="create-xml-index-transact-sql"></a>CREATE XML INDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Создает XML-индекс по заданной таблице. Индекс может быть создан до появления данных в таблице. XML-индексы можно создавать на основе таблиц другой базы данных — для этого нужно указать полное имя базы данных.  
  
> [!NOTE]  
>  Для создания реляционного индекса см. [CREATE INDEX &#40; Transact-SQL &#41; ](../../t-sql/statements/create-index-transact-sql.md). Сведения о создании пространственного индекса см. в разделе [CREATE SPATIAL INDEX &#40; Transact-SQL &#41; ](../../t-sql/statements/create-spatial-index-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Create XML Index   
CREATE [ PRIMARY ] XML INDEX index_name   
    ON <object> ( xml_column_name )  
    [ USING XML INDEX xml_index_name   
        [ FOR { VALUE | PATH | PROPERTY } ] ]  
    [ WITH ( <xml_index_option> [ ,...n ] ) ]  
[ ; ]  
  
<object> ::=  
{  
    [ database_name. [ schema_name ] . | schema_name. ]   
    table_name  
}  
  
<xml_index_option> ::=  
{   
    PAD_INDEX  = { ON | OFF }  
  | FILLFACTOR = fillfactor  
  | SORT_IN_TEMPDB = { ON | OFF }  
  | IGNORE_DUP_KEY = OFF  
  | DROP_EXISTING = { ON | OFF }  
  | ONLINE = OFF  
  | ALLOW_ROW_LOCKS = { ON | OFF }  
  | ALLOW_PAGE_LOCKS = { ON | OFF }  
  | MAXDOP = max_degree_of_parallelism  
}  
  
```  
  
## <a name="arguments"></a>Аргументы  
 [PRIMARY] XML  
 Создает XML-индекс в указанном **xml** столбца. Если присутствует ключевое слово PRIMARY, создается кластеризованный индекс с ключом, образованным из ключа кластеризации таблицы пользователя и идентификатора XML-узла. Для каждой таблицы можно создать до 249 XML-индексов. При создании XML-индекса помните следующее.  
  
-   Кластеризованный индекс должен существовать для первичного ключа таблицы пользователя.  
  
-   Максимальное количество столбцов в ключе кластеризации таблицы пользователя — 15.  
  
-   Каждый **xml** столбец в таблице может иметь один первичный XML-индекс и несколько вторичных XML-индексов.  
  
-   Первичный XML-индекс для **xml** столбец должен существовать, чтобы можно было создать вторичный XML-индекс для столбца.  
  
-   XML-индекс может создаваться только на одном **xml** столбца. Не удается создать XML-индекс не в**xml** столбца, а также создайте реляционный индекс на **xml** столбца.  
  
-   Не удается создать XML-индекс, первичный или вторичный, на **xml** столбцу в представлении для возвращающих табличные значения переменной с **xml** столбцы, или **xml** переменных типа.  
  
-   Не удается создать первичный XML-индекс для вычисляемого **xml** столбца.  
  
-   Значения параметров SET должны быть теми же, что и для индексированных представлений и индексов вычисляемых столбцов. В частности, параметр ARITHABORT должен быть присвоено значение ON при создании XML-индекса и при вставке, удалении или обновлении значений в **xml** столбца.  
  
 Дополнительные сведения см в разделе [XML-индексы (SQL Server)](../../relational-databases/xml/xml-indexes-sql-server.md).  
  
 *index_name*  
 Имя индекса. Имена индексов должны быть уникальными в пределах таблицы, но не обязательно должны быть уникальными в пределах базы данных. Имена индексов должны соответствовать правилам [идентификаторы](../../relational-databases/databases/database-identifiers.md).  
  
 Имена первичных XML-индексов не может начинаться со следующих символов:  **#** ,  **##** ,  **@** , или  **@@**  .  
  
 *xml_column_name*  
 — **Xml** столбец, на котором основан индекс. Только один **xml** столбец может быть указан в одном определении XML-индекса; Однако несколько вторичных XML-индексов могут создаваться на **xml** столбца.  
  
 С помощью XML-ИНДЕКСА *xml_index_name*  
 Указывает первичный XML-индекс, который должен использоваться при создании вторичного XML-индекса.  
  
 FOR { VALUE | PATH | PROPERTY }  
 Указывает тип вторичного XML-индекса.  
  
 VALUE  
 Создает вторичный XML-индекс для столбцов, где ключевые столбцы (значение узла и путь) входят в первичный XML-индекс.  
  
 PATH  
 Создает вторичный XML-индекс для столбцов, построенных на основе значений путей и узлов в первичном XML-индексе. Во вторичном индексе типа PATH значениями путей и узлов являются ключевые столбцы, обеспечивающие эффективный поиск путей.  
  
 PROPERTY  
 Создает вторичный XML-индекс по столбцам первичного XML-индекса (PK, путь и узел), где PK — первичный ключ базовой таблицы.  
  
 **\<object>::=**  
  
 Полное или неполное имя индексируемого объекта.  
  
 *database_name*  
 Имя базы данных.  
  
 *schema_name*  
 Имя схемы, которой принадлежит таблица.  
  
 *имя_таблицы*  
 Имя таблицы для индексирования.  
  
 **\<xml_index_option> ::=** 
  
 Указывает параметры, которые должны использоваться при создании индекса.  
  
 PAD_INDEX  **=**  {ON | **OFF** }  
 Определяет разреженность индекса. Значение по умолчанию — OFF.  
  
 ON  
 Процент свободного места, определяемый *fillfactor* применяется к страницам индекса промежуточного уровня.  
  
 ОТКЛЮЧЕНИЕ или *fillfactor* не указан  
 Страницы промежуточного уровня заполняются почти полностью, при этом остается достаточно места по крайней мере для одной строки максимального размера, возможного в этом индексе при заданном наборе ключей на промежуточных страницах.  
  
 Параметр PAD_INDEX имеет смысл только в случае, если указан параметр FILLFACTOR, так как использует процентное значение, указанное в нем. Если процент, заданный аргументом FILLFACTOR, недостаточно велик для размещения одной строки, компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] внутренне переопределит это значение, чтобы обеспечить минимум. Количество строк на странице промежуточного уровня никогда не будет меньше двух независимо от того, каким образом нижнего значения *fillfactor*.  
  
 FILLFACTOR **= *** fillfactor*  
 Определяет величину в процентах, показывающую, насколько компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] должен заполнять конечный уровень каждой страницы индекса во время его создания или перестроения. *значение коэффициента заполнения* должно быть целым числом от 1 до 100. Значение по умолчанию равно 0. Если *fillfactor* равен 100 или 0, [!INCLUDE[ssDE](../../includes/ssde-md.md)] создает индексы с заполненными страницами конечного.  
  
> [!NOTE]  
>  Значения коэффициентов заполнения 0 и 100 идентичны.  
  
 Аргумент FILLFACTOR действует только при создании или перестройке индекса. Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] не сохраняет динамически указанный процентный объем свободного места на страницах. Для просмотра коэффициента заполнения, используйте [sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md) представления каталога.  
  
> [!IMPORTANT]  
>  Создание кластеризованного индекса с аргументом FILLFACTOR меньше 100 влияет на объем пространства хранения, занимаемого данными, т. к. компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] перераспределяет данные, когда создает кластеризованный индекс.  
  
 Дополнительные сведения см. в статье [Указание коэффициента заполнения для индекса](../../relational-databases/indexes/specify-fill-factor-for-an-index.md).  
  
 ПАРАМЕТР SORT_IN_TEMPDB  **=**  {ON | **OFF** }  
 Указывает, следует ли хранить временные результаты сортировки в **tempdb**. Значение по умолчанию — OFF.  
  
 ON  
 Промежуточные результаты сортировки, используемые для построения индекса, хранятся в **tempdb**. Это может уменьшить время, необходимое для создания индекса, если **tempdb** находится на разных наборах дисков пользовательской базы данных. Однако это увеличивает использование места на диске, которое используется при индексировании.  
  
 OFF  
 Промежуточные результаты сортировки хранятся в той же базе данных, где и индекс.  
  
 Кроме места в базе данных пользователя, необходимого для создания индекса **tempdb** должен иметь примерно столько же дополнительного места на диске для хранения промежуточных результатов сортировки. Дополнительные сведения см. в разделе [параметр SORT_IN_TEMPDB для индексов](../../relational-databases/indexes/sort-in-tempdb-option-for-indexes.md).  
  
 IGNORE_DUP_KEY **=OFF**  
 Не влияет на XML-индексы, поскольку этот тип индекса никогда не уникален. Не устанавливайте этот параметр в значение ON, иначе произойдет ошибка.  
  
 DROP_EXISTING  **=**  {ON | **OFF** }  
 Указывает, что именованный существующий XML-индекс удален и перестраивается. Значение по умолчанию — OFF.  
  
 ON  
 Существующий индекс удаляется и перестраивается. Указанное имя индекса должно совпадать с уже существующим индексом, но определение индекса может быть изменено. Например, можно указать другие столбцы, порядок сортировки, схему секционирования или параметры индекса.  
  
 OFF  
 Выдается ошибка, если индекс с указанным именем уже существует.  
  
 Тип индекса не может быть изменен с помощью аргумента DROP_EXISTING. Кроме того, первичный XML-индекс не может быть переопределен как вторичный XML-индекс и наоборот.  
  
 ONLINE **= OFF**  
 Указывает, что базовые таблицы и связанные индексы будут недоступны для запросов и изменения данных во время операций с индексами. В этой версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не разрешено применять построение индекса в сети для XML-индексов. Если этому параметру присвоено значение ON для XML-индекса, то возникает ошибка. Не указывайте параметр ONLINE или установите его в значение OFF.  
  
 Операция вне сети с индексами, в ходе которой создается, перестраивается или удаляется XML-индекс, получает блокировку изменения схемы для таблицы. Это предотвращает доступ к базовой таблице всех пользователей во время операции.  
  
> [!NOTE]  
>  Операции с индексами доступны не во всех выпусках [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сведения о функциях, поддерживаемых различными выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье [Возможности, поддерживаемые различными выпусками SQL Server 2016](../../sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 ALLOW_ROW_LOCKS  **=**  { **ON** | {OFF}  
 Указывает, разрешена ли блокировка строк. Значение по умолчанию — ON.  
  
 ON  
 Блокировки строк допустимы при доступе к индексу. Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] определяет, когда используются блокировки строки.  
  
 OFF  
 Блокировки строк не используются.  
  
 ALLOW_PAGE_LOCKS  **=**  { **ON** | {OFF}  
 Указывает, разрешена ли блокировка страниц. Значение по умолчанию — ON.  
  
 ON  
 Блокировки страниц возможны при доступе к индексу. Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] определяет, когда используются блокировки страниц.  
  
 OFF  
 Блокировки страниц не используются.  
  
 MAXDOP **=***max_degree_of_parallelism*  
 Переопределяет [Настройка параметра max degree of parallelism Server Configuration Option](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md) параметр конфигурации в течение операции с индексами. MAXDOP можно использовать для ограничения числа процессоров, используемых при параллельном выполнении планов. Максимальное число процессоров — 64.  
  
> [!IMPORTANT]  
>  Несмотря на синтаксическую поддержку параметра MAXDOP для всех XML-индексов, инструкция CREATE XML INDEX использует только один процессор для первичного XML-индекса.  
  
 *max_degree_of_parallelism* может быть:  
  
 1  
 Подавляет формирование параллельных планов.  
  
 \>1  
 Ограничивает максимальное количество процессоров, используемых в параллельных операциях с индексами, заданным или меньшим числом в зависимости от текущей рабочей нагрузки системы.  
  
 0 (по умолчанию)  
 В зависимости от текущей рабочей нагрузки системы использует реальное или меньшее число процессоров.  
  
 Дополнительные сведения см. в статье [Настройка параллельных операций с индексами](../../relational-databases/indexes/configure-parallel-index-operations.md).  
  
> [!NOTE]  
>  Параллельные операции с индексами доступны не во всех выпусках [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сведения о функциях, поддерживаемых различными выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье [Возможности, поддерживаемые различными выпусками SQL Server 2016](../../sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
## <a name="remarks"></a>Remarks  
 Вычисляемые столбцы, производные от **xml** данные типы могут быть индексироваться как ключевые или включенные неключевые столбцы при условии, что тип данных вычисляемого столбца является допустимым в качестве ключевого столбца индекса или неключевого столбца. Не удается создать первичный XML-индекс для вычисляемого **xml** столбца.  
  
 Чтобы просмотреть сведения об XML-индексов, используйте [sys.xml_indexes](../../relational-databases/system-catalog-views/sys-xml-indexes-transact-sql.md) представления каталога.  
  
 Дополнительные сведения об XML-индексах см. в разделе [XML-индексы &#40; SQL Server &#41; ](../../relational-databases/xml/xml-indexes-sql-server.md).  
  
## <a name="additional-remarks-on-index-creation"></a>Дополнительные сведения о создании индексов  
 Дополнительные сведения о создании индексов см. в разделе «Примечания» раздела [CREATE INDEX &#40; Transact-SQL &#41; ](../../t-sql/statements/create-index-transact-sql.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-creating-a-primary-xml-index"></a>A. Создание первичного XML-индекса  
 В следующем примере создается первичный XML-индекс по столбцу `CatalogDescription` таблицы `Production.ProductModel`.  
  
```sql  
USE AdventureWorks2012;  
GO  
IF EXISTS (SELECT * FROM sys.indexes  
            WHERE name = N'PXML_ProductModel_CatalogDescription')  
    DROP INDEX PXML_ProductModel_CatalogDescription   
        ON Production.ProductModel;  
GO  
CREATE PRIMARY XML INDEX PXML_ProductModel_CatalogDescription  
    ON Production.ProductModel (CatalogDescription);  
GO  
```  
  
### <a name="b-creating-a-secondary-xml-index"></a>Б. Создание вторичного XML-индекса  
 В следующем примере создается вторичный XML-индекс по столбцу `CatalogDescription` таблицы `Production.ProductModel`.  
  
```sql  
USE AdventureWorks2012;  
GO  
IF EXISTS (SELECT name FROM sys.indexes  
            WHERE name = N'IXML_ProductModel_CatalogDescription_Path')  
    DROP INDEX IXML_ProductModel_CatalogDescription_Path  
        ON Production.ProductModel;  
GO  
CREATE XML INDEX IXML_ProductModel_CatalogDescription_Path   
    ON Production.ProductModel (CatalogDescription)  
    USING XML INDEX PXML_ProductModel_CatalogDescription FOR PATH ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [ALTER INDEX (Transact-SQL)](../../t-sql/statements/alter-index-transact-sql.md)   
 [CREATE INDEX (Transact-SQL)](../../t-sql/statements/create-index-transact-sql.md)   
 [CREATE PARTITION FUNCTION (Transact-SQL)](../../t-sql/statements/create-partition-function-transact-sql.md)   
 [CREATE PARTITION SCHEME (Transact-SQL)](../../t-sql/statements/create-partition-scheme-transact-sql.md)   
 [Создание ПРОСТРАНСТВЕННОГО ИНДЕКСА &#40; Transact-SQL &#41;](../../t-sql/statements/create-spatial-index-transact-sql.md)   
 [CREATE STATISTICS (Transact-SQL)](../../t-sql/statements/create-statistics-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [DBCC SHOW_STATISTICS (Transact-SQL)](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [DROP INDEX &#40; Transact-SQL &#41;](../../t-sql/statements/drop-index-transact-sql.md)   
 [XML-индексы (SQL Server)](../../relational-databases/xml/xml-indexes-sql-server.md)   
 [sys.indexes (Transact-SQL)](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)   
 [sys.xml_indexes &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-xml-indexes-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [XML-индексы &#40; SQL Server и &#41;](../../relational-databases/xml/xml-indexes-sql-server.md)  
  
  

