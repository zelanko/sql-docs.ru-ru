---
title: "column_definition (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 05/05/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- column_definition
- column_definition_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- column_definition
- ALTER TABLE statement
- column properties [SQL Server]
- column definitions [SQL Server]
ms.assetid: a1742649-ca29-4d9b-9975-661cdbf18f78
caps.latest.revision: 78
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5c63dcea3473198ded46ebf84053fa9d8b36330f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="alter-table-columndefinition-transact-sql"></a>Column_definition ALTER TABLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Определяет свойства столбца, которые добавляются в таблицу с помощью [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
column_name <data_type>  
[ FILESTREAM ]  
[ COLLATE collation_name ]   
[ NULL | NOT NULL ]  
[   
    [ CONSTRAINT constraint_name ] DEFAULT constant_expression [ WITH VALUES ]   
    | IDENTITY [ ( seed , increment ) ] [ NOT FOR REPLICATION ]   
]  
[ ROWGUIDCOL ]   
[ SPARSE ]   
[ ENCRYPTED WITH  
  ( COLUMN_ENCRYPTION_KEY = key_name ,  
      ENCRYPTION_TYPE = { DETERMINISTIC | RANDOMIZED } ,   
      ALGORITHM =  'AEAD_AES_256_CBC_HMAC_SHA_256'   
  ) ]  
[ MASKED WITH ( FUNCTION = ' mask_function ') ]  
[ <column_constraint> [ ...n ] ]  
  
<data type> ::=   
[ type_schema_name . ] type_name   
    [ ( precision [ , scale ] | max |   
        [ { CONTENT | DOCUMENT } ] xml_schema_collection ) ]   
  
<column_constraint> ::=   
[ CONSTRAINT constraint_name ]   
{     { PRIMARY KEY | UNIQUE }   
        [ CLUSTERED | NONCLUSTERED ]   
        [   
            WITH FILLFACTOR = fillfactor    
          | WITH ( < index_option > [ , ...n ] )   
        ]   
        [ ON { partition_scheme_name ( partition_column_name )   
            | filegroup | "default" } ]  
  | [ FOREIGN KEY ]   
        REFERENCES [ schema_name . ] referenced_table_name [ ( ref_column ) ]   
        [ ON DELETE { NO ACTION | CASCADE | SET NULL | SET DEFAULT } ]   
        [ ON UPDATE { NO ACTION | CASCADE | SET NULL | SET DEFAULT } ]   
        [ NOT FOR REPLICATION ]   
  | CHECK [ NOT FOR REPLICATION ] ( logical_expression )   
}  
```  
  
## <a name="arguments"></a>Аргументы  
 *column_name*  
 Имя столбца, который требуется изменить, добавить или удалить. *column_name* может содержать от 1 до 128 символов. Для новых столбцов, созданных с типом данных timestamp *column_name* можно опустить. Если не *column_name* указан для **timestamp** столбец типа данных, имя **timestamp** используется.  
  
 [ *type_schema_name***.** ] *type_name*  
 Тип данных добавленного столбца и схема, которой он принадлежит.  
  
 *Функция TYPE_NAME* может быть:  
  
-   Объект [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] системный тип данных.  
  
-   Псевдонимом типа данных, основанным на системном типе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Псевдонимы типов данных должны быть созданы с помощью инструкции CREATE TYPE прежде, чем их можно будет использовать в определении таблицы;  
  
-   Объект [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] определяемого пользователем типа и схему, к которой он принадлежит. Определяемые пользователем типы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] должны быть созданы с помощью инструкции CREATE TYPE прежде, чем их можно будет использовать в определении таблицы.  
  
 Если *type_schema_name* не указан, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] ссылки *type_name* в следующем порядке:  
  
-   системный тип данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)];  
  
-   в установленной по умолчанию для текущего пользователя схеме в текущей базе данных;  
  
-   Схема **dbo** в текущей базе данных.  
  
*precision*  
 Точность указанного типа данных. Дополнительные сведения о допустимых значениях точности см. в разделе [точность, масштаб и длина &#40; Transact-SQL &#41; ](../../t-sql/data-types/precision-scale-and-length-transact-sql.md).  
  
*масштаб*  
 Масштаб указанного типа данных. Дополнительные сведения о допустимых значениях масштаба см. в разделе [точность, масштаб и длина &#40; Transact-SQL &#41; ](../../t-sql/data-types/precision-scale-and-length-transact-sql.md).  
  
**max**  
 Применяется только к **varchar**, **nvarchar**, и **varbinary** типов данных. Они используются для хранения 2^31 байт символов или двоичных данных, либо 2^30 байт данных в формате Юникод.  
  
**СОДЕРЖИМОЕ**  
 Указывает, что каждый экземпляр **xml** в тип данных *column_name* может включать в себя несколько элементов верхнего уровня. CONTENT применим только к **xml** данных типа и может быть указан только в том случае, если *xml_schema_collection* также указан. Если он не задан, то CONTENT имеет обычный смысл, заданный по умолчанию.  
  
DOCUMENT  
 Указывает, что каждый экземпляр **xml** в тип данных *column_name* может содержать только один элемент верхнего уровня. DOCUMENT применим только к **xml** данных типа и может быть указан только в том случае, если *xml_schema_collection* также указан.  
  
 *xml_schema_collection*  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Применяется только к **xml** тип данных для сопоставления с типом коллекции XML-схем. Перед вводом **xml** столбца в схеме схемы сначала должна быть создана в базе данных с помощью [CREATE XML SCHEMA COLLECTION](../../t-sql/statements/create-xml-schema-collection-transact-sql.md).  
  
FILESTREAM  
 При необходимости указывает атрибут хранилища FILESTREAM для столбца, имеющего *type_name* из **varbinary(max)**.  
  
 Когда указан атрибут FILESTREAM для столбца, она должна содержать столбец **uniqueidentifier** типом данных с атрибутом ROWGUIDCOL. Этот столбец не должен допускать значений NULL и должен иметь относящееся к одному столбцу ограничение UNIQUE или PRIMARY KEY. Значение идентификатора GUID для столбца должно быть предоставлено приложением во время вставки данных или ограничением DEFAULT, в котором используется функция NEWID ().  
  
 Столбец ROWGUIDCOL нельзя удалить, а связанные ограничения нельзя изменить, если в таблице определен столбец FILESTREAM. Столбец ROWGUIDCOL можно удалить только после удаления последнего столбца FILESTREAM.  
  
 Если для столбца задан атрибут хранилища FILESTREAM, то все значения для этого столбца хранятся в контейнере данных FILESTREAM в файловой системе.  
  
 Пример, демонстрирующий способы использования определения столбца см. в разделе [FILESTREAM &#40; SQL Server &#41; ](../../relational-databases/blob/filestream-sql-server.md).  
  
COLLATE *collation_name*  
 Задает параметры сортировки для столбца. Если не указано, столбцу назначаются параметры сортировки, принятые в базе данных по умолчанию. Могут использоваться параметры сортировки Windows или параметры сортировки SQL. Список и Дополнительные сведения см. в разделе [имя параметров сортировки Windows &#40; Transact-SQL &#41; ](../../t-sql/statements/windows-collation-name-transact-sql.md) и [SQL Server Collation Name &#40; Transact-SQL &#41; ](../../t-sql/statements/sql-server-collation-name-transact-sql.md).  
  
 Предложение COLLATE можно использовать для изменения параметров сортировки только для столбцов **char**, **varchar**, **nchar**, и **nvarchar** типы данных .  
  
 Дополнительные сведения о предложении COLLATE см. в разделе [COLLATE &#40; Transact-SQL &#41; ](~/t-sql/statements/collations.md).  
  
 NULL | NOT NULL  
 Определяет, допустимы ли для столбца значения NULL. Параметр NULL не является ограничением в строгом смысле слова, но может быть указан так же, как и NOT NULL.  
  
[Ограничения *constraint_name* ]  
 Указывает начало определения значения DEFAULT. Для сохранения совместимости с более ранними версиями сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] значению DEFAULT может быть присвоено имя ограничения. *constraint_name* должны соответствовать правилам для [идентификаторы](../../relational-databases/databases/database-identifiers.md), за исключением того, что имя не может начинаться со знака номера (#). Если *constraint_name* не указан, определение DEFAULT назначается автоматически сформированное имя.  
  
DEFAULT  
 Ключевое слово, задающее значение по умолчанию для столбца. Определения DEFAULT могут использоваться для указания значений по умолчанию для новых столбцов в существующих строках данных. Определения DEFAULT не может применяться к **timestamp** столбцов или столбцов со свойством IDENTITY. Если указано значение по умолчанию для столбца определяемого пользователем типа, тип должен поддерживать неявное преобразование из *constant_expression* для определяемого пользователем типа.  
  
*constant_expression*  
 Символьное значение, NULL или системная функция, используемая в качестве значения столбца по умолчанию. Если используется в сочетании со столбцом определяемого [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] определяемого пользователем типа реализация типа должна поддерживать неявное преобразование из *constant_expression* для определяемого пользователем типа.  
  
WITH VALUES  
 Указывает, что значение, заданное по умолчанию *constant_expression* сохраняется в новом столбце, добавляемом к существующим строкам. Если добавленный столбец допускает значения NULL и указано предложение WITH VALUES, новый столбец, добавленный к существующим строкам, заполняется значением по умолчанию. Если предложение WITH VALUES не указано для столбцов, допускающих значение NULL, новый столбец для существующих строк заполняется значением NULL. Если новый столбец не допускает значения NULL, значение по умолчанию сохраняется во всех строках независимо от того, указан оператор WITH VALUES или нет.  
  
IDENTITY  
 Указывает, что новый столбец является столбцом идентификаторов. Компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] присваивает столбцу уникальное возрастающее значение. Когда добавляются столбцы идентификаторов к существующим таблицам, к существующим строкам таблицы добавляются номера идентификаторов с этим начальным значением и приращением. Порядок, в котором выполняется обновление строк, не гарантирован. Номера идентификаторов также формируются для всех новых строк, которые добавляются.  
  
 Столбцы идентификаторов наиболее часто используются в сочетании с ограничениями PRIMARY KEY для выполнения функции уникального идентификатора строки таблицы. Свойство IDENTITY может назначаться **tinyint**, **smallint**, **int**, **bigint**, **decimal(p,0)**, или **numeric(p,0)** столбца. Для каждой таблицы можно создать только один столбец идентификаторов. Ключевое слово DEFAULT и значения по умолчанию не могут применяться к столбцам идентификаторов. Начальное значение и шаг приращения для столбца идентификаторов должны быть либо заданы вместе, либо не заданы вообще. Если ничего не указано, применяется значение по умолчанию (1,1).  
  
> [!NOTE]  
>  Нельзя изменить существующий столбец таблицы, добавив в него свойство IDENTITY.  
  
 Не поддерживается добавление столбца идентификаторов к опубликованной таблице, так как это может привести к расхождению данных при репликации столбца на подписчик. Значения в столбце идентификаторов на издателе зависят от порядка, в котором строки изменяемой таблицы хранятся физически. Строки могут быть сохранены на подписчике иначе; следовательно, значение в столбце идентификаторов может отличаться для одних и тех же строк.  
  
 Чтобы отключить свойство IDENTITY столбца, позволяя явно вставляемые значения, используйте [SET IDENTITY_INSERT](../../t-sql/statements/set-identity-insert-transact-sql.md).  
  
*Начальное значение*  
 Значение, используемое для первой строки, загружаемой в таблицу.  
  
*приращение*  
 Значение приращения, добавляемое к значению столбца предыдущей строки для получения значения столбца новой строки.  
  
NOT FOR REPLICATION  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Может быть задано для свойства IDENTITY. Если это предложение задано для свойства IDENTITY, то значения в столбцах идентификаторов не увеличиваются при выполнении агентами репликации операций по вставке строк.  
  
ROWGUIDCOL  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Показывает, что столбец является столбцом глобального уникального идентификатора строки. Свойство ROWGUIDCOL может быть только **uniqueidentifier** столбца и только один **uniqueidentifier** столбца в каждой таблице можно определить как столбец ROWGUIDCOL. ROWGUIDCOL не может быть назначен столбцам с типами, определенными пользователем.  
  
 Свойство ROWGUIDCOL не обеспечивает уникальности значений, хранимых в столбце. Кроме того, оно не производит автоматического формирования значений для новых строк, вставляемых в таблицу. Для формирования уникальных значений для каждого столбца можно использовать функцию NEWID в инструкциях INSERT или определить функцию NEWID как значение по умолчанию для столбца. Дополнительные сведения см. в разделе [NEWID &#40; Transact-SQL &#41; ](../../t-sql/functions/newid-transact-sql.md)и [Вставить &#40; Transact-SQL &#41; ](../../t-sql/statements/insert-transact-sql.md).  
  
SPARSE  
 Указывает, что столбец является разреженным столбцом. Хранилище разреженных столбцов оптимизируется для значений NULL. Для разреженных столбцов нельзя указать параметр NOT NULL. Дополнительные ограничения и Дополнительные сведения о разреженных столбцах см. в разделе [Использование разреженных столбцов](../../relational-databases/tables/use-sparse-columns.md).  
  
\<column_constraint >  
 Определения аргументов ограничения столбцов см. в разделе [column_constraint &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-table-column-constraint-transact-sql.md).  
  
 ЗАШИФРОВАН  
 Указывает столбцы, шифрования с помощью [постоянного шифрования](../../relational-databases/security/encryption/always-encrypted-database-engine.md) компонентов.  
  
 COLUMN_ENCRYPTION_KEY = *key_name*  
 Указывает ключ шифрования столбца. Дополнительные сведения см. в разделе [CREATE COLUMN ENCRYPTION KEY &#40; Transact-SQL &#41; ](../../t-sql/statements/create-column-encryption-key-transact-sql.md).  
  
ENCRYPTION_TYPE = {ДЕТЕРМИНИРОВАННЫМ | СЛУЧАЙНОЕ ШИФРОВАНИЕ;}  
 **Детерминированное шифрование** использует метод, который всегда создает одно и то же зашифрованное значение для любого текстового значения. С помощью детерминированного шифрования позволяет выполнять поиск с помощью сравнения равенства, группирование и соединение таблиц с помощью соединения равенства, на основе зашифрованных значений, при этом также несанкционированные пользователи могут определять некоторую информацию о зашифрованных значениях путем анализа закономерностей в зашифрованный столбец. Соединение двух таблиц для столбцов, зашифрованных детерминированного возможна, только если оба столбца шифруются с помощью того же ключа шифрования столбца. При использовании детерминированного шифрования необходимо указать порядок сортировки binary2 в параметрах сортировки для символьных столбцов.  
  
 **Случайное шифрование** использует метод, который шифрует данные менее предсказуемым образом. Случайное шифрование более безопасна, но не позволяет выполнять поиск равенства, группирование и объединение по зашифрованным столбцам. Столбцы с помощью случайного шифрования, невозможно проиндексировать.  
  
 Детерминированное шифрование используется для столбцов, которые будут являться параметров поиска или группирования параметров, например ИНН. Используйте случайное шифрование, для данных, например номер кредитной карты, который не сгруппированы с другими записями, и используется для соединения таблиц и которого не осуществляется поиск, так как другие столбцы (такие как номер транзакции) используется для поиска строки, которая содержит зашифрованный столбец, представляющие интерес.  
  
 Столбцы должны иметь подходящий тип данных.  
  
АЛГОРИТМ  
**Применяется к**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
Должно быть **«AEAD_AES_256_CBC_HMAC_SHA_256»**.  
  
 Дополнительные сведения, включая возможность ограничения см. в разделе [постоянного шифрования &#40; компонент Database Engine &#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md).  
  
   
Добавить СКРЫТЫЙ с (ФУНКЦИЯ = " *mask_function* ")  
 **Применяется к**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  
  
 Задает маску динамических данных. *mask_function* имя функция маскирования с соответствующими параметрами. Доступны следующие функции:  
  
-   Default()  
  
-   Email()  
  
-   partial()  
  
-   Random()  
  
 Параметры функции. в разделе [динамической маскировки данных](../../relational-databases/security/dynamic-data-masking.md).  
  
## <a name="remarks"></a>Замечания  
 Если добавлен столбец, имеющий **uniqueidentifier** тип данных, оно может быть определено значение по умолчанию, который использует функцию NEWID() для предоставления значений уникального идентификатора в новом столбце для каждой существующей строки в таблице.  
  
 Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] не ограничивает порядок задания свойств DEFAULT, IDENTITY, ROWGUIDCOL или ограничений столбца в определении столбца.  
  
 Инструкция ALTER TABLE будет завершена с ошибками, если при добавлении столбца размер строки данных превысит 8060 байт.  
  
## <a name="examples"></a>Примеры  
 Примеры см. в разделе [ALTER TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-table-transact-sql.md).  
  
## <a name="see-also"></a>См. также:  
 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)  
  

