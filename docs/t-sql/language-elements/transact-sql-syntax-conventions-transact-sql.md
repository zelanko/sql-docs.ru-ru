---
title: Синтаксические обозначения в Transact-SQL (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/09/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- sql13.TSQLExpandPortal.f1
dev_langs:
- TSQL
helpviewer_keywords:
- conventions [SQL Server]
- Applies to section in Transact-SQL topics
- code example conventions [SQL Server]
- objects [SQL Server], names
- code [SQL Server], conventions
- multipart names [SQL Server]
- Transact-SQL syntax conventions
- syntax conventions [SQL Server]
- code [SQL Server]
- Transact-SQL
- naming conventions [SQL Server]
- syntax [SQL Server], Transact-SQL
ms.assetid: 35fbcf7f-8b55-46cd-a957-9b8c7b311241
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: edc4bd43b27235a35b6c8ed213e2925523015fde
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65981454"
---
# <a name="transact-sql-syntax-conventions-transact-sql"></a>Синтаксические обозначения в Transact-SQL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

В следующей таблице перечислены и описаны соглашения, которые используются в синтаксисе в справочнике по [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
|Обозначение|Используется для|  
|----------------|--------------|  
|ВЕРХНИЙ РЕГИСТР|Ключевые слова [!INCLUDE[tsql](../../includes/tsql-md.md)].|  
|_курсив_|Пользовательские параметры синтаксиса [!INCLUDE[tsql](../../includes/tsql-md.md)].|  
|**полужирный**|Имена баз данных типов, таблиц, столбцов, индексов, хранимых процедур, программ, типов данных и текст должны вводиться в точном соответствии с примером.|  
|подчеркнутый|Указывает значение по умолчанию, которое применяется, когда в инструкции пропущено предложение, содержащее подчеркнутое значение.|  
|&#124; (вертикальная черта)|Разделяет элементы синтаксиса внутри квадратных или фигурных скобок. Может быть использован только один из этих элементов.|  
|`[ ]` (квадратные скобки)|Необязательные элементы синтаксиса. Квадратные скобки не вводятся.|  
|{ } (фигурные скобки)|Обязательные элементы синтаксиса. Фигурные скобки не вводятся.|  
|[ **,** ..._n_]|Указывает на то, что предшествующий элемент можно повторить _n_ раз. Вхождения элемента разделяются запятыми.|  
|[..._n_]|Указывает на то, что предшествующий элемент можно повторить _n_ раз. Отдельные вхождения элемента разделяются пробелами.|  
|;|Признак конца инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)]. Хотя точка с запятой не требуется для большинства инструкций в этой версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], этот символ станет обязательным в будущей версии.|  
|\<label> ::=|Имя синтаксического блока. Используйте это соглашение для группирования и маркировки сегментов с длинным синтаксисом или элемента синтаксиса, который может использоваться в нескольких расположениях в пределах одной инструкции. Каждое расположение, в котором может быть использован синтаксический блок, обозначается меткой, заключенной в шевроны: \<label>.<br /><br /> Набор представляет собой коллекцию выражений, например \<grouping set>; а список — коллекцию наборов, например \<composite element list>.|  
  
## <a name="multipart-names"></a>Многочастные имена  
Если не указано иное, все ссылки [!INCLUDE[tsql](../../includes/tsql-md.md)] на имена объектов базы данных могут быть четырехсоставными именами, записываемыми в следующей форме.  
  
_server\_name_.[_database\_name_].[_schema\_name_]._object\_name_  
  
| _database\_name_.[_schema\_name_]._object\_name_  
 
| _schema\_name_._object\_name_  
  
| _object\_name_  
  
_server\_name_  
Указывает имя связанного или удаленного сервера.  
  
_database\_name_  
Указывает имя базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], если объект хранится на локальном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Когда объект находится на связанном сервере, аргумент *database_name* указывает каталог OLE DB.  
  
