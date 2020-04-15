---
title: Изменения типа данных на дату (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- time data type [ODBC]
- datetime data types [ODBC]
- date data type [ODBC]
- backward compatibility [ODBC], datetime data types
- timestamp data type [ODBC]
- compatibility [ODBC], datetime data types
ms.assetid: c38c79f9-8bb0-4633-ac86-542366c09a95
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4f186047dd31aa2c4b66ec1ce73c8cb9fae31c04
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304647"
---
# <a name="datetime-data-type-changes"></a>Изменения в типе данных Datetime
В ODBC *3.x*, идентификаторы для даты, времени и типы данных timestamp S'L изменились с SQL_DATE, SQL_TIME и SQL_TIMESTAMP (с экземплярами **#define** в файле заголовка 9, 10 и 11) до SQL_TYPE_DATE, SQL_TYPE_TIME и SQL_TYPE_TIMESTAMP (с экземплярами **#define** в файле заголовка 91, 92 и 93), соответственно. Соответствующие идентификаторы типа C изменились с SQL_C_DATE, SQL_C_TIME и SQL_C_TIMESTAMP на SQL_C_TYPE_DATE, SQL_C_TYPE_TIME и SQL_C_TYPE_TIMESTAMP соответственно.  
  
 Размер столбца и десятичные цифры, возвращенные для типов данных о дате S'L в ODBC *3.x,* такие же, как точность и масштаб, возвращенные для них в ODBC *2.x.* Эти значения отличаются от значений в полях SQL_DESC_PRECISION и SQL_DESC_SCALE дескриптора. (Для получения дополнительной информации [см. Размер столбца, десятичные цифры, длина передачи Octet и размер дисплея](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).)  
  
 Эти изменения влияют на **S'LDescribeCol**, **S'LDescribeParam**, и **S'LColAttribute**; **СЗЛБиндкол,** **СЗЛБандерПарастер**, и **S'LGetData**; и **S'LКолонки**, **S'LGetTypeInfo**, **S'LProcedureColumns**, **S'LСтатистика**, и **S'LSpecialКолонки**.  
  
 В следующей таблице показано, как менеджер драйверов ODBC *3.x* выполняет отображение типов данных даты, времени и метки времени C, введенных в аргументы *TargetType,* в которые приведены аргументы **S'LBindCol** и **S'LGetData** или в аргументе *ValueType* **s'LBindParameter.**  
  
|Тип данных<br /><br /> код вошел|*2.x* приложение для<br /><br /> *2.x* драйвер|*2.x* приложение для<br /><br /> *3.x* драйвер|*3.x* приложение для<br /><br /> *2.x* драйвер|*3.x* приложение для<br /><br /> *3.x* драйвер|  
|--------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|  
|SQL_C_DATE (9)|Без сопоставления|SQL_C_TYPE_DATE (91)|Нет отображения|SQL_C_TYPE_DATE (91)|  
|SQL_C_TYPE_DATE (91)|Ошибка (от DM)|Ошибка (от DM)|SQL_C_DATE (9)|Нет отображения|  
|SQL_C_TIME (10)|Без сопоставления|SQL_C_TYPE_TIME (92)|Нет отображения|SQL_C_TYPE_TIME (92)|  
|SQL_C_TYPE_TIME (92)|Ошибка (от DM)|Ошибка (от DM)|SQL_C_TIME (10)|Нет отображения|  
|SQL_C_TIMESTAMP (11)|Без сопоставления|SQL_C_TYPE_TIMESTAMP (93)|Нет отображения|SQL_C_TYPE_TIMESTAMP (93)|  
|SQL_C_TYPE_TIMESTAMP (93)|Ошибка (от DM)|Ошибка (от DM)|SQL_C_TIMESTAMP (11)|Нет отображения|  
  
 В результате этого приложение ODBC *3.x,* работая с драйвером ODBC *2.x,* может использовать коды даты, времени или метки времени, возвращенные в наборы результатов, которые возвращаются функциями каталога.  
  
 В результате этого приложение ODBC *3.x,* работая с драйвером ODBC *3.x,* может использовать коды даты, времени или метки времени, возвращенные в наборы результатов, которые возвращаются функциями каталога.  
  
 В следующей таблице показано, как менеджер драйверов ODBC *3.x* выполняет отображение даты, времени и типов данных на метки времени, введенных в аргумент *ParameterType* **s'LBindParameter** или в аргументе *DataType* **компании S'LGetTypeInfo.**  
  
|Тип данных<br /><br /> код вошел|*2.x* приложение для<br /><br /> *2.x* драйвер|*2.x* приложение для<br /><br /> *3.x* драйвер|*3.x* приложение для<br /><br /> *2.x* драйвер|*3.x* приложение для<br /><br /> *3.x* драйвер|  
|--------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|  
|SQL_DATE (9)|Без сопоставления|SQL_TYPE_DATE (91)|Нет отображения|SQL_TYPE_DATE (91)|  
|SQL_TYPE_DATE (91)|Ошибка (от DM)|Ошибка (от DM)|SQL_DATE (9)|Нет отображения|  
|SQL_TIME (10)|Без сопоставления|SQL_TYPE_TIME (92)|Нет отображения|SQL_TYPE_TIME (92)|  
|SQL_TYPE_TIME (92)|Ошибка (от DM)|Ошибка (от DM)|SQL_TIME (10)|Нет отображения|  
|SQL_TIMESTAMP (11)|Без сопоставления|SQL_TYPE_TIMESTAMP (93)|Нет отображения|SQL_TYPE_TIMESTAMP (93)|  
|SQL_TYPE_TIMESTAMP (93)|Ошибка (от DM)|Ошибка (от DM)|SQL_TIMESTAMP (11)|Нет отображения|  
  
 В результате этого приложение ODBC *3.x,* работая с драйвером ODBC *2.x,* может использовать коды даты, времени или метки времени, возвращенные в наборы результатов, которые возвращаются функциями каталога.  
  
 В результате этого приложение ODBC *3.x,* работая с драйвером ODBC *3.x,* может использовать коды даты, времени или метки времени, возвращенные в наборы результатов, которые возвращаются функциями каталога.
