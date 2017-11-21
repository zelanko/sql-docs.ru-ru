---
title: "CAST и CONVERT (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 09/08/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CAST_TSQL
- CONVERT_TSQL
- CAST
- CONVERT
dev_langs:
- TSQL
helpviewer_keywords:
- CAST function
- automatic data type conversion
- varbinary data type
- CONVERT function
- data types [SQL Server], converting
- large value data types
- implicit data type conversions
- image data type, converting
- explicit data type conversions [SQL Server]
- binary [SQL Server], converting
- text data type, converting
- date and time [SQL Server], cast and convert
- truncating conversions
- converting data types [SQL Server], conversion functions
- time zones [SQL Server]
- roundtrip conversions
ms.assetid: a87d0850-c670-4720-9ad5-6f5a22343ea8
caps.latest.revision: 136
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: b7f2f78bbda485de979c76076404f35122b61277
ms.contentlocale: ru-ru
ms.lasthandoff: 10/17/2017

---
# <a name="cast-and-convert-transact-sql"></a>Функции CAST и CONVERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Преобразует выражение одного типа данных в другой.  
Например следующие примеры изменить входным типом данных в двух других типов данных, с разными уровнями точности.
```sql  
SELECT 9.5 AS Original, CAST(9.5 AS int) AS int, 
    CAST(9.5 AS decimal(6,4)) AS decimal;
SELECT 9.5 AS Original, CONVERT(int, 9.5) AS int, 
    CONVERT(decimal(6,4), 9.5) AS decimal;
```  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
|Исходный текст   |int    |decimal |  
|----|----|----|  
|9.5 |9 |9.5000 |  

