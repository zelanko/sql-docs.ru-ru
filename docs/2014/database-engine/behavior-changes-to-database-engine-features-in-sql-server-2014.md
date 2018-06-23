---
title: Изменения в работе базы данных подсистемы функции в SQL Server 2014 | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- behavior changes [SQL Server]
- Database Engine [SQL Server], what's new
- Transact-SQL behavior changes
ms.assetid: 65eaafa1-9e06-4264-b547-cbee8013c995
caps.latest.revision: 134
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b91a84ac2973ee5569ff9a9f4b3fa54737492068
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36099853"
---
# <a name="behavior-changes-to-database-engine-features-in-sql-server-2014"></a>Изменения в работе функций компонента Database Engine в SQL Server 2014
  В этом разделе описаны изменения в компоненте [!INCLUDE[ssDE](../includes/ssde-md.md)]. Изменения в работе оказывают влияние на способ выполнения функций или взаимодействие между ними в [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] по сравнению с предыдущими версиями [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
## <a name="behavior-changes-in-includesssql14includessssql14-mdmd"></a>Изменения в поведении [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 В предыдущих версиях [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] запросы к XML-документу, содержащие строки длиннее определенной длины (более 4020 символов), могут возвращать неверные результаты. В [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] такие результаты возвращаются верно.  
  
## <a name="behavior-changes-in-includesssql11includessssql11-mdmd"></a>Изменения в поведении [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
  
### <a name="metadata-discovery"></a>Обнаружение метаданных  
 Улучшения в [!INCLUDE[ssDE](../includes/ssde-md.md)] начиная с версии [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] разрешить SQLDescribeCol получить более точные описания ожидаемых результатов, чем, возвращенные в предыдущих версиях SQLDescribeCol [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [обнаружение метаданных](../relational-databases/native-client/features/metadata-discovery.md).  
  
 The [SET FMTONLY](/sql/t-sql/statements/set-fmtonly-transact-sql) option for determining the format of a response without actually running the query is replaced with [sp_describe_first_result_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql), [sp_describe_undeclared_parameters &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql), [sys.dm_exec_describe_first_result_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-transact-sql), and [sys.dm_exec_describe_first_result_set_for_object &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-for-object-transact-sql).  
  
### <a name="changes-to-behavior-in-scripting-a-sql-server-agent-task"></a>Изменения в работе скриптов для задач агента SQL Server  
 В [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] при создании нового задания путем копирования скрипта из существующего задания новое задание может непреднамеренно повлиять на существующее. Чтобы создать новое задание с помощью скрипта из существующего задания, вручную удалите параметр *@schedule_uid* которой обычно является последнего параметра в разделе, где создается расписание для существующего задания. При этом для нового задания будет создано независимое расписание, которое не окажет влияния на существующие задания.  
  
### <a name="constant-folding-for-clr-user-defined-functions-and-methods"></a>Свертка констант для определяемых пользователем функций и методов среды CLR  
 В [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] теперь можно сворачивать следующие определяемые пользователем объекты среды CLR:  
  
-   детерминированные, определяемые пользователем функции среды CLR, возвращающие скалярное значение;  
  
-   детерминированные методы определяемых пользователем типов данных CLR.  
  
 Это улучшение должно повысить производительность при многократном вызове этих функций и методов с одинаковыми аргументами. Однако это изменение может приводить к непредвиденным результатам, когда недетерминированные функции или методы были ошибочно отмечены как детерминированные. Детерминированность функции или метода среды CLR задается значением свойства `IsDeterministic` атрибута `SqlFunctionAttribute` или `SqlMethodAttribute`.  
  
### <a name="behavior-of-stenvelope-method-has-changed-with-empty-spatial-types"></a>Изменение работы метода STEnvelope() с пустыми пространственными типами  
 Метод `STEnvelope` с пустыми объектами теперь выполняется так же, как и другие пространственные методы [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 В [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] метод `STEnvelope` при вызове с пустыми объектами возвращал следующие результаты:  
  
```  
select geometry::Parse('POINT EMPTY').STEnvelope().ToString()  
-- returns POINT EMPTY  
select geometry::Parse('LINESTRING EMPTY').STEnvelope().ToString()  
-- returns LINESTRING EMPTY  
select geometry::Parse('POLYGON EMPTY').STEnvelope().ToString()  
-- returns POLYGON EMPTY  
```  
  
 В [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] метод `STEnvelope` при вызове с пустыми объектами возвращает следующие результаты:  
  
```  
select geometry::Parse('POINT EMPTY').STEnvelope().ToString()  
-- returns GEOMETRYCOLLECTION EMPTY  
select geometry::Parse('LINESTRING EMPTY').STEnvelope().ToString()  
-- returns GEOMETRYCOLLECTION EMPTY  
select geometry::Parse('POLYGON EMPTY').STEnvelope().ToString()  
-- returns GEOMETRYCOLLECTION EMPTY  
```  
  
 Чтобы определить, является ли пространственный объект пустым, вызовите [STIsEmpty &#40;тип данных geometry&#41; ](/sql/t-sql/spatial-geometry/stisempty-geometry-data-type) метод.  
  
### <a name="log-function-has-new-optional-parameter"></a>Новый необязательный параметр функции LOG  
 `LOG` Функции теперь имеет необязательный *базового* параметра. Дополнительные сведения см. в разделе [ЖУРНАЛА &#40;Transact-SQL&#41;](/sql/t-sql/functions/log-transact-sql).  
  
### <a name="statistics-computation-during-partitioned-index-operations-has-changed"></a>Изменение статистических вычислений во время операций с секционированным индексом  
 Статистические данные в [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] не создаются путем сканирования всех строк таблицы при создании или перестроении секционированного индекса. Вместо этого оптимизатор запросов использует для создания статистики алгоритм выборки по умолчанию. После обновления базы данных с секционированными индексами можно заметить разницу в гистограммах для этих индексов. Это изменение в поведении может не влиять на время выполнения запросов. Для получения статистики по секционированным индексам путем сканирования всех строк таблицы используйте инструкции CREATE STATISTICS или UPDATE STATISTICS с предложением FULLSCAN.  
  
### <a name="data-type-conversion-by-the-xml-value-method-has-changed"></a>Изменение преобразования типов данных XML-методом value  
 Скрытое поведение метода `value` типа данных `xml` изменилось. Этот метод выполняет запрос XQuery к XML-данным и возвращает скалярное значение указанного типа данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Тип xs необходимо преобразовать в тип данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Прежде метод `value` в скрытом режиме преобразовывал исходное значение в xs:string, а затем xs:string — в тип данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. В [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] преобразование в xs:string опускается для следующих типов:  
  
|Исходный тип данных XS|Целевой тип данных SQL Server|  
|-------------------------|--------------------------------------|  
|byte<br /><br /> short<br /><br /> ssNoversion<br /><br /> integer<br /><br /> long<br /><br /> unsignedByte<br /><br /> unsignedShort<br /><br /> unsignedInt<br /><br /> unsignedLong<br /><br /> positiveInteger<br /><br /> nonPositiveInteger<br /><br /> negativeInteger<br /><br /> nonNegativeInteger|TINYINT<br /><br /> SMALLINT<br /><br /> ssNoversion<br /><br /> BIGINT<br /><br /> Decimal<br /><br /> NUMERIC|  
|Decimal|Decimal<br /><br /> NUMERIC|  
|FLOAT|REAL|  
|double|FLOAT|  
  
 Новые правила повышают производительность, если можно пропустить промежуточное преобразование. Однако при сбое преобразования данных появляются сообщения об ошибке, отличные от тех, которые возникают при преобразовании из промежуточного значения xs:string. Например, если метод value не смог преобразовать значение 100 000 типа `int` в `smallint`, то предыдущее сообщение об ошибке будет выглядеть так:  
  
 `The conversion of the nvarchar value '100000' overflowed an INT2 column. Use a larger integer column.`  
  
 В [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] без промежуточного преобразования в xs:string сообщение об ошибке выглядит следующим образом:  
  
 `Arithmetic overflow error converting expression to data type smallint.`  
  
### <a name="sqlcmdexe-behavior-change-in-xml-mode"></a>Изменение в работе программы sqlcmd.exe в режиме XML  
 Изменилась работа программы sqlcmd.exe в режиме XML (команда :XML ON) при выполнении инструкций SELECT * from T FOR XML…  
  
### <a name="dbcc-checkident-revised-message"></a>Измененное сообщение DBCC CHECKIDENT  
 В [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], сообщение, возвращаемое командой DBCC CHECKIDENT изменилось только при использовании вместе с RESEED *new_reseed_value* изменение текущего значения идентификатора. Новое сообщение «Проверка идентификационных данных: текущее значение идентификатора "\<текущее значение идентификатора >". Выполнение инструкции DBCC завершено. Если инструкция DBCC выдает сообщения об ошибках, обратитесь к системному администратору».  
  
 В более ранних версиях сообщение: «Проверка идентификационных данных: текущее значение идентификатора "\<текущее значение идентификатора >", текущее значение столбца "\<текущее значение столбца >". Выполнение инструкции DBCC завершено. Если инструкция DBCC выдает сообщения об ошибках, обратитесь к системному администратору». Это сообщение не меняется, если команда DBCC CHECKIDENT указана вместе с NORESEED, без второго параметра или без значения для повторного заполнения. Дополнительные сведения см. в разделе [DBCC CHECKIDENT (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-checkident-transact-sql).  
  
### <a name="behavior-of-exist-function-on-xml-datatype-has-changed"></a>Изменилась работа функции exist() типа данных XML  
 Поведение **exist()** функции был изменен при сравнении типа данных XML со значением null, 0 (ноль). Рассмотрим следующий пример:  
  
```xml  
DECLARE @test XML;  
SET @test = null;  
SELECT COUNT(1) WHERE @test.exist('/dogs') = 0;  
```  
  
 В более ранних версиях это сравнение возвращает 1 (true). Теперь это сравнение возвращает значение 0 (нуль, false).  
  
 Не изменились следующие сравнения:  
  
```xml  
DECLARE @test XML;  
SET @test = null;  
SELECT COUNT(1) WHERE @test.exist('/dogs') = 1; -- 0 expected, 0 returned  
SELECT COUNT(1) WHERE @test.exist('/dogs') IS NULL; -- 1 expected, 1 returned  
```  
  
## <a name="see-also"></a>См. также  
 [Критические изменения в функциях ядра СУБД в SQL Server 2014](breaking-changes-to-database-engine-features-in-sql-server-2016.md)   
 [Нерекомендуемые функции ядра СУБД в SQL Server 2014](deprecated-database-engine-features-in-sql-server-2016.md)   
 [Нерекомендуемые функции ядра СУБД в SQL Server 2014](discontinued-database-engine-functionality-in-sql-server-2016.md)   
 [Уровень совместимости инструкции ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)  
  
  
