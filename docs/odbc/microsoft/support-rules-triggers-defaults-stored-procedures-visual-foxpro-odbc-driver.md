---
title: Поддержка правил, триггеров, значений по умолчанию и хранимых процедур | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], stored procedures
- FoxPro ODBC driver [ODBC], commands and functions
- commands for FoxPro ODBC driver [ODBC]
- FoxPro ODBC driver [ODBC], default values
- FoxPro ODBC driver [ODBC], triggers
- stored procedures [ODBC], Visual FoxPro ODBC driver
- Visual FoxPro ODBC driver [ODBC], rules
- FoxPro commands and functions [ODBC]
- rules [ODBC]
- Visual FoxPro ODBC driver [ODBC], default values
- FoxPro ODBC driver [ODBC], rules
- functions [ODBC], Visual FoxPro
- default values [ODBC]
- Visual FoxPro ODBC driver [ODBC], commands and functions
- Visual FoxPro ODBC driver [ODBC], triggers
- FoxPro ODBC driver [ODBC], stored procedures
- Visual FoxPro commands and functions [ODBC]
ms.assetid: e449de20-d6ca-4902-9f8e-814eb6e86650
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a02aeea8f33e3a4d87fc771a7b0fa7b1a0067b6d
ms.sourcegitcommit: 99f61724de5edf6640efd99916d464172eb23f92
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87363364"
---
# <a name="support-for-rules-triggers-default-values-and-stored-procedures-visual-foxpro-odbc-driver"></a>Поддержка правил, триггеров, значений по умолчанию и хранимых процедур (драйвер ODBC для Visual FoxPro)
С помощью драйвера ODBC для Visual FoxPro нельзя создавать правила и триггеры Visual FoxPro, а также значения по умолчанию или хранимые процедуры. Однако приложение может взаимодействовать с существующими правилами, триггерами, значениями по умолчанию или хранимыми процедурами при вставке, обновлении или удалении данных Visual FoxPro, хранящихся в базе данных.  
  
 В следующей таблице перечислены команды и функции Visual FoxPro, поддерживаемые драйвером ODBC для Visual FoxPro при наличии команд или функций в правилах, триггерах, значениях по умолчанию или хранимых процедурах.  
  
 Если приложение взаимодействует с данными, правила, триггеры, значения по умолчанию или хранимые процедуры вызывают любые другие команды или функции Visual FoxPro, драйвер выдает ошибку. Список команд и функций, которые не поддерживаются драйвером, см. в разделе [неподдерживаемые команды и функции Visual FoxPro](../../odbc/microsoft/unsupported-visual-foxpro-commands-and-functions-visual-foxpro-odbc-driver.md) .  
  
> [!TIP]  
>  Если требуется вставить условный код в правила, триггеры или хранимые процедуры, определяющие команды, выполняемые при вызове драйвером, можно использовать функцию **Version ()** . Функция **Version ()** возвращает значение "драйвер ODBC для Visual FoxPro *\<version>* " при вызове драйвером.  
  
## <a name="visual-foxpro-commands-and-functions-supported-in-rules-triggers-default-values-and-stored-procedures"></a>Команды и функции Visual FoxPro, поддерживаемые в правилах, триггерах, значениях по умолчанию и хранимых процедурах  

:::row:::
    :::column:::
        Оператор $  
        Оператор %  
    :::column-end:::
    :::column:::
        Команда &  
        Команда &&   
    :::column-end:::
    :::column:::
        \* Command  
        = Команда  
    :::column-end:::
:::row-end:::

## <a name="a"></a>Объект  

:::row:::
    :::column:::
        Функция ABS ()  
        Функция АКОПИ ()  
        Функция ACOS ()  
        Функция АДАТАБАСЕС ()  
        Функция АДБОБЖЕКТС ()  
        Команда "добавить таблицу"  
        Функция Адель ()  
        Функция АЕЛЕМЕНТ ()  
        Функция АЕРРОР ()  
        Функция АФИЕЛДС ()  
        Функция АИНС ()  
        Функция Ален ()  
        ALIAS ()-функция  
    :::column-end:::
    :::column:::
        Функция АЛЛТРИМ ()  
        ALTER TABLE (команда SQL)  
        Оператор AND  
        Команда APPEND  
        Добавить из команды  
        Команда "Добавить из массива"  
        Команда "Добавить общую"  
        Команда "добавить записок"  
        Команда добавления процедур  
        Функция ASC ()  
        Функция АСКАН ()  
        Функция ASIN ()  
        Функция АСОРТ ()  
    :::column-end:::
    :::column:::
        Функция АСУБСКРИПТ ()  
        Функция AT ()  
        Функция AT_C ()  
        Функция ATAN ()  
        Функция АТК ()  
        Функция АТКК ()  
        Функция АТКЛИНЕ ()  
        Функция АТЛИНЕ ()  
        Функция ATN2 ()  
        Функция АУСЕД ()  
        Команда среднего значения  
    :::column-end:::