> [!TIP]
> Многие [примеры](#BKMK_examples) в нижней части этого раздела.  
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
-- Syntax for CAST:  
CAST ( expression AS data_type [ ( length ) ] )  
  
-- Syntax for CONVERT:  
CONVERT ( data_type [ ( length ) ] , expression [ , style ] )  
```  
  
## <a name="arguments"></a>Аргументы  
*expression*  
Любое допустимое [выражение](../../t-sql/language-elements/expressions-transact-sql.md).
  
*Тип данных*  
Целевой тип данных. Сюда входят **xml**, **bigint**, и **sql_variant**. Псевдонимы типов данных недопустимы.
  
*length*  
Указываемое дополнительно целое число, обозначающее длину целевого типа данных. Значение по умолчанию — 30.
  
*стиль*  
Целочисленное выражение, указывающее, как функцию CONVERT для преобразования *выражение*. Если стиль имеет значение NULL, возвращается NULL. Диапазон определяется *data_type*. 
  
## <a name="return-types"></a>Возвращаемые типы
Возвращает *выражение* преобразуется в *data_type*.

## <a name="date-and-time-styles"></a>Стили даты и времени  
Когда *выражение* имеет тип данных даты или времени *стиль* может принимать одно из значений, приведенных в следующей таблице. Другие значения обрабатываются как 0. Начиная с версии [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], единственные стили, которые поддерживаются при преобразовании из даты и времени с типами **datetimeoffset** : 0 или 1. Все другие стили преобразования возвращают ошибку 9809.
  
>  [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает формат даты в арабском стиле, используя кувейтский алгоритм.
  
|Без века (гг) (<sup>1</sup>)|С веком (гггг)|Standard Edition|Ввода вывода (<sup>3</sup>)|  
|---|---|--|---|
|-|**0** или **100** (<sup>1,</sup><sup>2</sup>)|Значение по умолчанию для типа данных datetime и smalldatetime|мес дд гггг чч:мм|  
|**1**|**101**|США|1 = мм/дд/гг<br /> 101 = мм/дд/гггг|  
|**2**|**102**|ANSI|2 = гг.мм.дд<br /> 102 = гггг.мм.дд|  
|**3**|**103**|Британский/французский|3 = дд/мм/гг<br /> 103 = дд/мм/гггг|  
|**4**|**104**|Немецкий|4 = дд.мм.гг<br /> 104 = дд.мм.гггг|  
|**5**|**105**|Итальянский|5 = дд-мм-гг<br /> 105 = дд-мм-гггг|  
|**6**|**106** <sup>(1)</sup>|-|6 = дд мес гг<br /> 106 = дд мм гггг|  
|**7**|**107** <sup>(1)</sup>|-|7 = Мес дд, гг<br /> 107 = Мес дд, гггг|  
|**8**|**108**|-|чч:мм:сс|  
|-|**9** или **109** (<sup>1,</sup><sup>2</sup>)|По умолчанию + миллисекунды|мес дд гггг чч:мм:сс:ммм|  
|**10**|**110**|США|10 = мм-дд-гг<br /> 110 = мм-дд-гггг|  
|**11**|**111**|ЯПОНСКИЙ|11 = гг/мм/дд<br /> 111 = гггг/мм/дд|  
|**12**|**112**|ISO|12 = ггммдд<br /> 112 = ггггммдд|  
|-|**13** или **113** (<sup>1,</sup><sup>2</sup>)|Европейский по умолчанию + миллисекунды|дд мес гггг чч:мм:сс:ммм (24-часовой формат)|  
|**14**|**114**|-|чч:ми:сс:ммм (24-часовой формат)|  
|-|**20** или **120** (<sup>2</sup>)|Канонический формат ODBC|гггг-мм-дд чч:ми:сс (24-часовой формат)|  
|-|**21** или **121** (<sup>2</sup>)|Каноническая форма ODBC (с миллисекундами) является значением по умолчанию для времени, даты, datetime2, и datetimeoffset|гггг-мм-дд чч:ми:сс.ммм (24-часовой формат)|  
|-|**126** (<sup>4</sup>)|ISO8601|гггг-мм-ддТчч:мм:сс.ммм (без пробелов)<br /> Примечание: Если значение миллисекунд (ммм) равно 0, значение миллисекунд не отображается. Например, значение "2012-11-07T18:26:20.000" будет отображено как "2012-11-07T18:26:20".|  
|-|**127**(<sup>6, 7</sup>)|ISO8601 с часовым поясом П.|гггг-мм-ддТчч:мм:сс.мммП (без пробелов)<br /> Примечание: Если значение миллисекунд (ммм) равно 0, значение миллисекунд не отображается. Например, значение "2012-11-07T18:26:20.000" будет отображено как "2012-11-07T18:26:20".|  
|-|**130** (<sup>1,</sup><sup>2</sup>)|Хиджра (<sup>5</sup>)|дд мес гггг чч:ми:сс:мммAM<br /> В этом стиле "мес" является представлением Юникода полного названия месяца в Хиджре. Это значение отображается неправильно на значение по умолчанию США установки SSMS.|  
|-|**131** (<sup>2</sup>)|Хиджра (<sup>5</sup>)|дд/мм/гггг чч:ми:сс:мммAM|  
  
<sup>1</sup> эти значения стилей возвращают недетерминированные результаты. Включают в себя все стили "гг" (без номера века) и часть стилей "гггг" (с номером века).
  
<sup>2</sup> значения по умолчанию (*стиль** *0** или **100**, **9** или **109**, **13** или **113**, **20** или **120**, и **21** или **121**) всегда возвращают год с веком (гггг).
  
<sup>3</sup> вход при преобразовании к **datetime**; выход при преобразовании в символьные данные.
  
<sup>4</sup> предназначен для использования в XML. Для преобразования из **datetime** или **smalldatetime** в символьные данные формат вывода является, как описано в предыдущей таблице.
  
<sup>5</sup> Хиджра — календарная система с несколькими вариантами. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используется кувейтский алгоритм.
  
> [!IMPORTANT]  
>  По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] интерпретирует двузначные значения года с пороговым значением 2049. Т.е. год, обозначенный двумя цифрами 49, интерпретируется как 2049, а год, обозначенный двумя цифрами 50, интерпретируется как 1950. В большинстве клиентских приложений, основанных, в частности, на объектах автоматизации, 2030 год используется в качестве порогового значения. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]предоставляет параметра two digit year cutoff конфигурации, который изменяет пороговое значение года в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , что позволяет согласовывать работу с датами. Рекомендуется использовать четырехзначные года.  
  
<sup>6</sup> поддерживается только при приведении символьных данных к **datetime** или **smalldatetime**. Когда символьных данных, представляющих только дату или только время компонентов приведен к **datetime** или **smalldatetime** типы данных неуказанное время равно 00:00:00.000 и указан компонента даты устанавливается значение 1900-01-01.
  
<sup>7</sup>Необязательный признак часового пояса, Z, используется для упрощения сопоставления XML- **datetime** значения, которые имеют данные о часовом поясе для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **datetime** значения, которые имеют часовой пояс . П — это индикатор часового пояса UTC-0. Другие часовые пояса обозначаются смещением в формате ЧЧ:ММ в направлении + или -. Например: `2006-12-12T23:45:12-08:00`.
  
При преобразовании в символьные данные из **smalldatetime**, стили, включающие секунды или миллисекунды, будут содержать нули в соответствующих позициях. При преобразовании из ненужные части даты можно усечь **datetime** или **smalldatetime** значения с помощью соответствующей **char** или **varchar** длина типа данных.
  
При преобразовании в **datetimeoffset** из символьных данных со стилем, включающим время, смещение часового пояса добавляется к результату.
  
## <a name="float-and-real-styles"></a>стили данных float и real
При *выражение* — **float** или **реальные**, *стиль* может принимать одно из значений, приведенных в следующей таблице. Другие значения обрабатываются как 0.
  
|Значение|Вывод|  
|---|---|
|**0** (по умолчанию)|Не более 6 разрядов. По необходимости используется экспоненциальное представление чисел.|  
|**1**|Всегда 8 разрядов. Всегда используется экспоненциальное представление чисел.|  
|**2**|Всегда 16 разрядов. Всегда используется экспоненциальное представление чисел.|  
|**3**|Всегда 17 знаков. Используется для преобразования без потери данных. С этим стилем каждые distinct float или real значение гарантированно преобразования в строку отдельным символом.<br /> **Применяется к:** [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], а начиная с версии [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].|  
|**126, 128, 129**|Включено для совместимости с прежними версиями и может быть исключено в следующих версиях.|  
  
## <a name="money-and-smallmoney-styles"></a>стили Money и smallmoney
Когда *выражение* — **money** или **smallmoney**, *стиль* может принимать одно из значений, приведенных в следующей таблице. Другие значения обрабатываются как 0.
  
|Значение|Вывод|  
|---|---|
|**0** (по умолчанию)|Без запятых, разделяющих группы разрядов, с двумя цифрами справа от десятичного разделителя, например 4235,98.|  
|**1**|Запятые, разделяющие группы из трех разрядов слева от десятичной точки, с двумя цифрами справа от десятичного разделителя, например 3 510,92.|  
|**2**|Без запятых, разделяющих группы разрядов, с четырьмя цифрами справа от десятичного разделителя, например 4235,9819.|  
|**126**|Эквивалентно стилю 2 при преобразовании в char(n) или varchar(n)|  
  
## <a name="xml-styles"></a>стили данных XML
Когда *выражение* — **xml***, стиль* может принимать одно из значений, приведенных в следующей таблице. Другие значения обрабатываются как 0.
  
|Значение|Вывод|  
|---|---|
|**0** (по умолчанию)|Использовать синтаксический разбор по умолчанию, при котором незначащие пробельные символы удаляются, а внутренние подмножества DTD не разрешены.<br /> **Примечание:** при преобразовании в **xml** тип данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] незначащие пробельные символы обрабатывается иначе, чем в XML 1.0. Дополнительные сведения см. в разделе [создание экземпляров XML-данных](../../relational-databases/xml/create-instances-of-xml-data.md).|  
|**1**|Сохранять незначащие пробельные символы. Значение по умолчанию устанавливает это значение стиля **XML: space** правила обработки работают так же, как если бы **XML: space = «preserve»** было указано.|  
|**2**|Использовать ограниченную обработку внутреннего подмножества DTD.<br /><br /> При этом для выполнения операций синтаксического анализа без проверки действительности сервер может пользоваться следующей информацией, предоставляемой внутренним подмножеством DTD.<br /> -Применяются атрибуты по умолчанию.<br /> : Ссылки на сущности внутренняя разрешаются и раскрываются.<br /> -Будет проверена синтаксическая правильность модели содержимого DTD.<br /> Средство синтаксического анализа пропускает внешние подмножества DTD. Он также не будет рассматривать XML-декларацию, чтобы увидеть ли **автономный** установлен атрибут **Да** или **не**, но вместо этого экземпляр XML будет анализироваться как будто это изолированный документ.|  
|**3**|Сохранять незначащие пробельные символы и использовать ограниченную обработку внутреннего подмножества DTD.|  
  
## <a name="binary-styles"></a>Стили двоичных данных
Когда *выражение* — **binary(n)**, **varbinary(n)**, **char(n)**, или **varchar(n)**, *стиль* может принимать одно из значений, приведенных в следующей таблице. При использовании значений стиля, отсутствующих в этой таблице, возвращается ошибка.
  
|Значение|Вывод|  
|---|---|
|**0** (по умолчанию)|Преобразует символы ASCII в двоичные байты либо двоичные байты в символы ASCII. Каждый символ или байт преобразуется в соотношении 1:1.<br /> Если *data_type* относится к двоичному типу, символы 0 x добавляются слева результата.|  
|**1**, **2**|Если *data_type* относится к двоичному типу, выражение должно быть символьное выражение. *Выражение* должно состоять из четного числа шестнадцатеричных цифр (0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A, B, C, D, E, F, a, b, c, d, e, f). Если *стиль* имеет значение 1 символы 0 x должны быть первые два символа в выражении. Если выражение содержит нечетное число символов или использованы недопустимые символы, возникает ошибка.<br /> Если длина преобразованного выражения превышает длину *data_type* результат усекается справа.<br /> Фиксированная длина *data_types* , больше, чем преобразованного результата имеет результата справа добавляются нули.<br /> Если параметр data_type принадлежит к символьному типу, выражение должно быть двоичным. Каждый двоичный символ преобразуется в два шестнадцатеричных символа. Если длина преобразованного выражения превышает *data_type* длина, она усекается справа.<br /> Если *data_type* относится к символьному типу фиксированного размера и длина преобразованного результата меньше длины типа *data_type*; вправо преобразованного выражения для сохранения даже добавляются пробелы количество шестнадцатеричных цифр.<br /> Символы 0 x добавляются слева к преобразованному результату для *стиль* 1.|  
  
## <a name="implicit-conversions"></a>Неявные преобразования
Неявные преобразования происходят, когда функции CAST или CONVERT не вызываются. Явные преобразования требуют вызова функции CAST или CONVERT. На следующей иллюстрации показаны все явные и неявные преобразования типов данных, допустимые для системных типов данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. К ним относятся **xml**, **bigint**, и **sql_variant**. Нет неявного преобразования на назначение на основе **sql_variant** тип данных, но существует неявное преобразование в **sql_variant**.
  
> [!TIP]  
>  На этой диаграмме доступен в виде PDF-файла в [центра загрузки Майкрософт](http://www.microsoft.com/download/details.aspx?id=35834).  
  
![Таблица преобразования типов данных](../../t-sql/data-types/media/lrdatahd.png "таблица преобразования типов данных")
  
При преобразовании между **datetimeoffset** и символьными типами **char**, **varchar**, **nchar**, и **nvarchar**  преобразованный часовой пояс часть смещения должна иметь по две цифры для часов и Минут, например, -08:00.
  
> [!NOTE]  
>  Поскольку данные в Юникоде всегда использует четное число байтов, будьте осторожны при преобразовании **двоичных** или **varbinary** в Юникод или обратно, поддерживаемые типы данных. Например, при следующем преобразовании не будет возвращено шестнадцатеричное значение 41, в данном случае будет получено значение 4100: `SELECT CAST(CAST(0x41 AS nvarchar) AS varbinary)`.  
  
## <a name="large-value-data-types"></a>Типы данных больших значений
Типы данных больших значений демонстрируют явные и неявные преобразования ведут себя их аналоги меньшего объема специально **varchar**, **nvarchar** и **varbinary**типы данных. Однако необходимо учитывать следующие правила:
-   Преобразование из **изображения** для **varbinary(max)** и наоборот — неявного преобразования и преобразования между **текст** и **varchar(max)**, и **ntext** и **nvarchar(max)**.  
-   Типы преобразование из большого объема данных, такие как **varchar(max)**на более мелкие аналогичный тип данных, таких как **varchar**, неявное преобразование, но усечение возникает, если слишком большое значение для больших значений Указанная длина типа данных меньшего размера.  
-   Преобразование из **varchar**, **nvarchar**, или **varbinary** типов выполняется неявно в соответствующие им данные большого объема.  
-   Преобразование из **sql_variant** тип данных в типы данных больших значений является явное преобразование.  
-   Типы данных больших значений невозможно преобразовать в **sql_variant** тип данных.  
  
Дополнительные сведения о преобразовании из **xml** тип данных, в разделе [создание экземпляров XML-данных](../../relational-databases/xml/create-instances-of-xml-data.md).
  
## <a name="xml-data-type"></a>Тип данных XML
При явном или неявном приведении **xml** типа данных в строке или двоичному типу данных, содержимое **xml** сериализации типа данных на основе набора правил. Сведения об этих правилах см. в разделе [определение сериализации XML-данных](../../relational-databases/xml/define-the-serialization-of-xml-data.md). Дополнительные сведения о преобразовании других типов данных для **xml** тип данных, в разделе [создание экземпляров XML-данных](../../relational-databases/xml/create-instances-of-xml-data.md).
  
## <a name="text-and-image-data-types"></a>типы данных Text и image
Автоматическое преобразование типов данных не поддерживается для **текст** и **изображение** типов данных. Можно явно преобразовать **текст** в символьные данные и **изображения** данных для **двоичных** или **varbinary**, но Максимальная длина составляет 8000 байт. Если при попытке неверное преобразование, например преобразовать символьное выражение, содержащее буквы, в **int**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает сообщение об ошибке.
  
## <a name="output-collation"></a>Параметры сортировки выходных данных  
Если входные и выходные данные функций CAST и CONVERT представляют собой символьные строки, у выходных данных будут те же параметры сортировки, что и у входных. Если входные данные не символьная строка, выходным назначаются параметры сортировки по умолчанию для этой базы данных и присваивается метка о том, что этот режим используется принудительно. Дополнительные сведения см. в разделе [очередность параметров сортировки &#40; Transact-SQL &#41; ](../../t-sql/statements/collation-precedence-transact-sql.md).
  
Чтобы назначить выходным данным другие параметры сортировки, примените предложение COLLATE к результирующему выражению функции CAST или CONVERT. Например:
  
`SELECT CAST('abc' AS varchar(5)) COLLATE French_CS_AS`
  
## <a name="truncating-and-rounding-results"></a>Усечение и округление результатов
При преобразовании символьных или двоичных выражений (**char**, **nchar**, **nvarchar**, **varchar**, **двоичныйфайл**, или **varbinary**) к выражению другого типа данных, данные могут быть усечены, отображаться только частично или возвращается сообщение об ошибке, так как результат слишком мал для отображения. Преобразования в **char**, **varchar**, **nchar**, **nvarchar**, **двоичных**, и  **varbinary** усекаются, за исключением перечисленных в следующей таблице.
  
|Из типа данных|В тип данных|Результат|  
|---|---|---|
|**int**, **smallint**, или **tinyint**|**char**|*|  
||**varchar**|*|  
||**nchar**|E|  
||**nvarchar**|E|  
|**Money**, **smallmoney**, **числовое**, **десятичное**, **float**, или **real**|**char**|E|  
||**varchar**|E|  
||**nchar**|E|  
||**nvarchar**|E|  
  
\*= Результат слишком мал для отображения. О = ошибка, так как длина результата слишком мала для отображения.
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]гарантирует только обратимые преобразования, преобразования, преобразования типа данных из исходного типа данных, а затем опять дает те же значения от версии к версии. В следующем примере показано обратимое преобразование:
  
```sql
DECLARE @myval decimal (5, 2);  
SET @myval = 193.57;  
SELECT CAST(CAST(@myval AS varbinary(20)) AS decimal(10,5));  
-- Or, using CONVERT  
SELECT CONVERT(decimal(10,5), CONVERT(varbinary(20), @myval));  
```  
  
> [!NOTE]  
>  Не пытайтесь составлять **двоичных** , а затем преобразовывать их в тип данных из категории числовых типов данных. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]не гарантирует, что результат **десятичное** или **числовое** преобразование в тип данных **двоичных** будет одинаковым в разных версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
В следующем примере показано результирующее выражение, которое слишком мало для отображения:
  
```sql
USE AdventureWorks2012;  
GO  
SELECT p.FirstName, p.LastName, SUBSTRING(p.Title, 1, 25) AS Title,
    CAST(e.SickLeaveHours AS char(1)) AS [Sick Leave]  
FROM HumanResources.Employee e JOIN Person.Person p 
    ON e.BusinessEntityID = p.BusinessEntityID  
WHERE NOT e.BusinessEntityID >5;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```   
FirstName   LastName      Title   Sick Leave
---------   ------------- ------- --------`
Ken         Sanchez       NULL   *
Terri       Duffy         NULL   *
Roberto     Tamburello    NULL   *
Rob         Walters       NULL   *
Gail        Erickson      Ms.    *
(5 row(s) affected)  
```
  
При преобразовании между типами данных с разными длинами дробных частей результат может усекаться или округляться. В следующей таблице описано это поведение.
  
|От|Чтобы|Поведение|  
|---|---|---|
|**numeric**|**numeric**|Округление|  
|**numeric**|**int**|Усечение|  
|**numeric**|**money**|Округление|  
|**money**|**int**|Округление|  
|**money**|**numeric**|Округление|  
|**float**|**int**|Усечение|  
|**float**|**numeric**|Округление<br /><br /> Преобразование **float** значения, которые используют экспоненциальный формат для **десятичное** или **числовое** ограничена только 17 знаков точности. Любое значение с точностью, превышающей 17 знаков, округляется до нуля.|  
|**float**|**datetime**|Округление|  
|**datetime**|**int**|Округление|  
  
Например, может усечен или округления при преобразовании в значения 10.6496 и-10.6496 **int** или **числовое** типов:
  
```sql
SELECT  CAST(10.6496 AS int) as trunc1,
         CAST(-10.6496 AS int) as trunc2,
         CAST(10.6496 AS numeric) as round1,
         CAST(-10.6496 AS numeric) as round2;
 ```
В следующей таблице показаны результаты запроса:
 
|trunc1|trunc2|round1|round2|
|---|---|---|---|
|10|-10|11|-11|
 
При преобразовании к типам данных, у которых дробная часть короче, чем у исходного типа, значение округляется. Например, результатом следующего преобразования будет `$10.3497`:
  
`SELECT CAST(10.3496847 AS money);`
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Возвращает сообщение об ошибке при попытке преобразовать нечисловые **char**, **nchar**, **varchar**, или **nvarchar** данные преобразуются в **int** , **float**, **числовое**, или **десятичное**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]также возвращает ошибку, если пустая строка (» «) преобразуется в **числовое** или **десятичное**.
  
## <a name="certain-datetime-conversions-are-nondeterministic"></a>Некоторые преобразования даты и времени являются недетерминированными
Следующая таблица содержит стили, для которых преобразование строк в тип datetime недетерминировано.
  
|||  
|-|-|  
|Все стили меньше 100<sup>1</sup>|106|  
|107|109|  
|113|130|  
  
<sup>1</sup> за исключением стилей 20 и 21
  
## <a name="supplementary-characters-surrogate-pairs"></a>Дополнительные символы (суррогатные пары)
Начиная с версии [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], при использовании параметров сортировки дополнительных символов (SC) Операция CAST из **nchar** или **nvarchar** для **nchar** или  **nvarchar** меньшей длиной не будет выполнять усечение внутри суррогатной пары; усечение происходит перед дополнительным символом. Например, выполнение следующего фрагмента кода приведет к тому, что в `@x` останется лишь `'ab'`. Места недостаточно для размещения дополнительного символа.
  
```sql
DECLARE @x NVARCHAR(10) = 'ab' + NCHAR(0x10000);  
SELECT CAST (@x AS NVARCHAR(3));  
```  
  
При использовании параметров сортировки SC поведение `CONVERT` аналогично `CAST`.
  
## <a name="compatibility-support"></a>Поддержка совместимости
В более ранних версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], стиль по умолчанию для операций CAST и CONVERT над **время** и **datetime2** типы данных — 121, за исключением того, при использовании любой из этих типов в выражении вычисляемого столбца. Для вычисляемых столбцов используемый по умолчанию стиль — 0. Это поведение влияет на вычисляемые столбцы при их создании и использовании в запросах с автоматической параметризацией, а также при использовании в определениях ограничений.
  
При уровне совместимости 110 и выше стиль по умолчанию для операций CAST и CONVERT на **время** и **datetime2** типы данных всегда имеет значение 121. Если запрос основан на прежнем поведении, следует использовать уровень совместимости ниже 110, либо явно задать в затрагиваемом запросе стиль 0.
  
Обновление базы данных до уровня совместимости 110 и выше не приведет к изменению пользовательских данных, сохраненных на диске. Следует исправить эти данных соответствующим образом вручную. Например, если бы вы использовали предложение SELECT INTO для создания таблицы на основе источника, содержащего описанное выше выражение вычисляемого столбца, то сохранялись бы данные (благодаря стилю 0), а не само определение вычисляемого столбца. Потребовалось бы вручную обновлять эти данные в соответствии со стилем 121.
  
## <a name="BKMK_examples"></a> Примеры  
  
### <a name="a-using-both-cast-and-convert"></a>A. Использование функций CAST и CONVERT  
В каждом примере получаются имена продуктов, у которых первая цифра цены — `3`, для этого их значения `ListPrice` преобразовываются к `int`.
  
```sql
-- Use CAST  
USE AdventureWorks2012;  
GO  
SELECT SUBSTRING(Name, 1, 30) AS ProductName, ListPrice  
FROM Production.Product  
WHERE CAST(ListPrice AS int) LIKE '3%';  
GO  
  
-- Use CONVERT.  
USE AdventureWorks2012;  
GO  
SELECT SUBSTRING(Name, 1, 30) AS ProductName, ListPrice  
FROM Production.Product  
WHERE CONVERT(int, ListPrice) LIKE '3%';  
GO  
```  
  
### <a name="b-using-cast-with-arithmetic-operators"></a>Б. Использование функции CAST с арифметическими операторами  
В следующем примере вычисляется столбец значений (`Computed`) путем деления суммарных продаж за год (`SalesYTD`) на проценты комиссионных (`CommissionPCT`). Результат преобразуется к типу данных `int` после округления до ближайшего целого числа.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT CAST(ROUND(SalesYTD/CommissionPCT, 0) AS int) AS Computed  
FROM Sales.SalesPerson   
WHERE CommissionPCT != 0;  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
```  
Computed
------
379753754
346698349
257144242
176493899
281101272
0  
301872549
212623750
298948202
250784119
239246890
101664220
124511336
97688107
(14 row(s) affected)  
```  
  
### <a name="c-using-cast-to-concatenate"></a>В. Использование функции CAST для объединения строк  
Следующий пример Сцепляет несимвольных выражения приведения. Использует AdventureWorksDW.
  
```sql
SELECT 'The list price is ' + CAST(ListPrice AS varchar(12)) AS ListPrice  
FROM dbo.DimProduct  
WHERE ListPrice BETWEEN 350.00 AND 400.00;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
ListPrice
------------------------
The list price is 357.06
The list price is 364.09
The list price is 364.09
The list price is 364.09
The list price is 364.09  
```  
  
### <a name="d-using-cast-to-produce-more-readable-text"></a>Г. Использование функции CAST для получения удобочитаемого текста  
В следующем примере используется ПРИВЕДЕНИЕ в списке ВЫБОРА для преобразования `Name` столбец **char(10)** столбца. Использует AdventureWorksDW.
  
```sql
SELECT DISTINCT CAST(EnglishProductName AS char(10)) AS Name, ListPrice  
FROM dbo.DimProduct  
WHERE EnglishProductName LIKE 'Long-Sleeve Logo Jersey, M';  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
Name        UnitPrice
----------  ---------
Long-Sleev  31.2437
Long-Sleev  32.4935
Long-Sleev  49.99  
```  
  
### <a name="e-using-cast-with-the-like-clause"></a>Д. Использование функции CAST с предложением LIKE  
В следующем примере столбец значений `money` типа `SalesYTD` преобразуется в тип `int`, а затем в тип `char(20)` так, чтобы его можно было использовать в предложении `LIKE`.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT p.FirstName, p.LastName, s.SalesYTD, s.BusinessEntityID  
FROM Person.Person AS p   
JOIN Sales.SalesPerson AS s   
    ON p.BusinessEntityID = s.BusinessEntityID  
WHERE CAST(CAST(s.SalesYTD AS int) AS char(20)) LIKE '2%';  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
FirstName        LastName            SalesYTD         SalesPersonID
---------------- ------------------- ---------------- -------------
Tsvi             Reiter              2811012.7151      279
Syed             Abbas               219088.8836       288
Rachel           Valdez              2241204.0424      289
(3 row(s) affected)  
```
  
### <a name="f-using-convert-or-cast-with-typed-xml"></a>Е. Использование функции CONVERT или CAST с типизированным XML  
Ниже приведены несколько примерах показано использование функции CONVERT для преобразования данных в типизированный XML с помощью [тип данных XML и столбцами &#40; SQL Server &#41; ](../../relational-databases/xml/xml-data-type-and-columns-sql-server.md).
  
В этом примере строка, содержащая пробельные символы, текст и разметку, преобразуется в типизированный XML, в котором удаляются все незначащие пробельные символы (пробелы, разделяющие узлы):
  
```sql
CONVERT(XML, '<root><child/></root>')  
```  
  
В этом примере похожая строка, содержащая пробельные символы, текст и разметку, преобразуется в типизированный XML, в котором сохраняются все незначащие пробельные символы (пробелы, разделяющие узлы):
  
```sql
CONVERT(XML, '<root>          <child/>         </root>', 1)  
```  
  
В этом примере строка, содержащая пробельные символы, текст и разметку, приводится к типизированному XML:
  
```sql
CAST('<Name><FName>Carol</FName><LName>Elliot</LName></Name>'  AS XML)  
```  
  
Дополнительные примеры см. в разделе [создание экземпляров XML-данных](../../relational-databases/xml/create-instances-of-xml-data.md).
  
### <a name="g-using-cast-and-convert-with-datetime-data"></a>Ж. Использование функций CAST и CONVERT с данными типа datetime  
Следующий пример показывает текущую дату и время, использует функцию `CAST` для изменения текущей даты и времени в символьный тип данных и затем использует `CONVERT` для отображения даты и времени в формате `ISO 8901`.
  
```sql
SELECT   
   GETDATE() AS UnconvertedDateTime,  
   CAST(GETDATE() AS nvarchar(30)) AS UsingCast,  
   CONVERT(nvarchar(30), GETDATE(), 126) AS UsingConvertTo_ISO8601  ;  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
UnconvertedDateTime     UsingCast              UsingConvertTo_ISO8601
----------------------- ---------------------- ------------------------------
2006-04-18 09:58:04.570 Apr 18 2006  9:58AM    2006-04-18T09:58:04.570
(1 row(s) affected)  
```
  
Следующий пример — частичная противоположность предыдущему примеру. Пример отображает дату и время в виде символьных данных, использует функцию `CAST` для изменения символьных данных в тип данных `datetime`, а затем использует функцию `CONVERT` для изменения символьных данных в тип данных `datetime`.
  
```sql
SELECT   
   '2006-04-25T15:50:59.997' AS UnconvertedText,  
   CAST('2006-04-25T15:50:59.997' AS datetime) AS UsingCast,  
   CONVERT(datetime, '2006-04-25T15:50:59.997', 126) AS UsingConvertFrom_ISO8601 ;  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
UnconvertedText         UsingCast               UsingConvertFrom_ISO8601
----------------------- ----------------------- ------------------------
2006-04-25T15:50:59.997 2006-04-25 15:50:59.997 2006-04-25 15:50:59.997
(1 row(s) affected)  
```
  
### <a name="h-using-convert-with-binary-and-character-data"></a>З. Использование функции CONVERT с двоичными и символьными данными  
В следующих примерах показаны результаты преобразования двоичных и символьных данных с использованием различных стилей.
  
```sql
--Convert the binary value 0x4E616d65 to a character value.  
SELECT CONVERT(char(8), 0x4E616d65, 0) AS [Style 0, binary to character];  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
Style 0, binary to character
----------------------------
Name  
(1 row(s) affected)  
```
 
В следующем примере показано, как стиль 1 можно принудительно результат, который должен быть усечен. Усечение вызвана включая символы 0 x в результат.  
```sql  
SELECT CONVERT(char(8), 0x4E616d65, 1) AS [Style 1, binary to character];  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
Style 1, binary to character
------------------------------
0x4E616D
(1 row(s) affected)  
```  
 
В следующем примере показано, что стиль 2 не усечь результат, так как символы 0 x не включаются в результат.  
```sql  
SELECT CONVERT(char(8), 0x4E616d65, 2) AS [Style 2, binary to character];  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
Style 2, binary to character
------------------------------
4E616D65
(1 row(s) affected)  
```
  
Преобразуйте символьное значение «Имя» в двоичное значение.  
```sql
SELECT CONVERT(binary(8), 'Name', 0) AS [Style 0, character to binary];  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
Style 0, character to binary
----------------------------
0x4E616D6500000000
(1 row(s) affected)  
```
  
```sql
SELECT CONVERT(binary(4), '0x4E616D65', 1) AS [Style 1, character to binary];  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
Style 1, character to binary
---------------------------- 
0x4E616D65
(1 row(s) affected)  
```  

```sql
SELECT CONVERT(binary(4), '4E616D65', 2) AS [Style 2, character to binary];  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
Style 2, character to binary  
----------------------------------  
0x4E616D65
(1 row(s) affected)  
```  
  
### <a name="i-converting-date-and-time-data-types"></a>И. Конвертирование типов данных даты и времени  
Следующий пример демонстрирует конвертацию типов данных даты, времени и datetime.
  
```sql
DECLARE @d1 date, @t1 time, @dt1 datetime;  
SET @d1 = GETDATE();  
SET @t1 = GETDATE();  
SET @dt1 = GETDATE();  
SET @d1 = GETDATE();  
-- When converting date to datetime the minutes portion becomes zero.  
SELECT @d1 AS [date], CAST (@d1 AS datetime) AS [date as datetime];  
-- When converting time to datetime the date portion becomes zero   
-- which converts to January 1, 1900.  
SELECT @t1 AS [time], CAST (@t1 AS datetime) AS [time as datetime];  
-- When converting datetime to date or time non-applicable portion is dropped.  
SELECT @dt1 AS [datetime], CAST (@dt1 AS date) AS [datetime as date], 
   CAST (@dt1 AS time) AS [datetime as time];  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="j-using-cast-and-convert"></a>К. Использование функций CAST и CONVERT  
В этом примере извлекается имя продукта для этих продуктов, имеющих `3` в первая цифра их цену по прейскуранту и преобразует их `ListPrice` для **int**. Использует AdventureWorksDW.
  
```sql
SELECT EnglishProductName AS ProductName, ListPrice  
FROM dbo.DimProduct  
WHERE CAST(ListPrice AS int) LIKE '3%';  
```  
  
Этот пример демонстрирует тот же запрос, использование функции CONVERT вместо CAST. Использует AdventureWorksDW.
  
```sql
SELECT EnglishProductName AS ProductName, ListPrice  
FROM dbo.DimProduct  
WHERE CONVERT(int, ListPrice) LIKE '3%';  
```  
  
### <a name="k-using-cast-with-arithmetic-operators"></a>Л. Использование функции CAST с арифметическими операторами  
В следующем примере вычисляется столбец значений, разделив цена единицы товара (`UnitPrice`), процент скидки (`UnitPriceDiscountPct`). Результат преобразуется к типу данных `int` после округления до ближайшего целого числа. Использует AdventureWorksDW.
  
```sql
SELECT ProductKey, UnitPrice,UnitPriceDiscountPct,  
       CAST(ROUND (UnitPrice*UnitPriceDiscountPct,0) AS int) AS DiscountPrice  
FROM dbo.FactResellerSales  
WHERE SalesOrderNumber = 'SO47355'   
      AND UnitPriceDiscountPct > .02;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
ProductKey  UnitPrice  UnitPriceDiscountPct  DiscountPrice
----------  ---------  --------------------  -------------
323         430.6445   0.05                  22
213         18.5043    0.05                  1
456         37.4950    0.10                  4
456         37.4950    0.10                  4
216         18.5043    0.05                  1  
```  
  
### <a name="l-using-cast-with-the-like-clause"></a>М. Использование функции CAST с предложением LIKE  
В следующем примере выполняется преобразование **money** столбца `ListPrice` для **int** типа и затем **char(20)** тип, так что он может использоваться с предложением LIKE. Использует AdventureWorksDW.
  
```sql
SELECT EnglishProductName AS Name, ListPrice  
FROM dbo.DimProduct  
WHERE CAST(CAST(ListPrice AS int) AS char(20)) LIKE '2%';  
```  
  
### <a name="m-using-cast-and-convert-with-datetime-data"></a>Н. Использование функций CAST и CONVERT с данными типа datetime  
В следующем примере отображается текущая дата и время, использует ПРИВЕДЕНИЯ для изменения текущей даты и времени в символьный тип данных, а затем использует CONVERT отобразить дату и время в формате ISO 8601. Использует AdventureWorksDW.
  
```sql
SELECT TOP(1)  
   SYSDATETIME() AS UnconvertedDateTime,  
   CAST(SYSDATETIME() AS nvarchar(30)) AS UsingCast,  
   CONVERT(nvarchar(30), SYSDATETIME(), 126) AS UsingConvertTo_ISO8601  
FROM dbo.DimCustomer;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
UnconvertedDateTime     UsingCast                     UsingConvertTo_ISO8601  
---------------------   ---------------------------   ---------------------------  
07/20/2010 1:44:31 PM   2010-07-20 13:44:31.5879025   2010-07-20T13:44:31.5879025  
```  
  
Следующий пример — частичная противоположность предыдущему примеру. Пример отображает дату и время в виде символьных данных, использует функцию CAST для изменения символьных данных в **datetime** тип данных и затем использует ПРЕОБРАЗОВАНИЯ для изменения символьных данных в **datetime** тип данных. Использует AdventureWorksDW.
  
```sql
SELECT TOP(1)   
   '2010-07-25T13:50:38.544' AS UnconvertedText,  
CAST('2010-07-25T13:50:38.544' AS datetime) AS UsingCast,  
   CONVERT(datetime, '2010-07-25T13:50:38.544', 126) AS UsingConvertFrom_ISO8601  
FROM dbo.DimCustomer;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
UnconvertedText         UsingCast               UsingConvertFrom_ISO8601
----------------------- ----------------------- ------------------------
2010-07-25T13:50:38.544 07/25/2010 1:50:38 PM   07/25/2010 1:50:38 PM  
```  
  
## <a name="see-also"></a>См. также:
[Преобразование типов данных &#40; компонент Database Engine &#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)  
[Системные функции &#40; Transact-SQL &#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
[Написание инструкций Transact-SQL, адаптированных к международному использованию](../../relational-databases/collations/write-international-transact-sql-statements.md)
  

