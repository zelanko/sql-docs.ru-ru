---
title: Тип данных об использовании | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
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
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 41fc88722e93dd57f026f4e1e153d9c3e59aaaf6
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37432053"
---
# <a name="data-type-usage"></a>Использование типов данных
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используются следующим типов данных.  
  
|Тип данных|Ограничение|  
|---------------|----------------|  
|Литералы даты|Литералы даты при сохранении в столбец SQL_TYPE_TIMESTAMP ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типы данных **datetime** или **smalldatetime**), имеют значение времени 12:00:00.000 часов утра|  
|**Money** и **smallmoney**|Только целочисленные части **деньги** и **smallmoney** значимы типов данных. Если десятичная часть SQL **деньги** данные будут усечены при преобразовании типа данных, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента возвращает предупреждение, а не ошибкой.|  
|SQL_BINARY (допускающий значения NULL)|Если столбец SQL_BINARY допускает значения NULL, при подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии 6.0 или более ранней данные, помещенные в источник данных, не заполняются нулями. При получении данных из таких столбцов, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента заполняет их нулями справа. Однако данные, которые создаются в операциях, выполняемых [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (например объединении), не имеют такого заполнения.<br /><br /> Также при помещении данных в такие столбцы в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии 6.0 или более ранней [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] усекает данные справа, если их длина слишком большая, чтобы поместиться в столбец. **Примечание:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента поддерживают подключение к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 и более ранних версий.|  
|SQL_CHAR (усечение)|Если при подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.0 или более ранней версии данные помещаются в столбец SQL_CHAR, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] усекает их справа, не выдавая предупреждения, если их длина слишком большая, чтобы поместиться в столбец. **Примечание:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента поддерживают подключение к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 и более ранних версий.|  
|SQL_CHAR (допускающий значения NULL)|Если столбец SQL_CHAR допускает значения NULL, при подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии 6.0 или более ранней данные, данные, сохраненные в источник данных, не дополняются пробелами. При получении данных из таких столбцов, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента заполняет их пустыми полями справа. Однако данные, которые создаются в операциях, выполняемых [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (например объединении), не имеют такого заполнения. **Примечание:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента поддерживают подключение к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 и более ранних версий.|  
|SQL_LONGVARBINARY, SQL_LONGVARCHAR, SQL_WLONGVARCHAR|При подключении к экземпляру, полностью поддерживаются обновления столбцов с SQL_LONGVARBINARY, SQL_LONGVARCHAR или SQL_WLONGVARCHAR типы данных (с использованием предложения WHERE), которые влияют на несколько строк [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6. *x* и более поздних версий. При подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 4.2*x*, ошибка S1000, «частичная вставка или обновление. Вставка или обновление столбца text или image не завершено», если обновление затрагивает более одной строки. **Примечание:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента поддерживают подключение к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 и более ранних версий.|  
|Параметры строковых функций|*строковое_выражение* введите параметры в строку функции должны быть данных SQL_CHAR или SQL_VARCHAR. Типы данных SQL_LONG_VARCHAR не поддерживаются в строковых функциях. *Число* параметр должен быть меньше или равен 8000, так как типы данных SQL_CHAR и SQL_VARCHAR ограничены максимальной длиной 8000 символов.|  
|Литералы времени|Литералы времени при сохранении в столбец SQL_TIMESTAMP ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типы данных **datetime** или **smalldatetime**), имеют значение даты 1 января 1900 г.|  
|**timestamp**|Можно вручную вставлять только значение NULL в **timestamp** столбца. Тем не менее так как **timestamp**столбцы автоматически обновляются по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], значение NULL перезаписывается.|  
|**tinyint**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Tinyint** тип данных не имеет знака. Объект **tinyint** столбец привязан к переменной типа данных SQL_C_UTINYINT по умолчанию.|  
|Псевдонимы типов данных|При подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 4.2*x*, драйвер ODBC добавляет значение NULL в определение столбца, допустимость значений NULL столбца явно не объявлен. Поэтому допустимость значений NULL, помещенная в определение псевдонима типа данных, не учитывается.<br /><br /> При подключении к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 4.2*x*, столбцы с типом данных псевдонима с базовых данных тип **char** или **двоичных** и для которого не допустимость значений NULL объявленные создаются как тип данных **varchar** или **varbinary**. [SQLColAttribute](../native-client-odbc-api/sqlcolattribute.md), [SQLColumns](../native-client-odbc-api/sqlcolumns.md), и [SQLDescribeCol](../native-client-odbc-api/sqldescribecol.md) возвращают SQL_VARCHAR и SQL_VARBINARY в качестве данных типа для этих столбцов. Данные, полученные из этих столбцов, не заполнены. **Примечание:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента поддерживают подключение к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 и более ранних версий.|  
|Типы данных большой длины|*данные времени выполнения* параметров ограничены для SQL_LONGVARBINARY и SQL_LONGVARCHAR типы данных.|  
|Типы больших значений|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента будет предоставлять **varchar(max)**, **varbinary(max)**, и **nvarchar(max)** типы как SQL_VARCHAR, SQL_VARBINARY и SQL_ WVARCHAR (соответственно), в API, которые принимают или возвращают типы данных ODBC SQL.|  
|Определяемый пользователем тип|Столбцы определяемого пользователем типа преобразуются в тип данных SQL_SS_UDT. Если столбец определяемого пользователем типа явно сопоставлен с другим типом в инструкции SQL с помощью методов ToString() или ToXMLString() определяемого пользователем типа или с помощью функций CAST/CONVERT, то тип столбца в результирующем наборе будет отражать реальный тип, к которому столбец был преобразован.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента может только привязать столбец определяемого пользователем ТИПА как двоичный файл. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает преобразование только между типами данных SQL_SS_UDT и SQL_C_BINARY.|  
|XML|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматически преобразует XML в текст Юникода. Тип XML преобразуется в SQL_SS_XML.|  
  
## <a name="see-also"></a>См. также  
 [Обработка результатов &#40;ODBC&#41;](processing-results-odbc.md)  
  
  
