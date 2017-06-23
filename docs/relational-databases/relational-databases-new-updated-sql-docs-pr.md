---
title: "Обновлено - docs реляционных баз данных | Документы Microsoft"
description: "Отображение фрагментов обновленное содержимое для последних измененных в документации для реляционных баз данных."
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: BYHAM
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.workload: relational-databases
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 05/23/2017
ms.author: genemi
ms.translationtype: Human Translation
ms.sourcegitcommit: 96f6a7eeb03fdc222d0e5b42bcfbf05c25d11db6
ms.openlocfilehash: 3ab051a6fd00670139bb1089dcd3f4af76b9ecef
ms.contentlocale: ru-ru
ms.lasthandoff: 06/23/2017

---
# <a name="new-and-recently-updated-relational-databases-docs"></a>Обновление новых и недавно: docs реляционных баз данных



Почти каждый день Корпорация Майкрософт обновляет некоторые из его существующих статей на его [Docs.Microsoft.com](http://docs.microsoft.com/) документации веб-сайта. В этой статье отображает выдержки из недавно обновлены статьи. Ссылки на новые статьи также может быть указан.

В этой статье создается программой, которая периодически запускается повторно. Иногда фрагмент могут отображаться идеально подходит форматирования или как разметки из статьи источника. Образы никогда не отображается.

Следующий диапазон дат и темы отображаются последние обновления:



- *Диапазон обновлений дат:* &nbsp; **2017 г-05-01** &nbsp; - в - &nbsp; **2017 г-05-23**
- *Предметной области:* &nbsp; **реляционных баз данных**.




&nbsp;

## <a name="updated-articles-with-excerpts"></a>Обновлены статьи с отрывки

В этом разделе отображается отрывки обновлений, полученные из статей, в которых были недавно крупных обновлений.

Из семантической контексту отрывки, показанные здесь отображаются раздельно. Кроме того иногда фрагмент отделяется от синтаксис важные разметки окружающего в реальной статьи. Поэтому эти отрывки являются только общие рекомендации. Только отрывки позволяют знаете ли потребностей гарантирует времени, нажмите кнопку и посетите реальной статьи.

Для этих и других причин не копировать из этих отрывки кода и не выполняют как точное истинности любой фрагмент текста. Вместо этого посетите реальной статьи.



&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-create-a-graph-database-and-run-some-pattern-matching-queries-using-t-sqlgraphssql-graph-samplemd"></a>1. &nbsp;[Создание диаграммы базы данных и выполнить некоторые шаблоны запросов с помощью T-SQL](graphs/sql-graph-sample.md)

*Updated: 2017-05-04* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Next](#TitleNum_2))

<!-- Source markdown line 68.  ms.author= "shkale".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 ff467bf5fcf13592c796836def36e16e34f8cc31 99fcf0399006de16d0ac7cc9057564d307cb981b -->


```
INSERT INTO Person VALUES (1,'John');
INSERT INTO Person VALUES (2,'Mary');
INSERT INTO Person VALUES (3,'Alice');
INSERT INTO Person VALUES (4,'Jacob');
INSERT INTO Person VALUES (5,'Julie');

INSERT INTO Restaurant VALUES (1,'Taco Dell','Bellevue');
INSERT INTO Restaurant VALUES (2,'Ginger and Spice','Seattle');
INSERT INTO Restaurant VALUES (3,'Noodle Land', 'Redmond');

INSERT INTO City VALUES (1,'Bellevue','wa');
INSERT INTO City VALUES (2,'Seattle','wa');
INSERT INTO City VALUES (3,'Redmond','wa');

-- Insert into edge table. While inserting into an edge table, 
-- you need to provide the $node_id from $from_id and $to_id columns.
INSERT INTO likes VALUES ((SELECT $node_id FROM Person WHERE id = 1), 
       (SELECT $node_id FROM Restaurant WHERE id = 1),9);
INSERT INTO likes VALUES ((SELECT $node_id FROM Person WHERE id = 2), 
      (SELECT $node_id FROM Restaurant WHERE id = 2),9);
INSERT INTO likes VALUES ((SELECT $node_id FROM Person WHERE id = 3), 
      (SELECT $node_id FROM Restaurant WHERE id = 3),9);
INSERT INTO likes VALUES ((SELECT $node_id FROM Person WHERE id = 4), 
      (SELECT $node_id FROM Restaurant WHERE id = 3),9);
INSERT INTO likes VALUES ((SELECT $node_id FROM Person WHERE id = 5), 
      (SELECT $node_id FROM Restaurant WHERE id = 3),9);

INSERT INTO livesIn VALUES ((SELECT $node_id FROM Person WHERE id = 1),
      (SELECT $node_id FROM City WHERE id = 1));
INSERT INTO livesIn VALUES ((SELECT $node_id FROM Person WHERE id = 2),
      (SELECT $node_id FROM City WHERE id = 2));
INSERT INTO livesIn VALUES ((SELECT $node_id FROM Person WHERE id = 3),
      (SELECT $node_id FROM City WHERE id = 3));
INSERT INTO livesIn VALUES ((SELECT $node_id FROM Person WHERE id = 4),
      (SELECT $node_id FROM City WHERE id = 3));
INSERT INTO livesIn VALUES ((SELECT $node_id FROM Person WHERE id = 5),
      (SELECT $node_id FROM City WHERE id = 1));

INSERT INTO locatedIn VALUES ((SELECT $node_id FROM Restaurant WHERE id = 1),
      (SELECT $node_id FROM City WHERE id =1));
```



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-sysfngetauditfile-transact-sqlsystem-functionssys-fn-get-audit-file-transact-sqlmd"></a>2. &nbsp; [sys.fn_get_audit_file (Transact-SQL)](system-functions/sys-fn-get-audit-file-transact-sql.md)

*Updated: 2017-05-16* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Previous](#TitleNum_1) | [Next](#TitleNum_3))

<!-- Source markdown line 145.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 046fa92ad1b7e6bb7a956493ca06cf72d45b5285 fbf55361da90663835d7e107fda697c358e0e061 -->



- **База данных SQL Azure**

  В следующем примере выполняется чтение из файла, который имеет имя `ShiraServer/MayaDB/SqlDbAuditing_Audit/2017-07-14/10_45_22_173_1.xel`.  
  
  ```  
  SELECT * FROM sys.fn_get_audit_file sys.fn_get_audit_file ('https://mystorage.blob.core.windows.net/sqldbauditlogs/ShiraServer/MayaDB/SqlDbAuditing_Audit/2017-07-14/10_45_22_173_1.xel',default,default);
  GO  
  ```  

  Этот пример считывает все журналы с серверов, которые начинаются с аудита `Sh`.  
  
  ```  
  SELECT * FROM sys.fn_get_audit_file sys.fn_get_audit_file ('https://mystorage.blob.core.windows.net/sqldbauditlogs/Sh',default,default);
  GO  
  ```





&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-manage-retention-of-historical-data-in-system-versioned-temporal-tablestablesmanage-retention-of-historical-data-in-system-versioned-temporal-tablesmd"></a>3. &nbsp;[Управление хранением данных журнала в Темпоральных таблицах с системным управлением версиями](tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)

*Updated: 2017-05-19* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Previous](#TitleNum_2))

<!-- Source markdown line 425.  ms.author= "carlrab".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 ee69beb6a46913934d4a322f5d95343cc86f2ec4 94da98fec4ab16636a4581c16eb4456e2d1ff66b -->



**Используя подход политики хранения журнала**

> **Примечание:** с помощью временных политики хранения журнала подход действует для [! ВКЛЮЧИТЬ [sqldbesa--... /.. /includes/sqldbesa-MD.md]) и SQL Server 2017 г., начиная с CTP-версии 1.3.  

Хранение журнала может быть настроен на уровне отдельных таблиц, который дает пользователям возможность создавать гибкие время существования политики. Применение временного хранения проста: требуется только один параметр для задания во время создания или схемы изменения таблицы.

После определения политики хранения, базы данных SQL Azure запускает регулярно проверку, если есть исторических строк, пригодных для Автоматическая очистка. Идентификация совпадающих строк и их удаление из таблицы журнала прозрачного, выполнения в фоновой задачей, которая является планируются и выполняются в системе. Возраст условия для строк таблицы журнала, проверяется на основе столбца, представляющее конец периода SYSTEM_TIME. Если срок хранения, например, равным шесть месяцев, строк таблицы, подходящие для очистки удовлетворять следующим условиям:
```
ValidTo < DATEADD (MONTH, -6, SYSUTCDATETIME())
```
В предыдущем примере предполагается, что ValidTo столбец соответствует окончания периода SYSTEM_TIME.
**Как настроить политику хранения?**

Прежде чем настраивать политику хранения для темпоральной таблицы, сначала проверьте включен ли временного хранения журнала на уровне базы данных.
```
SELECT is_temporal_history_retention_enabled, name
FROM sys.databases
```
Базы данных флаг **is_temporal_history_retention_enabled** установлен в ON по умолчанию, но пользователи могут изменить с помощью инструкции ALTER DATABASE. Он также автоматически устанавливается в OFF после точки во время операции восстановления. Чтобы включить очистку хранения журнала для базы данных, выполните следующую инструкцию:
```
ALTER DATABASE <myDB>
SET TEMPORAL_HISTORY_RETENTION  ON
```
Настроена политика хранения во время создания таблицы путем указания значения для параметра HISTORY_RETENTION_PERIOD:
```
CREATE TABLE dbo.WebsiteUserInfo
```





&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>Сокращенный список статей, недавно обновлены

Compact представлены ссылки на обновленные статьи, перечисленные в предыдущем разделе.

1. [Создание диаграммы базы данных и выполнить некоторые шаблоны запросов с помощью T-SQL](#TitleNum_1)
2. [sys.fn_get_audit_file (Transact-SQL)](#TitleNum_2)
3. [Управление хранением данных журнала в темпоральных таблицах с системным управлением версиями](#TitleNum_3)


<a name="sisters2"/>

&nbsp;

## <a name="sister-articles"></a>Филиалы статей

В этом разделе перечислены схожий статей для недавно обновлены статьи в других предметных областей, в одном репозитории GitHub.


&nbsp;

[Microsoft и**sql документы pr** ](https://github.com/microsoftdocs/sql-docs-pr/) репозитория в GitHub.com:

- [Недавно обновлены: **реляционных баз данных и Microsoft SQL Server** документы](/sql/relational-databases/relational-databases-new-updated-sql-docs-pr)
- [Недавно обновлены: **Microsoft SQL Server** документы](/sql/sql-server/sql-server-new-updated-sql-docs-pr)
- [Недавно обновлены: **Transact-SQL в SQL Server** документы](/sql/t-sql/t-sql-new-updated-sql-docs-pr)


&nbsp;

<!--
[Microsoft/**azure-docs**](https://github.com/microsoft/azure-docs/) repository on GitHub.com:

- [Sisters list for **azure-docs** repo](https://docs.microsoft.com/azure/sql-server-new-updated-azure-docs/#sisters2)
-->

&nbsp;