:::row-end:::

## <a name="b"></a>B  

:::row:::
    :::column:::
        Команда BEGIN TRANSACTION  
        Функция BETWEEN ()  
        Функция BITAND ()  
        Функция БИТКЛЕАР ()  
        Функция БИТЛШИФТ ()  
    :::column-end:::
    :::column:::
        Функция БИТНОТ ()  
        Функция BITOR ()  
        Функция БИТРШИФТ ()  
        Функция БИТОВОМ массиве ()  
        Функция БИТТЕСТ ()  
    :::column-end:::
    :::column:::
        Функция БИТКСОР ()  
        ПУСТая команда  
        Функция BOF ()  
    :::column-end:::
:::row-end:::

## <a name="c"></a>C  

:::row:::
    :::column:::
        Команда CALCULATE  
        CANDIDATE (), функция  
        Функция КДОВ ()  
        Функция CDX ()  
        Функция CEILING ()  
        Функция CHR ()  
        Функция ЧРТРАН ()  
        Функция ЧРТРАНК ()  
        ЗАКРЫТЬ команды  
        Функция КМОНС ()  
    :::column-end:::
    :::column:::
        Команда "продолжить"  
        Команда "Копировать ИНДЕКСы"  
        Команда копирования процедур  
        Команда "копировать структуру"  
        Команда копирования структуры EXTENDED  
        Команда "Копировать тег"  
        Команда "Копировать в"  
        Команда "Копировать в массив"  
        COS (), функция  
        COUNT, команда  
    :::column-end:::
    :::column:::
        Функция КПКОНВЕРТ ()  
        Функция КПКУРРЕНТ ()  
        Функция КПДБФ ()  
        Функция КТОД ()  
        Функция КТОТ ()  
        Функция КУРСОРЖЕТПРОП ()  
        Функция КУРСОРСЕТПРОП ()  
        Функция КРИВЫХ ()  
    :::column-end:::
:::row-end:::

## <a name="d"></a>D  

:::row:::
    :::column:::
        Функция DATE ()  
        DATETIME (), функция  
        DAY (), функция  
        DBC (), функция  
        Функция DBF ()  
        Функция ДБЖЕТПРОП ()  
        Функция ДБУСЕД ()  
        DELETE (команда SQL)  
    :::column-end:::
    :::column:::
        УДАЛИТЬ команду  
        Команда DELETE TAG  
        DELETEd (), функция  
        Функция Descending ()  
        DIFFERENCE (), функция  
        ИЗМЕРЕНИЕ, команда  
        Функция места ()  
        Функция DMY ()  
    :::column-end:::
    :::column:::
        DO, команда  
        УЧИТЫВАТЬ РЕГИСТР... Команда ЕНДКАСЕ  
        ВЫПОЛНЯТЬ ВО ВРЕМЯ... Команда ЕНДДО  
        Функция DOW ()  
        Функция ДТОК ()  
        Функция DTOR ()  
        Функция DTO ()  
        Функция ДТОТ ()  
    :::column-end:::
:::row-end:::

## <a name="e"></a>E  

:::row:::
    :::column:::
        ПУСТая функция ()  
        Команда завершения транзакции  
        Функция EOF ()  
    :::column-end:::
    :::column:::
        ERROR (), функция  
        Функция EVALUATE ()  
        EXIT, команда  
    :::column-end:::
    :::column:::
        Функция EXP ()  
    :::column-end:::
:::row-end:::

## <a name="f"></a>F  

:::row:::
    :::column:::
        Функция ФКАУНТ ()  
        Функция ФДАТЕ ()  
        FIELD (), функция  
        FILE (), функция  
        FILTER (), функция  
        Функция ФЛДЛИСТ ()  
    :::column-end:::
    :::column:::
        Функция ФЛОКК ()  
        Функция FLOOR ()  
        Команда FLUSH  
        ДЛЯ функции ()  
        ДЛЯ... Команда ЕНДФОР  
        Функция FOUND ()  
    :::column-end:::
    :::column:::
        Команда "СВОБОДная таблица"  
        Функция FSIZE ()  
        Функция ФТИМЕ ()  
        Функция FULLPATH ()  
        Команда функции  
        FV ()-функция  
    :::column-end:::
:::row-end:::

## <a name="g"></a>G  

