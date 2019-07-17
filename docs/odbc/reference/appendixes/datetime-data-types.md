---
title: Типы данных даты и времени | Документация Майкрософт
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
- data types [ODBC], date
- backward compatibility [ODBC], datetime data types
- timestamp data type [ODBC]
- data types [ODBC], timestamp
- data types [ODBC], backward compatibility
- compatibility [ODBC], datetime data types
- data types [ODBC], time
ms.assetid: 6b9363c9-04bf-4492-a210-7aa15dea4af8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1cb92afa9467717b8a589ddbcaee4ab8a5a529f6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68130093"
---
# <a name="datetime-data-types"></a>Типы данных даты и времени
В ODBC *3.x*, идентификаторы для даты, времени и типы данных timestamp SQL были изменены относительно SQL_DATE, SQL_TIME и SQL_TIMESTAMP (экземплярами **#define** в файле заголовка, 9, 10 и 11) для SQL_ TYPE_DATE, SQL_TYPE_TIME и SQL_TYPE_TIMESTAMP (экземплярами **#define** в файле заголовка, 91, 92 и 93), соответственно. Соответствующий тип C идентификаторы были изменены относительно SQL_C_DATE SQL_C_TIME и SQL_C_TIMESTAMP SQL_C_TYPE_DATE SQL_C_TYPE_TIME и SQL_C_TYPE_TIMESTAMP, соответственно и в экземплярах **#define** были изменены соответствующим образом.  
  
 Размер столбца и десятичных цифр, возвращаемых для типов данных даты и времени SQL в ODBC *3.x* являются, так же, как точность и масштаб возвращается для них в ODBC *2.x*. Эти значения могут отличаться от значений в полях дескриптора SQL_DESC_PRECISION и SQL_DESC_SCALE. (Дополнительные сведения см. в разделе [размер столбца, десятичных разрядов, длительность октета передачи и отображаемый размер](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) в приложение г Типы данных).  
  
 Эти изменения влияют на **SQLDescribeCol**, **SQLDescribeParam**, и **SQLColAttributes**; **SQLBindCol**, **SQLBindParameter**, и **SQLGetData**; и **SQLColumns**, **SQLGetTypeInfo** , **SQLProcedureColumns**, **SQLStatistics**, и **SQLSpecialColumns**.  
  
 ODBC *3.x* драйвер обрабатывает вызовы функций, перечисленных в предыдущем абзаце в соответствии с настройкой атрибута SQL_ATTR_ODBC_VERSION среды. Для **SQLColumns**, **SQLGetTypeInfo**, **SQLProcedureColumns**, **SQLSpecialColumns**, и **SQLStatistics** , если SQL_ATTR_ODBC_VERSION присваивается значение SQL_OV_ODBC3, функции возвращают результат SQL_TYPE_DATE, SQL_TYPE_TIME и SQL_TYPE_TIMESTAMP в поле DATA_TYPE. В столбце COLUMN_SIZE (в результирующий набор, возвращаемый **SQLColumns**, **SQLGetTypeInfo**, **SQLProcedureColumns**, и **SQLSpecialColumns**) содержит двоичной точностью для приблизительного числового типа. Столбец NUM_PREC_RADIX (в результирующий набор, возвращаемый **SQLColumns**, **SQLGetTypeInfo**, и **SQLProcedureColumns**) содержит значение 2. Если SQL_ATTR_ODBC_VERSION имеет значение SQL_OV_ODBC2, а затем функции возврата SQL_DATE, SQL_TIME и SQL_TIMESTAMP в поле DATA_TYPE, столбца COLUMN_SIZE содержит десятичную точность для приблизительного числового типа, а столбец NUM_PREC_RADIX содержит значение 10.  
  
 При запросе всех типов данных в вызове **SQLGetTypeInfo**, результирующий набор, возвращаемый функцией будет содержать SQL_TYPE_DATE, SQL_TYPE_TIME и SQL_TYPE_TIMESTAMP, как определено в ODBC *3.x*, и SQL_DATE, SQL_TIME и SQL_TIMESTAMP, как определено в ODBC *2.x*.  
  
 Из-за как ODBC *3.x* диспетчера драйверов выполняет сопоставление типов date, time и timestamp данных, ODBC *3.x* драйверы нужно будет только выбрать **#defines** 91, 92, и Введенный 93 для даты, времени и типы данных timestamp C в *TargetType* аргументы **SQLBindCol** и **SQLGetData** или  *ValueType* аргумент **SQLBindParameter**и нужно будет только выбрать **#defines** 91, 92 и 93 для даты, времени и типы данных timestamp SQL, введенные в *ParameterType* аргумент **SQLBindParameter** или *DataType* аргумент **SQLGetTypeInfo**. Дополнительные сведения см. в разделе [изменения типов данных даты и времени](../../../odbc/reference/develop-app/datetime-data-type-changes.md).