_schema\_name_  
Если объект находится в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], указывает имя схемы, которая содержит объект. Когда объект находится на связанном сервере, аргумент *schema_name* указывает имя схемы OLE DB.  
  
_object\_name_  
Ссылается на имя объекта.  
  
При ссылке на конкретный объект нет необходимости всякий раз указывать сервер, базу данных и схему — компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] попытается определить этот объект. Однако, если объект не удается найти, возвращается ошибка.  
  
> [!NOTE]  
> Чтобы избежать ошибок разрешения имен, при указании объекта области схемы рекомендуется указать имя схемы.  
  
Чтобы пропустить промежуточные узлы, для обозначения их позиций используйте точки. В следующей таблице показаны допустимые форматы имен объектов.  
  
|Формат ссылки на объект|Описание|  
|-----------------------------|-----------------|  
|_server_._database_._schema_._object_|Четырехчастное имя.|  
|_server_._database_.._object_|Имя схемы пропущено.|  
|_server_.._schema_._object_|Имя базы данных пропущено.|  
|_server_..._object_|Имя базы данных и имя схемы пропущены.|  
|_database_._schema_._object_|Имя сервера пропущено.|  
|_database_.._object_|Имя сервера и имя схемы пропущены.|  
|_schema_._object_|Имя сервера и имя базы данных пропущены.|  
|_object_|Имена сервера, базы данных и схемы пропущены.|  
  
## <a name="code-example-conventions"></a>Соглашения примеров кода  
Если не указано иное, примеры, приведенные в справочнике по [!INCLUDE[tsql](../../includes/tsql-md.md)], были проверены с использованием среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и настроек по умолчанию для следующих параметров:  
  
-   ANSI_NULLS  
-   ANSI_NULL_DFLT_ON  
-   ANSI_PADDING  
-   ANSI_WARNINGS  
-   CONCAT_NULL_YIELDS_NULL  
-   QUOTED_IDENTIFIER  
  
Большинство примеров кода в руководстве по [!INCLUDE[tsql](../../includes/tsql-md.md)] было проверено на серверах, работающих с порядком сортировки с учетом регистра. Тестовые серверы, как правило, использовали кодовую страницу ANSI/ISO 1252.  
  
Многие примеры кода добавляют к строковым константам в Юникоде префикс в виде буквы **N**. Без префикса **N** строка преобразуется в кодовую страницу базы данных по умолчанию. Кодовая страница по умолчанию может не распознавать определенные символы.  
  
## <a name="applies-to-references"></a>Ссылки «Относится к»  
Ссылка [!INCLUDE[tsql](../../includes/tsql-md.md)] включает статьи, относящиеся к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]), [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] и [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)].   

В верхней части каждой статьи есть раздел, где указано, к каким продуктам относится тема статьи. Если продукт не указан, то компонент, описанный в статье, для данного продукта недоступен. Например, группы доступности были введены в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. В статье о **CREATE AVAILABILITY GROUP** указано, что эта функция применима к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]), так как она неприменима к [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] или [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
К продукту относится общая тема статьи, но в некоторых случаях не все аргументы поддерживаются. Например, пользователи автономной базы данных впервые появились в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. Инструкцию **CREATE USER** можно применять в любом продукте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], однако синтаксис **WITH PASSWORD** не может использоваться с более ранними версиями. Дополнительные разделы **Область применения** вставляются в описания соответствующих аргументов в статье.  
  
## <a name="see-also"></a>См. также:  
[Справочник по Transact-SQL &#40;ядро СУБД&#41;](../../t-sql/transact-sql-reference-database-engine.md)    
[Зарезервированные ключевые слова &#40;Transact-SQL&#41;](../../t-sql/language-elements/reserved-keywords-transact-sql.md)      
[Проблемы проектирования Transact-SQL](https://msdn.microsoft.com/library/dd193411.aspx)    
[Проблемы именования Transact-SQL](https://msdn.microsoft.com/library/dd193246.aspx)        
[Проблемы производительности Transact-SQL](https://msdn.microsoft.com/library/dd172117.aspx)    


