---
title: "Обновлено — документы по реляционным базам данных | Документация Майкрософт"
description: "Отображение фрагментов обновленного содержимого для последних изменений в документации по реляционным базам данных."
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
ms.date: 07/17/2017
ms.author: genemi
ms.translationtype: HT
ms.sourcegitcommit: 71203bfa7cb4dcd06cc14ad8e49e5bc1113f8605
ms.openlocfilehash: 519fbd2bc596112dbb1c662d76e4aeeb230ffc36
ms.contentlocale: ru-ru
ms.lasthandoff: 07/31/2017

---
# <a name="new-and-recently-updated-relational-databases-docs"></a>Новые и недавно обновленные статьи — документы по реляционным базам данных



Почти каждый день корпорация Майкрософт вносит изменения в свои статьи на веб-сайте документации [Docs.Microsoft.com](http://docs.microsoft.com/). В этой статье приводятся отрывки из обновленных недавно статей, а также ссылки на новые статьи.

Статья создается программой и периодически обновляется. Отрывки из измененных статей могут иметь неидеальный формат или разметку исходной статьи. Картинки здесь не отображаются.

Последние обновления соответствуют следующему периоду времени и предметной области:



- *Диапазон дат для обновлений:* &nbsp; **23.05.2017** &nbsp;—&nbsp; **17.07.2017**
- *Предметная область:* &nbsp; **Реляционные базы данных**.




&nbsp;

## <a name="new-articles-created-recently"></a>Недавно созданные статьи

Приведенные ниже ссылки указывают на новые статьи, которые были добавлены недавно.


1. [Внутренние компоненты выполняющейся в памяти OLTP SQL Server для SQL Server 2016](in-memory-oltp/sql-server-in-memory-oltp-internals-for-sql-server-2016.md)
2. [Адаптивная обработка запросов в базах данных SQL](performance/adaptive-query-processing.md)
3. [Руководство по улучшению конфиденциальности и удовлетворению требований GDPR с помощью платформы Microsoft SQL](security/microsoft-sql-and-the-gdpr-requirements.md)
4. [sys.pdw_replicated_table_cache_state (Transact-SQL)](system-catalog-views/sys-pdw-replicated-table-cache-state-transact-sql.md)
5. [sys.trusted_assemblies (Transact-SQL)](system-catalog-views/sys-trusted-assemblies-transact-sql.md)
6. [sys.dm_exec_query_parallel_workers (Transact-SQL)](system-dynamic-management-views/sys-dm-exec-query-parallel-workers-transact-sql.md)
7. [sys.sp_add_trusted_assembly (Transact-SQL)](system-stored-procedures/sys-sp-add-trusted-assembly-transact-sql.md)
8. [sys.sp_drop_trusted_assembly (Transact-SQL)](system-stored-procedures/sys-sp-drop-trusted-assembly-transact-sql.md)




&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>Сокращенный список недавно обновленных статей

В этом сокращенном списке приводятся ссылки на все обновленные статьи, перечисленные в разделе "Отрывки".



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Обновленные статьи с отрывками

В этом разделе приводятся отрывки из статей, в которые недавно были внесены значительные изменения.

Отрывки отображаются отдельно от соответствующего семантического контекста. Кроме того, иногда фрагмент отделяется от синтаксиса разметки, окружающей саму статью. Таким образом, эти отрывки приводятся только для общего сведения. Они позволяют понять, стоит ли вам перейти по ссылке и прочитать всю статью полностью.

По этой и другим причинам не копируйте код из этих отрывков и не воспринимайте содержание этих отрывков как однозначно верное. Вместо этого пройдите по ссылке и ознакомьтесь с фактическим текстом статьи.



&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-altering-memory-optimized-tablesin-memory-oltpaltering-memory-optimized-tablesmd"></a>1. &nbsp; [Изменение таблиц, оптимизированных для памяти](in-memory-oltp/altering-memory-optimized-tables.md)

*Обновление: 23.06.2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Далее](#TitleNum_2))

<!-- Source markdown line 82.  ms.author= "genemi".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 8359700b5db24838f1bb273526794c2865bbbe11 41d77cf0bbcf53a1b64d6524a24e5736c5a073da  (PR=2171  ,  Filename=altering-memory-optimized-tables.md  ,  Dirpath=docs\relational-databases\in-memory-oltp\  ,  MergeCommitSha40=7d2dbe0bdc4cbd05f11eacf938b35a9c35ace2e7) -->



**Ведение журнала по инструкции ALTER TABLE для таблиц, оптимизированных для памяти**

В таблицах, оптимизированных для памяти, большинство сценариев ALTER TABLE теперь выполняются параллельно и позволяют оптимизировать операции записи в журнал транзакций. Оптимизация заключается в том, что только изменения метаданных записываются в журнал транзакций. Тем не менее следующие операции ALTER TABLE запускаются в одном потоке и не оптимизированы для журнала.

В этом случае однопотоковая операция записала бы в журнал транзакций все содержимое измененной таблицы. Далее приведен список операций, выполняемых в одном потоке:

- изменение и добавление столбца для использования типа данных больших объектов (LOB): nvarchar(max), varbinary(max) или varchar(max);

- добавление или удаление индекса columnstore;

- почти все, что влияет на [столбец "вне строки"--../../relational-databases/in-memory-oltp/supported-data-types-for-in-memory-oltp.md);

    - перемещение столбца в строке за пределы строки;

    - перемещение столбца вне строки в строку;

    - создание нового столбца вне строки.

    - *Исключение:* удлинение столбца, который уже находится вне строки, фиксируется в журнале оптимизированным образом. 
  




&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-table-and-row-size-in-memory-optimized-tablesin-memory-oltptable-and-row-size-in-memory-optimized-tablesmd"></a>2. &nbsp; [Размер строк и таблицы для таблиц, оптимизированных для памяти](in-memory-oltp/table-and-row-size-in-memory-optimized-tables.md)

*Обновлено: 22.06.2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Назад](#TitleNum_1) | [Далее](#TitleNum_3))

<!-- Source markdown line 114.  ms.author= "genemi".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 27ce0fa2e7bb464f9c3d6e32dd195de3b79abfcd 0a3cacd86024e2b734704ffd37e55ca0b17a0c94  (PR=2163  ,  Filename=table-and-row-size-in-memory-optimized-tables.md  ,  Dirpath=docs\relational-databases\in-memory-oltp\  ,  MergeCommitSha40=fe6de2b16b9792a5399b1c014af72a2a5ee52377) -->



 
  
 Вычисление [размера текста строки] демонстрируется в следующей таблице.  
  
 Размер текста строки вычисляется двумя способами: вычисляемый размер и фактический размер.  
  
-   Вычисляемый размер, далее [вычисляемый размер строки текста], используется для того, чтобы определить, не превышает ли размер строки ограничение в 8060 байт.  
  
-   Фактический размер, далее [фактический размер строки текста], представляет собой фактический размер хранилища текста строки в памяти и в файле контрольных точек.  
  
 Оба показателя [вычисляемый размер строки текста] и [фактический размер строки текста] вычисляются аналогичным образом. Отличается только вычисление размера столбцов (n)varchar(I) и столбцов varbinary (I), как показано в нижней части таблицы. Вычисляемый размер строки использует в качестве размера столбца декларируемый размер *i* , тогда как фактический размер строки использует фактический размер данных.  
  
 В следующей таблице описано вычисление размера текста строки как [фактический размер текста строки] = SUM([размер мелких типов]) + 2 + 2 * [число столбцов глубокого типа].  
  
|Раздел|Размер|Комментарии|  
|-------------|----------|--------------|  
|Столбцы поверхностных типов|SUM [размер поверхностных типов] Размер отдельных типов в байтах:<br /><br /> **Bit**: 1<br /><br /> **Tinyint**: 1<br /><br /> **Smallint**: 2<br /><br /> **Int**: 4<br /><br /> **Real**: 4<br /><br /> **Smalldatetime**: 4<br /><br /> **Smallmoney**: 4<br /><br /> **Bigint**: 8<br /><br /> **Datetime**: 8<br /><br /> **Datetime2**: 8<br /><br /> **Float**: 8<br /><br /> **Money**: 8<br /><br /> **Numeric** (точность <=18): 8<br /><br /> **Time**: 8<br /><br /> **Numeric**(точность>18): 16<br /><br /> **Uniqueidentifier**: 16||  
|Заполнение столбца поверхностного типа|Возможны следующие значения:<br /><br /> 1, если в таблице присутствуют столбцы глубоких типов, а общий размер данных в столбцах поверхностного типа является нечетным числом.<br /><br /> 0 в остальных случаях|Глубокие типы — это типы (var)binary и (n)(var)char.|  




&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-post-migration-validation-and-optimization-guidepost-migration-validation-and-optimization-guidemd"></a>3. &nbsp; [Руководство по оптимизации и проверке после миграции](post-migration-validation-and-optimization-guide.md)

*Обновлено: 21.06.2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Назад](#TitleNum_2) | [Далее](#TitleNum_4))

<!-- Source markdown line 27.  ms.author= "harinid".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 faa2e3dd8be3aeb475bf8c7f71617ebf17969892 f2760dfecda10baeb121929b72a4d8164e81185b  (PR=2126  ,  Filename=post-migration-validation-and-optimization-guide.md  ,  Dirpath=docs\relational-databases\  ,  MergeCommitSha40=dcbeda6b8372b358b6497f78d6139cad91c8097c) -->



Ниже приведены некоторые распространенные сценарии, возникающие после миграции на платформу [!INCLUDE[ssNoVersion--../includes/ssnoversion-md.md)], а также способы их разрешения. Сюда относятся сценарии, характерные для перехода с [!INCLUDE[ssNoVersion--../includes/ssnoversion-md.md)] на [!INCLUDE[ssNoVersion--../includes/ssnoversion-md.md)] (со старых версий на новые), а также для перехода с внешней платформы (например, Oracle, DB2, MySQL и Sybase) на [!INCLUDE[ssNoVersion--../includes/ssnoversion-md.md)].

**<a name="CEUpgrade"></a> Регрессии запросов из-за изменения в версии CE**


**Область применения:** переход с [!INCLUDE[ssNoVersion--../includes/ssnoversion-md.md)] на [!INCLUDE[ssNoVersion--../includes/ssnoversion-md.md)].

При переходе с более старых версий [!INCLUDE[ssNoVersion--../includes/ssnoversion-md.md)] на [!INCLUDE[ssSQL14--../includes/sssql14-md.md)] или более новой версии и при обновлении [уровня совместимости базы данных--../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md) до самого последнего рабочая нагрузка может подвергаться риску регрессии производительности.

Это объясняется тем, что, начиная с [!INCLUDE[ssSQL14--../includes/sssql14-md.md)], все изменения в оптимизаторе запросов привязаны к последнему [уровню совместимости базы данных--../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md), поэтому планы изменяются не в момент обновления, а когда пользователь изменяет параметр базы данных `COMPATIBILITY_LEVEL` на последнюю версию. В сочетании с хранилищем запросов эта возможность обеспечивает высокий уровень контроля над производительностью запросов в процессе обновления. 

Дополнительные сведения об изменениях оптимизатора запросов, появившихся в [!INCLUDE[ssSQL14](../includes/sssql14-md.md)], см. в документе [Optimizing Your Query Plans with the SQL Server 2014 Cardinality Estimator](http://msdn.microsoft.com/library/dn673537.aspx) (Оптимизация планов запросов с помощью модуля оценки кратности SQL Server 2014).




&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-sysquerystoreplan-transact-sqlsystem-catalog-viewssys-query-store-plan-transact-sqlmd"></a>4. &nbsp; [sys.query_store_plan (Transact-SQL)](system-catalog-views/sys-query-store-plan-transact-sql.md)

*Обновлено: 05.06.2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Назад](#TitleNum_3))

<!-- Source markdown line 58.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 1b77e34309ba7033578b3c82ed83c8c2fbc93e24 ce4ade9ab906c35cb87068a1fb91c4e1d7549aac  (PR=1940  ,  Filename=sys-query-store-plan-transact-sql.md  ,  Dirpath=docs\relational-databases\system-catalog-views\  ,  MergeCommitSha40=1d363db8e8bd0e1460cdea3c3a7add68e48714c9) -->



**Ограничения принудительного использования планов**

Хранилище запросов имеет механизм, позволяющий оптимизатору запросов принудительно применить определенный план выполнения. Но существуют некоторые ограничения, которые могут препятствовать применению плана. 

Во-первых, когда план содержит следующие конструкции:
* Инструкция INSERT BULK.
* Инструкция INSERT BULK.
* ссылка на внешнюю таблицу;
* распределенный запрос или полнотекстовые операции;
* использование глобальных запросов. 
* Курсоры
* Недопустимая спецификация соединения типа "звезда" 

Во-вторых, когда объекты, от которых зависит план, больше не доступны:
* база данных (если база данных, где план был создан изначально, больше не существует);
* индекс (больше не существует или отключен).

Наконец, проблемы с самим планом:
* недопустим для запроса;
* оптимизатор запросов превысил количество разрешенных операций;
* неправильно сформированный XML-код плана.





<a name="similars2"/>

&nbsp;

## <a name="similar-articles"></a>Похожие статьи

Этот раздел содержит похожие статьи, аналогичные недавно измененным, для других предметных областей в том же репозитории GitHub.com: [MicrosoftDocs/**sql-docs-pr**](https://github.com/microsoftdocs/sql-docs-pr/).

<!--  20170717-1101  -->

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Предметные области, содержащие новые или недавно обновленные статьи

- [Новые + обновленные (4+4): **Дополнительные аналитические функции для SQL**](../advanced-analytics/new-updated-advanced-analytics.md)
- [Новые + обновленные (2+0): **Analysis Services для SQL**](../analysis-services/new-updated-analysis-services.md)
- [Новые + обновленные (1+2): **Подключение к SQL**](../connect/new-updated-connect.md)
- [Новые + обновленные (6+0): **Ядро СУБД для SQL**](../database-engine/new-updated-database-engine.md)
- [Новые + обновленные (13+2): **Linux для SQL**](../linux/new-updated-linux.md)
- [Новые + обновленные (1+0): **Master Data Services (MDS) для SQL**](../master-data-services/new-updated-master-data-services.md)
- [Новые + обновленные (1+0): **ODBC (Open Database Connectivity) для SQL**](../odbc/new-updated-odbc.md)
- [Новые + обновленные (8+4): **Реляционные базы данных для SQL**](../relational-databases/new-updated-relational-databases.md)
- [Новые + обновленные (2+2): **Microsoft SQL Server**](../sql-server/new-updated-sql-server.md)
- [Новые + обновленные (0+1): **SQL Server Management Studio (SSMS)**](../ssms/new-updated-ssms.md)
- [Новые + обновленные (1+0): **Transact-SQL**](../t-sql/new-updated-t-sql.md)
- [Новые + обновленные (1+0): **Инструменты для SQL**](../tools/new-updated-tools.md)


#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Предметные области, не содержащие новые или недавно обновленные статьи

- [Новые + обновленные (0+0): **объекты данных ActiveX (ADO) для SQL**](../ado/new-updated-ado.md)
- [Новые + обновленные (0+0): **Data Quality Services для SQL**](../data-quality-services/new-updated-data-quality-services.md)
- [Новые + обновленные (0+0): **расширения интеллектуального анализа данных (DMX) для SQL**](../dmx/new-updated-dmx.md)
- [Новые + обновленные (0+0): **Integration Services для SQL**](../integration-services/new-updated-integration-services.md)
- [Новые + обновленные (0+0): **многомерные выражения (MDX) для SQL**](../mdx/new-updated-mdx.md)
- [Новые + обновленные (0+0): **PowerShell для SQL**](../powershell/new-updated-powershell.md)
- [Новые + обновленные (0+0): **Reporting Services для SQL**](../reporting-services/new-updated-reporting-services.md)
- [Новые + обновленные (0+0): **примеры для SQL**](../sample/new-updated-sample.md)
- [Новые + обновленные (0+0): **SQL Server Data Tools (SSDT)**](../ssdt/new-updated-ssdt.md)
- [Новые + обновленные (0+0): **помощник по миграции SQL Server (SSMA)**](../ssma/new-updated-ssma.md)
- [Новые + обновленные (0+0): **XQuery для SQL**](../xquery/new-updated-xquery.md)


&nbsp;


