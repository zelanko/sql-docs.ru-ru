---
title: Поддержка правил, триггеров, значений по умолчанию и сохраненных процедур Документы Майкрософт
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
ms.openlocfilehash: 2fcf8e7c80b2712313cba81199489dc7cb06dce0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301141"
---
# <a name="support-for-rules-triggers-default-values-and-stored-procedures-visual-foxpro-odbc-driver"></a>Поддержка правил, триггеров, значений по умолчанию и хранимых процедур (драйвер ODBC для Visual FoxPro)
Вы не можете создавать правила Visual FoxPro, триггеры, значения по умолчанию или сохраненные процедуры с помощью Visual FoxPro ODBC Driver. Однако приложение может взаимодействовать с существующими правилами, триггерами, значениями по умолчанию или сохраненными процедурами при вставке, обновлении или удалении данных Visual FoxPro, хранящихся в базе данных.  
  
 В следующей таблице перечислены команды и функции Visual FoxPro, поддерживаемые Драйвером Visual FoxPro ODBC, когда команды или функции существуют в правилах, триггерах, значениях по умолчанию или сохраненных процедурах.  
  
 Если приложение взаимодействует с данными, правила которых, триггеры, значения по умолчанию или сохраненные процедуры вызывают любые другие команды или функции Visual FoxPro, драйвер генерирует ошибку. Смотрите [неподдерживаемые команды и функции Visual FoxPro](../../odbc/microsoft/unsupported-visual-foxpro-commands-and-functions-visual-foxpro-odbc-driver.md) для списка команд и функций, не поддерживаемых драйвером.  
  
> [!TIP]  
>  Если вы хотите вставить условный код в правила, триггеры или сохраненные процедуры, определяющие команды для выполнения при вызове драйвером, можно использовать функцию **VERSION.** **Версия()** функция возвращает "Visual FoxPro * \< *ODBC Driver версия>", когда называется драйвером.  
  
## <a name="visual-foxpro-commands-and-functions-supported-in-rules-triggers-default-values-and-stored-procedures"></a>Визуальные команды и функции FoxPro, поддерживаемые в правилах, триггерах, значениях по умолчанию и процедурах хранения  
  
||||  
|-|-|-|  
|$ Оператор|Оператор %|Командование &|  
|Командование && |- Командование|- Командование|  
  
## <a name="a"></a>Объект  
  
||||  
|-|-|-|  
|ABS() Функция|ACOPY () Функция|Команда ADD TABLE|  
|ADATABASES() Функция|ADBOBJECTS() Функция|AERROR() Функция|  
|ADEL() Функция|AELEMENT() Функция|ALEN() Функция|  
|AFIELDS () Функция|AINS() Функция|ALTER TABLE (команда SQL)|  
|ALIAS () Функция|ALLTRIM( ) Функция|APPEND ОТ КОМАНДЫ МАССИВА|  
|И Оператор|Командование APPEND|Командование APPEND MEMO|  
|ПРИЛОЖЕНИЕ от командования|Командование APPEND GENERAL|ASCAN() Функция|  
|Команда APPEND PROCEDURES|ASC() Функция|ASUBSCRIPT( ) Функция|  
|ASIN() Функция|ASORT () Функция|ATAN( ) Функция|  
|AT() Функция|AT_C() Функция|ATCLINE() Функция|  
|УВД() Функция|AtCC( ) Функция|AUSED () Функция|  
|Atline( ) Функция|ATN2( ) Функция||  
|Командование AVERAGE|ACOS() Функция||  
  
## <a name="b"></a>B  
  
||||  
|-|-|-|  
|КОМАНДование ИНИНЕНДОНЛ|BETWEEN( ) Функция|БИТНОТ () Функция|  
|BITCLEAR () Функция|BITLSHIFT() Функция|BITSET ( ) Функция|  
|BITOR () Функция|BITRSHIFT() Функция|Командование BLANK|  
|BITTEST () Функция|BITXOR () Функция||  
|BOF() Функция|BITAND() Функция||  
  
## <a name="c"></a>C  
  
||||  
|-|-|-|  
|Командование CALCULATE|КАНДИДАТЕ() Функция|CHR() Функция|  
|CDX() Функция|CEILING( ) Функция|Команды CLOSE|  
|CHRTRAN () Функция|CHRTRANC () Функция|Командование COPY INDEXES|  
|CMONTH() Функция|КОМАНДА CONTINUE|COPY STRUCTURE EXTENDED Командование|  
|Copy PROCEDURES Командование|Командование COPY STRUCTURE|КОПИРОВАНИЕ КОМАНДЫ TO|  
|Командование COPY TAG|КопированиЕ КОМАНДЫ МАССИВА TO|CPCONVERT( ) Функция|  
|COS() Функция|Команда СОНТ|CTOD() Функция|  
|CPCURRENT() Функция|CPDBF() Функция|CURSORSETPROP( ) Функция|  
|CTOT() Функция|CURSORGETPROP( ) Функция||  
|CURVAL ( ) Функция|CDOW () Функция||  
  
