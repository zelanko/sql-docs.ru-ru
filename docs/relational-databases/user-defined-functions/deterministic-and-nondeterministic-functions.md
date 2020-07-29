---
title: Детерминированные и недетерминированные функции | Документация Майкрософт
ms.custom: ''
ms.date: 08/26/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- built-in functions [SQL Server]
- nondeterministic functions
- extended stored procedures [SQL Server], functions that call
- deterministic functions
- user-defined functions [SQL Server], deterministic
ms.assetid: 2f3ce5f5-c81c-4470-8141-8144d4f218dd
author: rothja
ms.author: jroth
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7df37d9b9339ef98e438e15678c0781df2875a18
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87247267"
---
# <a name="deterministic-and-nondeterministic-functions"></a>Детерминированные и недетерминированные функции
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Детерминированные функции каждый раз возвращают один и тот же результат, если предоставлять им один и тот же набор входных значений и использовать одно и то же состояние базы данных. Недетерминированные функции могут возвращать каждый раз разные результаты, даже если предоставлять им один и тот же набор входных значений и использовать одно и то же состояние базы данных. Например, функция AVG всегда возвращает один результат при указанных выше условиях, а функция GETDATE, возвращающая текущие дату и время, всегда возвращает разный результат.  
  
 Определяемые пользователями функции имеют несколько свойств, определяющих способность ядра [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] индексировать результаты функции как с помощью индексов вычисляемых столбцов, вызывающих функцию, так и с помощью индексированных представлений, которые на нее ссылаются. Детерминизм функции — одно из таких свойств. Например, в представлении нельзя создать кластеризованный индекс, если оно ссылается на какие-либо недетерминированные функции. Дополнительные сведения о свойствах функций, включая детерминизм, см. в разделе [Определяемые пользователем функции](../../relational-databases/user-defined-functions/user-defined-functions.md).  
  
 В этом разделе описан детерминизм встроенных системных функций и их влияние на свойство детерминированности определяемых пользователем функций, если оно содержит вызов расширенных хранимых процедур.  
  