:::row:::
    :::column:::
        Команда "собрать"  
        Функция ЖЕТКП ()  
        Функция GETENV ()  
    :::column-end:::
    :::column:::
        Функция ЖЕТФЛДСТАТЕ ()  
        Функция ЖЕТНЕКСТМОДИФИЕД ()  
        Команда GO/GOTO  
    :::column-end:::
    :::column:::
        Функция ГОМОНС ()  
    :::column-end:::
:::row-end:::

## <a name="h"></a>H  

:::row:::
    :::column:::
        HEADER (), функция
    :::column-end:::
    :::column:::
        HOUR (), функция
    :::column-end:::
:::row-end:::

## <a name="i"></a>I  

:::row:::
    :::column:::
        Функция ИДКСКОЛЛАТЕ ()  
        ЕСЛИ... ENDIF, команда  
        Функция IIF ()  
        Функция ИНДБК ()  
        Команда INDEX  
        Функция LIST ()  
    :::column-end:::
    :::column:::
        Команда INSERT-SQL  
        Функция INT ()  
        Функция-альфа ()  
        Функция onblank ()  
        Функция "DIGIT ()"  
        Функция EXCLUSIVE ()  
    :::column-end:::
    :::column:::
        Функция ИСЛЕАДБИТЕ ()  
        Функция LOWER ()  
        Функция ISNULL ()  
        Функция ISREADONLY ()  
        Функция UPPER ()  
    :::column-end:::
:::row-end:::

## <a name="k"></a>K  

:::row:::
    :::column:::
        KEY (), функция
    :::column-end:::
    :::column:::
        Функция КЭЙМАТЧ ()
    :::column-end:::
:::row-end:::

## <a name="l"></a>L  

:::row:::
    :::column:::
        Функция LEFT ()  
        Функция ЛЕФТК ()  
        LEN (), функция  
        Функция ТРОЯНСКАЯ LENC ()  
        Функция LIKE ()  
        Функция ЛИКЕК ()  
    :::column-end:::
    :::column:::
        ЛОКАЛЬная команда  
        Команда "выбрать"  
        LOCK (), функция  
        LOG (), функция  
        Функция LOG10 ()  
        LOOKUP (), функция  
    :::column-end:::
    :::column:::
        Функция LOWER ()  
        Команда ЛПАРАМЕТЕРС  
        Функция LTRIM ()  
        Функция ЛУПДАТЕ ()  
    :::column-end:::
:::row-end:::

## <a name="m"></a>M  

:::row:::
    :::column:::
        Функция MAX ()  
        Функция MDX ()  
        Функция MDY ()  
        Функция МЕМЛИНЕС ()  
    :::column-end:::
    :::column:::
        MESSAGE (), функция  
        MIN (), функция  
        Функция MINUTE ()  
        _MLINE переменная системной памяти  
    :::column-end:::
    :::column:::
        Функция МЛИНЕ ()  
        Функция MOD ()  
        MONTH (), функция  
        Функция МТОН ()  
    :::column-end:::
:::row-end:::

## <a name="n"></a>N  

:::row:::
    :::column:::
        Функция НДКС ()  
        Функция НОРМАЛИЗАЦИи ()  
    :::column-end:::
    :::column:::
        Оператор NOT  
        Примечание, команда  
    :::column-end:::
    :::column:::
        Функция НТОМ ()  
        Функция НВЛ ()  
    :::column-end:::
:::row-end:::

## <a name="o"></a>O  

:::row:::
    :::column:::
        Функция имеет ()  
        Функция ОЛДВАЛ ()  
        Функция ON ()  
    :::column-end:::
    :::column:::
        ON ERROR, команда  
        ON KEY, команда  
        Команда OPEN DATABASE  
    :::column-end:::
    :::column:::
        Оператор OR  
        ORDER (), функция  
        Функция OS ()  
    :::column-end:::
:::row-end:::

## <a name="p"></a>P  

:::row:::
    :::column:::
        Команда PACK  
        Функции ПАДЛ () &#124; ПАДР () &#124; ПАДК ()  
        Команда PARAMETERS  
        PARAMETERS ()-функция  
        Функция PAYMENT ()  
    :::column-end:::
    :::column:::
        Функция PI ()  
        Функция PRIMARY ()  
        Частная команда  
        Команда процедуры  
        Функция PROGRAM ()  
    :::column-end:::
    :::column:::
        ПРАВИЛЬНая функция ()  
        ОТКРЫТАЯ команда  
        Функция ПС ()  
    :::column-end:::
:::row-end:::

## <a name="r"></a>R  

