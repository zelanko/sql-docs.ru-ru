---
title: Типы данных DateTime | Документация Майкрософт
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68130093"
---
# <a name="datetime-data-types"></a>Типы данных даты и времени
В ODBC *3. x*идентификаторы типов данных SQL даты, времени и timestamp изменились с SQL_DATE, SQL_TIME и SQL_TIMESTAMP (с экземплярами **#define** в файле заголовка 9, 10 и 11) на SQL_TYPE_DATE, SQL_TYPE_TIME и SQL_TYPE_TIMESTAMP (с экземплярами **#define** в файле заголовка 91, 92 и 93) соответственно. Соответствующие идентификаторы типа C изменились с SQL_C_DATE, SQL_C_TIME и SQL_C_TIMESTAMP на SQL_C_TYPE_DATE, SQL_C_TYPE_TIME и SQL_C_TYPE_TIMESTAMP соответственно, а экземпляры **#define** соответственно изменились.  
  
 Размер столбца и десятичные цифры, возвращаемые для типов данных SQL datetime в ODBC *3. x* , совпадают с точностью и масштабом, возвращаемым для них в ODBC *2. x*. Эти значения отличаются от значений в полях дескриптора SQL_DESC_PRECISION и SQL_DESC_SCALE. (Дополнительные сведения см. в разделе [размер столбца, десятичные цифры, длина октета и размер дисплея](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) в приложении г: типы данных.)  
  
 Эти изменения влияют на **SQLDescribeCol**, **SQLDescribeParam**и **SQLColAttributes**; **SQLBindCol**, **SQLBindParameter**и **SQLGetData**; и **SQLColumns**, **SQLGetTypeInfo**, **SQLProcedureColumns**, **SQLStatistics**и **SQLSpecialColumns**.  
  
 Драйвер ODBC *3. x* обрабатывает вызовы функций, перечисленные в предыдущем абзаце, в соответствии с настройкой атрибута среды SQL_ATTR_ODBC_VERSION. Для **SQLColumns**, **SQLGetTypeInfo**, **SQLProcedureColumns**, **SQLSpecialColumns**и **SQLStatistics**, если SQL_ATTR_ODBC_VERSION имеет значение SQL_OV_ODBC3, функции возвращают SQL_TYPE_DATE, SQL_TYPE_TIME и SQL_TYPE_TIMESTAMP в поле data_type. Столбец COLUMN_SIZE (в результирующем наборе, возвращаемом **SQLColumns**, **SQLGetTypeInfo**, **SQLProcedureColumns**и **SQLSpecialColumns**) содержит двоичную точность для приблизительного числового типа. Столбец NUM_PREC_RADIX (в результирующем наборе, возвращаемом **SQLColumns**, **SQLGetTypeInfo**и **SQLProcedureColumns**) содержит значение 2. Если SQL_ATTR_ODBC_VERSION имеет значение SQL_OV_ODBC2, функции возвращают SQL_DATE, SQL_TIME и SQL_TIMESTAMP в поле DATA_TYPE, столбец COLUMN_SIZE содержит десятичную точность для приблизительного числового типа, а столбец NUM_PREC_RADIX содержит значение 10.  
  
 Когда все типы данных запрашиваются при вызове **SQLGetTypeInfo**, результирующий набор, возвращаемый функцией, будет содержать как SQL_TYPE_DATE, SQL_TYPE_TIME, так и SQL_TYPE_TIMESTAMP, как определено в ODBC *3. x*, SQL_DATE, SQL_TIME и SQL_TIMESTAMP, как определено в ODBC *2. x*.  
  
 Из-за того, как диспетчер драйверов ODBC *3. x* выполняет сопоставление даты, типы данных времени и отметок времени, драйверы ODBC *3. x* должны распознать только **#defines** 91, 92 и 93 для типов данных даты, времени и отметки времени C, вводимых в аргументах *TargetType* для **SQLBindCol** и **SQLGetData** или аргумента *ValueType* **SQLBindParameter**, и необходимо распознать только **#defines** из 91, 92 и 93 для типов данных SQL даты, времени и timestamp, вводимых в Аргумент *ParameterType* **SQLBindParameter** или аргумент *DataType* **SQLGetTypeInfo**. Дополнительные сведения см. в разделе [изменения типа данных DateTime](../../../odbc/reference/develop-app/datetime-data-type-changes.md).
