---
title: Использование типа данных | Документы Microsoft
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-odbc-results
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
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
caps.latest.revision: 34
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 4fed82c2cfb21efa75278847716e90f546e64eb3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="data-type-usage"></a>Использование типов данных
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используются следующим типов данных.  
  
|Тип данных|Ограничение|  
|---------------|----------------|  
|Литералы даты|Литералы даты при сохранении в столбец SQL_TYPE_TIMESTAMP ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типы данных **datetime** или **smalldatetime**), имеют значение времени до полудня 12:00:00.000|  
|**Money** и **smallmoney**|Только целочисленные части **money** и **smallmoney** типы данных являются значимыми. Если десятичная часть SQL **money** данные будут усечены во время преобразования типов данных, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента возвращает предупреждение, а не ошибкой.|  
|SQL_BINARY (допускающий значения NULL)|Если столбец SQL_BINARY допускает значения NULL, при подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии 6.0 или более ранней данные, помещенные в источник данных, не заполняются нулями. При получении данных из таких столбцов, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента заполняет их нулями справа. Однако данные, которые создаются в операциях, выполняемых [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (например объединении), не имеют такого заполнения.<br /><br /> Также при помещении данных в такие столбцы в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии 6.0 или более ранней [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] усекает данные справа, если их длина слишком большая, чтобы поместиться в столбец.<br /><br /> Примечание: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента поддерживает соединение с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 и более ранних версий.|  
|SQL_CHAR (усечение)|Если при подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.0 или более ранней версии данные помещаются в столбец SQL_CHAR, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] усекает их справа, не выдавая предупреждения, если их длина слишком большая, чтобы поместиться в столбец.<br /><br /> Примечание: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента поддерживает соединение с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 и более ранних версий.|  
|SQL_CHAR (допускающий значения NULL)|Если столбец SQL_CHAR допускает значения NULL, при подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии 6.0 или более ранней данные, данные, сохраненные в источник данных, не дополняются пробелами. При получении данных из таких столбцов, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента заполняет их пустыми полями справа. Однако данные, которые создаются в операциях, выполняемых [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (например объединении), не имеют такого заполнения.<br /><br /> Примечание: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента поддерживает соединение с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 и более ранних версий.|  
|SQL_LONGVARBINARY, SQL_LONGVARCHAR, SQL_WLONGVARCHAR|При подключении к экземпляру, полностью поддерживаются обновления столбцов с SQL_LONGVARBINARY, SQL_LONGVARCHAR или SQL_WLONGVARCHAR типы данных (с помощью предложения WHERE), влияющие на несколько строк [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6. *x* и более поздних версий. При подключении к экземпляру компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 4.2*x*, ошибка S1000, «частичная вставка или обновление. Вставка или обновление столбца text или image не завершено», если обновление затрагивает более одной строки.<br /><br /> Примечание: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента поддерживает соединение с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 и более ранних версий.|  
|Параметры строковых функций|*строковое_выражение* введите параметры к строке, функции должны быть данных SQL_CHAR или SQL_VARCHAR. Типы данных SQL_LONG_VARCHAR не поддерживаются в строковых функциях. *Число* параметр должен быть меньше или равна 8000, так как типы данных SQL_CHAR и SQL_VARCHAR ограничены максимальной длиной 8000 символов.|  
|Литералы времени|Литералы времени при сохранении в столбец SQL_TIMESTAMP ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типы данных **datetime** или **smalldatetime**), имеют значение даты 1 января 1900 г.|  
|**timestamp**|Значение NULL может быть вставлен вручную в **timestamp** столбца. Тем не менее поскольку **timestamp**столбцы автоматически обновляются по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], значение NULL перезаписывается.|  
|**tinyint**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Tinyint** тип данных без знака. Объект **tinyint** столбец привязан к переменной типа данных SQL_C_UTINYINT по умолчанию.|  
|Псевдонимы типов данных|При подключении к экземпляру компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 4.2*x*, драйвер ODBC добавляет значение NULL в определении столбца, допустимость значений NULL столбца явно не объявлен. Поэтому допустимость значений NULL, помещенная в определение псевдонима типа данных, не учитывается.<br /><br /> При подключении к экземпляру компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 4.2*x*, столбцы с типом данных псевдонима с базовые данные типа **char** или **двоичных** и для которого не допустимость значений NULL объявленные создается с типом данных **varchar** или **varbinary**. [SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md), [SQLColumns](../../relational-databases/native-client-odbc-api/sqlcolumns.md), и [SQLDescribeCol](../../relational-databases/native-client-odbc-api/sqldescribecol.md) возвращают SQL_VARCHAR и SQL_VARBINARY в качестве данных типа для этих столбцов. Данные, полученные из этих столбцов, не заполнены.<br /><br /> Примечание: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента поддерживает соединение с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 и более ранних версий.|  
|Типы данных большой длины|*данные времени выполнения* параметры ограничены для SQL_LONGVARBINARY и SQL_LONGVARCHAR типы данных.|  
|Типы больших значений|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента будет предоставлять **varchar(max)**, **varbinary(max)**, и **nvarchar(max)** типов в виде SQL_VARCHAR, SQL_VARBINARY и SQL_ WVARCHAR (соответственно), в API, которые принимают или возвращают типы данных ODBC SQL.|  
|Определяемый пользователем тип|Столбцы определяемого пользователем типа преобразуются в тип данных SQL_SS_UDT. Если столбец определяемого пользователем типа явно сопоставлен с другим типом в инструкции SQL с помощью методов ToString() или ToXMLString() определяемого пользователем типа или с помощью функций CAST/CONVERT, то тип столбца в результирующем наборе будет отражать реальный тип, к которому столбец был преобразован.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента может только привязать столбец определяемого пользователем ТИПА в двоичном виде. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает преобразование только между типами данных SQL_SS_UDT и SQL_C_BINARY.|  
|XML|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматически преобразует XML в текст Юникода. Тип XML преобразуется в SQL_SS_XML.|  
  
## <a name="see-also"></a>См. также  
 [Обработка результатов &#40;ODBC&#41;](../../relational-databases/native-client-odbc-results/processing-results-odbc.md)  
  
  