## <a name="d"></a>D  
  
||||  
|-|-|-|  
|DATE ( ) Функция|DATETIME () Функция|ДНЯ() Функция|  
|DBC() Функция|DBF() Функция|DBGETPROP() Функция|  
|DBUSED() Функция|DELETE (команда SQL)|Командование DELETE|  
|Команда DELETE TAG|DELETED( ) Функция|СОНТОНИНГ() Функция|  
|СИПРИЕСИЯ() Функция|Командование DIMENSION|DISKSPACE( ) Функция|  
|DMY() Функция|ДЕЛАТЬ случае ... Команда ENDCASE|Командование DO|  
|ДЕЛАЙТЕ ТО ВРЕМЯ как ... Команда ENDDO|DOW() Функция|DTOC() Функция|  
|DTOR() Функция|DTOS() Функция|DTOT() Функция|  
  
## <a name="e"></a>E  
  
||||  
|-|-|-|  
|EMPTY() Функция|ОЦЕНКА() Функция|Команда EXIT|  
|ERROR( ) Функция|EXP() Функция||  
|End TRANSACTION Команда|EOF() Функция||  
  
## <a name="f"></a>F  
  
||||  
|-|-|-|  
|FCOUNT () Функция|FDATE() Функция|ФИЛЕС() Функция|  
|FILE() Функция|FILTER( ) Функция|FLDLIST() Функция|  
|FLOCK( ) Функция|FLOOR( ) Функция|Командование FLUSH|  
|Для... Командование ЭНДФОР|ДЛЯ() Функция|FOUND() Функция|  
|БЕСПЛАТНО TABLE Команды|ФИЗЕ() Функция|FTIME () Функция|  
|FullPATH() Функция|FUNCTION Command|FV() Функция|  
  
## <a name="g"></a>G.  
  
||||  
|-|-|-|  
|Командование GATHER|GETNEXTMODIFIED( ) Функция|Командование GO/GOTO|  
|GETFLDSTATE() Функция|GOMONTH() Функция||  
|GETCP() Функция|GETENV() Функция||  
  
## <a name="h"></a>H  
  
|||  
|-|-|  
|HEADER() Функция|ЧАС() Функция|  
  
## <a name="i"></a>I  
  
||||  
|-|-|-|  
|IDXCOLLATE ( ) Функция|Если... Командование ENDIF|IIF() Функция|  
|INDBC() Функция|Команда INDEX|INlist() Функция|  
|Командование INSERT-S'L|INT() Функция|ISALPHA() Функция|  
|ISBLANK () Функция|ISDIGIT() Функция|ISEXCLUSIVE () Функция|  
|ISLEADBYTE( ) Функция|ISLOWER() Функция|ISNULL() Функция|  
|ИСРЕДЕЛОЛо() Функция|ISUPPER () Функция||  
  
## <a name="k"></a>K  
  
||||  
|-|-|-|  
|KEY() Функция|KEYMATCH( ) Функция||  
  
## <a name="l"></a>L  
  
||||  
|-|-|-|  
|LEFT() Функция|LEFTC() Функция|LIKEC() Функция|  
|LENC ( ) Функция|LIKE() Функция|ЛОКК() Функция|  
|Командование LOCAL|Команда LOCATE|LOOKUP ( ) Функция|  
|ЛОГ() Функция|LOG10() Функция|LTRIM() Функция|  
|LOWER() Функция|Командование LPARAMETERS||  
|LUPDATE() Функция|LEN( ) Функция||  
  
## <a name="m"></a>M  
  
||||  
|-|-|-|  
|_MLINE системы памяти Переменный|MAX( ) Функция|MDX() Функция|  
|MDY() Функция|MEMLINES( ) Функция|MESSAGE( ) Функция|  
|MIN() Функция|MINUTE( ) Функция|MLINE() Функция|  
|МОД() Функция|MONTH() Функция|MTON() Функция|  
  
## <a name="n"></a>Нет  
  
||||  
|-|-|-|  
|NDX() Функция|НОРМИЗЕИЯ() Функция|НЕ Оператор|  
|КОМАНДА ПРИМЕЧАНИЕ|NTOM() Функция|NVL() Функция|  
  
## <a name="o"></a>O  
  
||||  
|-|-|-|  
|ПРОИСХОДИТ() Функция|OLDVAL ( ) Функция|Команда НА ERROR|  
|Команда НА КИЕ|ON() Функция|Команда OPEN DATABASE|  
|Или Оператор|ORDER( ) Функция|ОС() Функция|  
  
