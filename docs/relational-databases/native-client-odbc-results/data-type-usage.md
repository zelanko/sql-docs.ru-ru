---
title: Использование типа данных (ru) Документы Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC data types
- ODBC data types, about ODBC data types
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- data types [ODBC]
- SQL Server Native Client ODBC driver, data types
- data types [ODBC], about data types
ms.assetid: 4f19b0d6-94ac-4a98-a121-57d38787864c
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0384857c53e898af9fca89bb2ee2351f0b65f986
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297862"
---
# <a name="data-type-usage"></a>Использование типов данных
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Драйвер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] налагает следующее использование типов данных.  
  
|Тип данных|Ограничение|  
|---------------|----------------|  
|Литералы даты|Дата буквальные, при хранении в[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] столбце SQL_TYPE_TIMESTAMP (типы данных **времени даты** или **небольшое время даты),** имеют значение времени 12:00:00.000 a.M.|  
|**деньги** и **небольшиеденьги**|Только несколько частей **денег** и **малых денежных** типов данных являются значительными. Если десятичная часть **данных о деньгах** S'L усечена во время преобразования типа данных, водитель [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC возвращает предупреждение, а не ошибку.|  
|SQL_BINARY (допускающий значения NULL)|Если столбец SQL_BINARY допускает значения NULL, при подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии 6.0 или более ранней данные, помещенные в источник данных, не заполняются нулями. При извлечении данных из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] такого столбца водитель Native Client ODBC накладывает его нулями справа. Однако данные, которые создаются в операциях, выполняемых [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (например объединении), не имеют такого заполнения.<br /><br /> Также при помещении данных в такие столбцы в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии 6.0 или более ранней [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] усекает данные справа, если их длина слишком большая, чтобы поместиться в столбец.<br /><br /> Примечание: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер Native Client ODBC поддерживает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подключение к 6.5 и более раньше.|  
|SQL_CHAR (усечение)|Если при подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.0 или более ранней версии данные помещаются в столбец SQL_CHAR, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] усекает их справа, не выдавая предупреждения, если их длина слишком большая, чтобы поместиться в столбец.<br /><br /> Примечание: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер Native Client ODBC поддерживает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подключение к 6.5 и более раньше.|  
|SQL_CHAR (допускающий значения NULL)|Если столбец SQL_CHAR допускает значения NULL, при подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии 6.0 или более ранней данные, данные, сохраненные в источник данных, не дополняются пробелами. При извлечении данных из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] такого столбца водитель Native Client ODBC накладывал их пробелами справа. Однако данные, которые создаются в операциях, выполняемых [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (например объединении), не имеют такого заполнения.<br /><br /> Примечание: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер Native Client ODBC поддерживает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подключение к 6.5 и более раньше.|  
|SQL_LONGVARBINARY, SQL_LONGVARCHAR, SQL_WLONGVARCHAR|Обновления столбцов с SQL_LONGVARBINARY, SQL_LONGVARCHAR или SQL_WLONGVARCHAR типов данных (с использованием положения WHERE), которые [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] влияют на несколько строк, полностью поддерживаются при подключении к экземпляру 6. *x* и позже. При подключении [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] к экземпляру 4.2*x*, ошибка S1000, "Частичная вставка / обновление. Вставка или обновление столбца text или image не завершено», если обновление затрагивает более одной строки.<br /><br /> Примечание: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер Native Client ODBC поддерживает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подключение к 6.5 и более раньше.|  
|Параметры строковых функций|*string_exp* параметры к функциям строки должны быть SQL_CHAR или SQL_VARCHAR типа данных. Типы данных SQL_LONG_VARCHAR не поддерживаются в строковых функциях. Параметр *подсчета* должен быть меньше или равен 8000, поскольку SQL_CHAR и SQL_VARCHAR типов данных ограничены максимальной длиной 8000 символов.|  
|Литералы времени|Значение времени, при хранении в[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL_TIMESTAMP столбце (типы данных **времени даты** или **небольшого времени)** имеют значение даты 1 января 1900 года.|  
|**TIMESTAMP**|Только значение NULL может быть вручную вставлено в **столбец метки времени.** Однако, поскольку столбцы **метки времени**автоматически [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]обновляются, значение NULL перезаписано.|  
|**tinyint**|Тип [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **данных tinyint** не подписан. **Крошечный** столбец привязан к переменной типа данных SQL_C_UTINYINT по умолчанию.|  
|Псевдонимы типов данных|При подключении [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] к экземпляру 4.2*x*драйвер ODBC добавляет NULL к определению столбца, которое явно не объявляет недействительность столбца. Поэтому допустимость значений NULL, помещенная в определение псевдонима типа данных, не учитывается.<br /><br /> При подключении [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] к экземпляру 4.2*x,* столбцы с типом данных псевдонима, который имеет базовый тип данных **символа** или **двоичного** файла и для которого не объявляется недействительность, создаются как тип данных **varchar** или **varbinary.** [S'LColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md), [S'LКолонки](../../relational-databases/native-client-odbc-api/sqlcolumns.md), и [S'LDescribeCol](../../relational-databases/native-client-odbc-api/sqldescribecol.md) возвращения SQL_VARCHAR или SQL_VARBINARY в качестве типа данных для этих столбцов. Данные, полученные из этих столбцов, не заполнены.<br /><br /> Примечание: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер Native Client ODBC поддерживает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подключение к 6.5 и более раньше.|  
|Типы данных большой длины|Параметры *данных по исполнению* ограничены как для SQL_LONGVARBINARY, так и для типов данных SQL_LONGVARCHAR.|  
|Типы больших значений|Драйвер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC будет подвергать **вачар (макс)**, **varbinary(max)** и **nvarchar (max)** типы, как SQL_VARCHAR, SQL_VARBINARY и SQL_WVARCHAR (соответственно) в AI, которые принимают или возвращают типы данных ODBC S'L.|  
|Определяемый пользователем тип|Столбцы определяемого пользователем типа преобразуются в тип данных SQL_SS_UDT. Если столбец определяемого пользователем типа явно сопоставлен с другим типом в инструкции SQL с помощью методов ToString() или ToXMLString() определяемого пользователем типа или с помощью функций CAST/CONVERT, то тип столбца в результирующем наборе будет отражать реальный тип, к которому столбец был преобразован.<br /><br /> Драйвер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC может связываться только с столбцом UDT как двоичный. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает преобразование только между типами данных SQL_SS_UDT и SQL_C_BINARY.|  
|XML|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматически преобразует XML в текст Юникода. Тип XML преобразуется в SQL_SS_XML.|  
  
## <a name="see-also"></a>См. также:  
 [Результаты обработки &#40;ODBC&#41;](../../relational-databases/native-client-odbc-results/processing-results-odbc.md)  
  
  