:::row:::
    :::column:::
        Функция RAND ()  
        RAT ()-функция  
        Функция РАТК ()  
        Функция РАТЛИНЕ ()  
        ОТОЗВАТЬ команду  
        Функция РЕККАУНТ ()  
        Функция РЕКНО ()  
        Функция РЕКСИЗЕ ()  
    :::column-end:::
    :::column:::
        РЕГИОНАЛЬная команда  
        Функция RELATION ()  
        Команда "удалить таблицу"  
        Команда замены  
        Команда "заменить из массива"  
        Функция REPLICATE ()  
        Команда "повторить"  
        ВЕРНУТЬ команду  
    :::column-end:::
    :::column:::
        Функция RIGHT ()  
        Функция РИГХТК ()  
        Функция РЛОКК ()  
        Команда ROLLBACK  
        Функция ROUND ()  
        Функция РТОД ()  
        Функция RTRIM ()  
    :::column-end:::
:::row-end:::

## <a name="s"></a>S  

:::row:::
    :::column:::
        СКАНИРОВАТЬ... Команда ЕНДСКАН  
        ТОЧЕЧная команда  
        SEC (), функция  
        Функция SECONDs ()  
        SEEK, команда  
        SEEK (), функция  
        ВЫБРАТЬ команду  
        Функция SELECT ()  
        Команда SELECT-SQL  
        Функция SET ()  
        Команда SET BLOCKSIZE  
        ЗАДАТЬ выполнение команды  
        Команда SET век  
        Команда SET COLLATE  
        Команда SET DATABASE  
        Команда "задать дату"  
        ЗАДАТЬ команду по УМОЛЧАНИю  
        Команда SET DELETED  
        Команда SET EXACT  
        Команда SET EXCLUSIVE  
        Команда SET ФДОВ  
    :::column-end:::
    :::column:::
        Команда "задать поля"  
        Команда "задать фильтр"  
        Команда SET FIXED  
        Команда SET FULLPATH  
        Команда SET ФВИК  
        Команда "задать часы"  
        Команда задания индекса  
        Команда SET LOCK  
        Команда "задать многоблокировки"  
        ЗАДАТЬ БЛИЖАЙШую команду  
        Команда SET НОКПТРАНС  
        Команда SET NOTIFY  
        Команда SET NULL  
        Команда "задать ОПТИМИЗАЦИю"  
        Команда SET ORDER  
        Команда SET PATH  
        Команда SET PROCEDURE  
        Команда «задать отношение»  
        Команда «задать отношение OFF»  
        Команда SET REPROCESS  
        Команда "задать пропуск"  
    :::column-end:::
    :::column:::
        Команда SET УДФПАРМС  
        Команда SET UNIQUE  
        Команда "задать том"  
        Функция СЕТФЛДСТАТЕ ()  
        SIGN (), функция  
        Функция SIN ()  
        ПРОПУСТИТЬ команду  
        Команда SORT  
        Функция SPACE ()  
        Функция SQRT ()  
        СОХРАНИТЬ команду  
        STR (), функция  
        STRCONV (), функция  
        Функция СТРТРАН ()  
        Функция "ПРОЧее" ()  
        Функция СТУФФК ()  
        Функция substr ()  
        Функция СУБСТРК ()  
        SUM, команда  
        Функция SYS (2011)  
    :::column-end:::
:::row-end:::

## <a name="t"></a>T  

:::row:::
    :::column:::
        Функция ТАБЛЕРЕВЕРТ ()  
        Функция ТАБЛЕУПДАТЕ ()  
        TAG (), функция  
        Функция ТАГКАУНТ ()  
        Функция ТАГНО ()  
        _TALLY переменная системной памяти  
    :::column-end:::
    :::column:::
        Функция TAN ()  
        TARGET ()-функция  
        TIME (), функция  
        Команда "всего"  
        _TRIGGERLEVEL переменная системной памяти  
        TRIM (), функция  
    :::column-end:::
    :::column:::
        Функция ТТОК ()  
        Функция ТТОД ()  
        Функция ТКСНЛЕВЕЛ ()  
        TYPE (), функция  
    :::column-end:::
:::row-end:::

## <a name="u"></a>U  

:::row:::
    :::column:::
        Функция UNIQUE ()  
        Команда UNLOCK  
        Команда обновления  
    :::column-end:::
    :::column:::
        UPDATE (команда SQL)  
        Функция UPPER ()  
        Команда USE  
    :::column-end:::
    :::column:::
        USED ()-функция  
    :::column-end:::
:::row-end:::

## <a name="v"></a>V  

:::row:::
    :::column:::
        VAL ()-функция
    :::column-end:::
    :::column:::
        VERSION (), функция
    :::column-end:::
:::row-end:::

## <a name="w"></a>W  

WEEK (), функция

## <a name="y"></a>Да  

YEAR (), функция

## <a name="z"></a>Z  

ZAP, команда