## <a name="p"></a>P  
  
||||  
|-|-|-|  
|Командование ПАК|ПАРАМЕТРЕС() Функция|ПЛАЕВИЯ() Функция|  
|Команда PARAMETERS|PRIMARY( ) Функция|Командование PRIVATE|  
|PI() Функция|PROGRAM( ) Функция|PROPER() Функция|  
|Команда ПРОЦЕДУР|П.в. () Функция||  
|Public Командование|PADL( ) &#124; PADR( ) &#124; PADC( ) Функции||  
  
## <a name="r"></a>R  
  
||||  
|-|-|-|  
|RAND() Функция|RAT() Функция|RATC() Функция|  
|RATLINE( ) Функция|Команда RECALL|RECCOUNT () Функция|  
|RECNO () Функция|ВЫсоцизе () Функция|Командование РЕГИОНЕ|  
|RELATION( ) Функция|Команда REMOVE TABLE|Командование REPLACE|  
|ЗАМЕНА ИЗ КОМАНДЫ ARRAY|REPLICATE( ) Функция|Командование RETRY|  
|Команда RETURN|RIGHT() Функция|RIGHTC() Функция|  
|RLOCK() Функция|Командование ROLLBACK|ROUND() Функция|  
|RTOD() Функция|RTRIM( ) Функция||  
  
## <a name="s"></a>S  
  
||||  
|-|-|-|  
|Сканирования... Командование ENDSCAN|Командование SCATTER|SEC() Функция|  
|SECONDS( ) Функция|Команда SEEK|SEEK() Функция|  
|Командование SELECT|SELECT() Функция|Командование SELECT-S'L|  
|Команда SET BLOCKSIZE|Команда SET CARRY|Командование SET CENTURY|  
|Команда SET COLLATE|Командование SET DATABASE|Команда SET DATE|  
|Командование SET DEFAULT|Команда SET DELETED|Команда SET EXACT|  
|Команда SET EXCLUSIVE|Командование SET FDOW|Командование SET FIELDS|  
|Командование SET FILTER|Командование SET FIXED|Set FULLPATH Командование|  
|Командование SET FWEEK|Командование SET HOURS|Командование SET INDEX|  
|Команда SET LOCK|Командование SET MULTILOCKS|Командование SET NEAR|  
|Командование SET NOCPTRANS|Командование SET NOTIFY|Команда SET NULL|  
|Командование SET OPTIMIZE|Командование SET ORDER|Команда SET PATH|  
|Команда SET PROCEDURE|Команда SET RELATION|КОМАНДА SET RELATION OFF|  
|Команда SET REPROCESS|Команда SET SKIP|Командование SET UDFPARMS|  
|Команда SET UNIQUE|Командование SET VOLUME|SET() Функция|  
|SETFLDSTATE() Функция|SIGN ( ) Функция|SIN() Функция|  
|Командование SKIP|Команда SORT|SPACE( ) Функция|  
|СКЗРТ () Функция|Командование STORE|STR( ) Функция|  
|STRCONV () Функция|STRTRAN () Функция|STUFF( ) Функция|  
|STUFFC( ) Функция|SUBSTR( ) Функция|SUBSTRC( ) Функция|  
|Командование СУМ|SYS (2011) Функция||  
  
## <a name="t"></a>T  
  
||||  
|-|-|-|  
|_TALLY системная память переменная|_TRIGGERLEVEL системы памяти Переменный|TAGCOUNT () Функция|  
|TABLEUPDATE () Функция|TAG() Функция|ТАРГЕТ() Функция|  
|TAGNO () Функция|TAN() Функция|TRIM( ) Функция|  
|ВРЕМЯ() Функция|Командование TOTAL|TXNLEVEL ( ) Функция|  
|TTOC() Функция|TTOD() Функция||  
|TYPE( ) Функция|TABLEREVERT( ) Функция||  
  
## <a name="u"></a>U  
  
||||  
|-|-|-|  
|УНИКЕ() Функция|Командование РАЗГИНАТ|Командование USE|  
|ОБНОВЛЕНИЕ Командование|UPPER( ) Функция||  
|USED() Функция|UPDATE (команда SQL)||  
  
## <a name="v"></a>V  
  
||||  
|-|-|-|  
|VAL() Функция|ВЕРСИЯ() Функция||  
  
## <a name="w"></a>W  
  
||||  
|-|-|-|  
|WEEK() Функция|||  
  
## <a name="y"></a>Да  
  
||||  
|-|-|-|  
|ГОДА() Функция|||  
  
## <a name="z"></a>Z  
  
||||  
|-|-|-|  
|Командование ЗАП|||
