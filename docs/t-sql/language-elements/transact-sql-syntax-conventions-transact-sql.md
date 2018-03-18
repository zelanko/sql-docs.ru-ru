---
title: "Синтаксические обозначения в Transact-SQL (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: 7c4eb67190b5123296fbcffb3fac3f09e9ec2000
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="transact-sql-syntax-conventions-transact-sql"></a>Синтаксические обозначения в Transact-SQL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  В следующей таблице перечислены и описаны соглашения, которые используются в синтаксисе в справочнике по [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
|Обозначение|Используется для|  
|----------------|--------------|  
|ВЕРХНИЙ РЕГИСТР|Ключевые слова [!INCLUDE[tsql](../../includes/tsql-md.md)].|  
|*курсив*|Пользовательские параметры синтаксиса [!INCLUDE[tsql](../../includes/tsql-md.md)].|  
|**полужирный**|Имена баз данных, таблиц, столбцов, индексов, хранимых процедур, программ, типов данных и текст должны вводиться в точном соответствии с примером.|  
|**underline**|Указывает значение по умолчанию, которое применяется, когда в инструкции пропущено предложение, содержащее подчеркнутое значение.|  
|&#124; (вертикальная черта)|Разделяет элементы синтаксиса внутри квадратных или фигурных скобок. Может быть использован только один из этих элементов.|  
|`[ ]` (квадратные скобки)|Необязательные элементы синтаксиса. Скобки набирать не следует.|  
|{ } (фигурные скобки)|Обязательные элементы синтаксиса. Скобки набирать не следует.|  
|[**,**...*n*]|Указывает на то, что предшествующий элемент можно повторить *n* раз. Вхождения элемента разделяются запятыми.|  
|[...*n*]|Указывает на то, что предшествующий элемент можно повторить *n* раз. Отдельные вхождения элемента разделяются пробелами.|  
|;|Признак конца инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)]. Хотя точка с запятой не требуется для большинства инструкций в данной версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], она понадобится в следующей версии.|  
|\<label> ::=|Имя синтаксического блока. Это обозначение используется для группирования и маркировки сегментов с длинным синтаксисом или элемента синтаксиса, который может использоваться в нескольких местах в пределах одной инструкции. Каждое место, в котором может быть использован синтаксический блок, обозначается меткой, заключенной в двойные угловые скобки: \<label>.<br /><br /> Набор представляет собой коллекцию выражений, например \<grouping set>; а список — коллекцию наборов, например \<composite element list>.|  
  
## <a name="multipart-names"></a>Многочастные имена  
 Если не указано иное, все ссылки [!INCLUDE[tsql](../../includes/tsql-md.md)] на имена объектов базы данных могут быть четырехсоставными именами, записываемыми в следующей форме.  
  
 *server_name* **.**[*database_name*]**.**[*schema_name*]**.***object_name*  
  
 | *database_name***.**[*schema_name*]**.***object_name*  
  
 | *schema_name***.***object_name*  
  
 *| object_name*  
  
 *server_name*  
 Указывает имя связанного или удаленного сервера.  
  
 *database_name*  
 Указывает имя базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], если объект хранится на локальном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Когда объект находится на связанном сервере, аргумент *database_name* указывает каталог OLE DB.  
  
 *schema_name*  
 Если объект находится в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], указывает имя схемы, которая содержит объект. Когда объект находится на связанном сервере, аргумент *schema_name* указывает имя схемы OLE DB.  
  
 *object_name*  
 Ссылается на имя объекта.  
  
 При ссылке на конкретный объект нет необходимости всякий раз указывать сервер, базу данных и схему — компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] попытается определить этот объект. Однако, если объект не удается найти, возвращается ошибка.  
  
> [!NOTE]  
>  Чтобы избежать ошибок разрешения имен, при указании объекта области схемы рекомендуется указать имя схемы.  
  
 Чтобы пропустить промежуточные узлы, для обозначения их позиций используйте точки. В следующей таблице показаны допустимые форматы имен объектов.  
  
|Формат ссылки на объект|Description|  
|-----------------------------|-----------------|  
|*server* **.** *database* **.** *schema* **.** *object*|Четырехчастное имя.|  
|*server* **.** *database* **..** *object*|Имя схемы пропущено.|  
|*server* **..** *schema* **.** *object*|Имя базы данных пропущено.|  
|*server* **...** *object*|Имя базы данных и имя схемы пропущены.|  
|*database* **.** *schema* **.** *object*|Имя сервера пропущено.|  
|*database* **..** *object*|Имя сервера и имя схемы пропущены.|  
|*schema* **.** *object*|Имя сервера и имя базы данных пропущены.|  
|*object*|Имена сервера, базы данных и схемы пропущены.|  
  
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
 Ссылка [!INCLUDE[tsql](../../includes/tsql-md.md)] включает разделы, относящиеся к [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] и [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]. В верхней части каждого раздела есть глава, где указано, какие продукты поддерживают тему раздела. Если продукт не указан, то компонент, описанный в разделе, для данного продукта недоступен. Например, группы доступности были введены в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. В разделе **CREATE AVAILABILITY GROUP** указано, что он применяется к **SQL Server (SQL Server 2012 до текущей версии)**, так как он не применяется к [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] или [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 В некоторых случаях в продукте используется общая тема раздела, но не все аргументы поддерживаются. Например, пользователи автономной базы данных впервые появились в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. Инструкция **CREATE USER** может использоваться в любом продукте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], однако синтаксис **WITH PASSWORD** не может использоваться с более ранними версиями. В этом случае дополнительные главы **Область применения** вставляются в описания соответствующих аргументов в разделе.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по Transact-SQL (компонент Database Engine)](../../t-sql/transact-sql-reference-database-engine.md)  
  
  