## <a name="built-in-function-determinism"></a>Детерминизм встроенных функций  
 На детерминизм встроенных функций повлиять нельзя. Каждая из них детерминирована или недетерминирована в зависимости от реализации в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Например, если вы укажете в запросе предложение ORDER BY, детерминизм функции, используемой в этом запросе, не изменится.  
  
 Все встроенные строковые функции являются детерминированными, кроме [FORMAT](../../t-sql/functions/format-transact-sql.md). Список этих функций см. в разделе [Строковые функции (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md).  
  
 Следующие встроенные функции, отличные от строковых функций, всегда детерминированы.  
  
:::row:::
    :::column:::
        ABS
    :::column-end:::
    :::column:::
        DATEDIFF
    :::column-end:::
    :::column:::
        POWER
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        ACOS
    :::column-end:::
    :::column:::
        DAY
    :::column-end:::
    :::column:::
        RADIANS
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        ASIN
    :::column-end:::
    :::column:::
        DEGREES
    :::column-end:::
    :::column:::
        ROUND
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        ATAN
    :::column-end:::
    :::column:::
        EXP
    :::column-end:::
    :::column:::
        SIGN
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        ATN2
    :::column-end:::
    :::column:::
        FLOOR
    :::column-end:::
    :::column:::
        SIN
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CEILING
    :::column-end:::
    :::column:::
        ISNULL
    :::column-end:::
    :::column:::
        SQUARE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        COALESCE
    :::column-end:::
    :::column:::
        ISNUMERIC
    :::column-end:::
    :::column:::
        SQRT
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        COS
    :::column-end:::
    :::column:::
        LOG
    :::column-end:::
    :::column:::
        TAN
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        COT
    :::column-end:::
    :::column:::
        LOG10
    :::column-end:::
    :::column:::
        YEAR
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        DATALENGTH
    :::column-end:::
    :::column:::
        MONTH
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        DATEADD
    :::column-end:::
    :::column:::
        NULLIF
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::
 
 Следующие функции не всегда детерминированы, их можно использовать в индексированных представлениях или индексах вычисляемых столбцов, если они заданы детерминированным образом.  
  
|Компонент|Комментарии|  
|--------------|--------------|  
|все агрегатные функции|Все агрегатные функции являются детерминированными, если они не указаны с помощью предложения OVER или ORDER BY. Список этих функций см. в разделе [Агрегатные функции (Transact-SQL)](../../t-sql/functions/aggregate-functions-transact-sql.md).|  
|CAST|Детерминированные, за исключением использования их с данными типа **datetime**, **smalldatetime**и **sql_variant**.|  
|CONVERT|Детерминирована, кроме следующих случаев.<br /><br /> <br /><br /> Тип источника — **sql_variant**.<br /><br /> Конечный тип — **sql_variant** , и его исходный тип недетерминирован.<br /><br /> Исходный или конечный тип — **datetime** или **smalldatetime**, другой исходный или конечный тип — строка символов, и задан недетерминированный стиль. Чтобы быть детерминированным, параметр стиля должен быть константой. Кроме того, стили, которые меньше или равны 100, являются недетерминированными, за исключением стилей 20 и 21. Стили более 100 являются детерминированными, за исключением стилей 106, 107, 109 и 113.|  
|CHECKSUM|Детерминирована, за исключением CHECKSUM(*).|  
|ISDATE|Детерминирована, только если используется с функцией CONVERT, при этом параметр стиля CONVERT задан, но не равен 0, 100, 9 или 109.|  
|RAND|Функция RAND детерминирована, только если параметр *seed* определен.|  
  
 Все функции конфигурации, курсора, метаданных, безопасности и системные статистические — недетерминированные. Список этих функций см. в разделе [Функции конфигурации (Transact-SQL)](../../t-sql/functions/configuration-functions-transact-sql.md), [Функции работы с курсорами (Transact-SQL)](../../t-sql/functions/cursor-functions-transact-sql.md), [Функции метаданных (Transact-SQL)](../../t-sql/functions/metadata-functions-transact-sql.md), [Функции безопасности (Transact-SQL)](../../t-sql/functions/security-functions-transact-sql.md) и [Системные статистические функции (Transact-SQL)](../../t-sql/functions/system-statistical-functions-transact-sql.md).  
  
 Следующие встроенные функции других классов всегда недетерминированы.  
  
:::row:::
    :::column:::
        @@CONNECTIONS
    :::column-end:::
    :::column:::
        GETDATE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        @@CPU_BUSY
    :::column-end:::
    :::column:::
        GETUTCDATE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        @@DBTS
    :::column-end:::
    :::column:::
        GET_TRANSMISSION_STATUS
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        @@IDLE
    :::column-end:::
    :::column:::
        LAG
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        @@IO_BUSY
    :::column-end:::
    :::column:::
        LAST_VALUE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        @@MAX_CONNECTIONS
    :::column-end:::
    :::column:::
        LEAD
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        @@PACK_RECEIVED
    :::column-end:::
    :::column:::
        MIN_ACTIVE_ROWVERSION
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        @@PACK_SENT
    :::column-end:::
    :::column:::
        NEWID
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        @@PACKET_ERRORS
    :::column-end:::
    :::column:::
        NEWSEQUENTIALID
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        @@TIMETICKS
    :::column-end:::
    :::column:::
        NEXT VALUE FOR
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        @@TOTAL_ERRORS
    :::column-end:::
    :::column:::
        NTILE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        @@TOTAL_READ
    :::column-end:::
    :::column:::
        PARSENAME
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        @@TOTAL_WRITE
    :::column-end:::
    :::column:::
        PERCENTILE_CONT
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        AT TIME ZONE
    :::column-end:::
    :::column:::
        PERCENTILE_DISC
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        CUME_DIST
    :::column-end:::
    :::column:::
        PERCENT_RANK
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CURRENT_TIMESTAMP
    :::column-end:::
    :::column:::
        RAND
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        DENSE_RANK
    :::column-end:::
    :::column:::
        RANK
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        FIRST_VALUE
    :::column-end:::
    :::column:::
        ROW_NUMBER
    :::column-end:::
:::row-end:::   
:::row:::
    :::column:::
        FORMAT
    :::column-end:::
    :::column:::
        TEXTPTR
    :::column-end:::
:::row-end:::
 
## <a name="calling-extended-stored-procedures-from-functions"></a>Вызов расширенной хранимой процедуры из функций  
 Функции, вызывающие расширенные хранимые процедуры, недетерминированы, так как расширенные хранимые процедуры могут оказать на базу данных побочное действие. Побочные действия — это такое изменение глобального состояния базы данных, как обновление таблицы, внешнего сетевого ресурса или файла. Например, к таким действиям можно отнести изменение файла или отправку сообщения по электронной почте. При выполнении расширенной хранимой процедуры из пользовательской функции не следует полагаться на то, что будет возвращен непротиворечивый результирующий набор. Не рекомендуется применять пользовательские функции, которые оказывают побочное действие на базу данных.  
  
 При вызове из функции расширенные хранимые процедуры не могут вернуть клиенту результирующий набор. API-интерфейс любых открытых служб данных, который возвращает результирующие наборы клиенту, имеет код возврата FAIL.  
  
 Расширенная хранимая процедура может подключиться обратно к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Однако процедура не может соединиться с той же транзакцией, что и первоначальная функция, которая вызвала расширенную хранимую процедуру.  
  
 Как и при вызове из пакета или хранимой процедуры, расширенная хранимая процедура выполняется в контексте той учетной записи [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, под которой запущен [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Владелец расширенной хранимой процедуры должен учитывать разрешения в контексте безопасности при предоставлении разрешения на выполнение этой процедуры другим пользователям.  
  
  
