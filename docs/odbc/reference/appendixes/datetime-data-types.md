---
title: "Типы данных даты и времени | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 92ab5f52282fddf89c48bef73fa7817684ae3496
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="datetime-data-types"></a>Типы данных даты и времени
В ODBC 3*.x*, идентификаторы для даты, времени и типы данных timestamp SQL были изменены из SQL_DATE, SQL_TIME и SQL_TIMESTAMP (экземплярами **#define** в файле заголовка, 9, 10 и 11) для SQL_ TYPE_DATE, SQL_TYPE_TIME и SQL_TYPE_TIMESTAMP (экземплярами **#define** в файле заголовка 91, 92 и 93) соответственно. Соответствующий тип C идентификаторы измененных с SQL_C_DATE, SQL_C_TIME и SQL_C_TIMESTAMP SQL_C_TYPE_DATE, SQL_C_TYPE_TIME и SQL_C_TYPE_TIMESTAMP, соответственно и экземпляры **#define** были изменены соответствующим образом.  
  
 Размер столбца и десятичных цифр, возвращаемых для типов данных даты и времени SQL в ODBC 3*.x* являются таким же, как точность и масштаб возвращается для них в ODBC 2. *x*. Эти значения могут отличаться от значений в полях дескриптора SQL_DESC_PRECISION и SQL_DESC_SCALE. (Дополнительные сведения см. в разделе [размер столбца, десятичных цифр, длина в октетах передачи и отображаемый размер](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) в типах данных приложение г.)  
  
 Эти изменения влияют на **SQLDescribeCol**, **SQLDescribeParam**, и **SQLColAttributes**; **SQLBindCol**, **SQLBindParameter**, и **SQLGetData**; и **SQLColumns**, **SQLGetTypeInfo** , **SQLProcedureColumns**, **SQLStatistics**, и **SQLSpecialColumns**.  
  
 ODBC 3*.x* драйвер обрабатывает вызовы функций, перечисленных в предыдущем абзаце согласно настройке атрибута SQL_ATTR_ODBC_VERSION среды. Для **SQLColumns**, **SQLGetTypeInfo**, **SQLProcedureColumns**, **SQLSpecialColumns**, и **SQLStatistics** , если SQL_ATTR_ODBC_VERSION задано значение SQL_OV_ODBC3, функции возвращают SQL_TYPE_DATE, SQL_TYPE_TIME и SQL_TYPE_TIMESTAMP в тип данных поля. Столбца COLUMN_SIZE (в результирующий набор, возвращенный **SQLColumns**, **SQLGetTypeInfo**, **SQLProcedureColumns**, и **SQLSpecialColumns**) содержит точность двоичного представления для приблизительный числовой тип. Столбец NUM_PREC_RADIX (в результирующий набор, возвращенный **SQLColumns**, **SQLGetTypeInfo**, и **SQLProcedureColumns**) содержит значение 2. Если SQL_ATTR_ODBC_VERSION имеет значение SQL_OV_ODBC2, то функции возвращаемого SQL_DATE, SQL_TIME и SQL_TIMESTAMP в поле DATA_TYPE, столбца COLUMN_SIZE содержит десятичную точность для приблизительный числовой тип, а столбец NUM_PREC_RADIX содержит значение 10.  
  
 Когда запрашиваются все типы данных в вызове **SQLGetTypeInfo**, результирующий набор, возвращаемый функцией будет содержать SQL_TYPE_DATE, SQL_TYPE_TIME и SQL_TYPE_TIMESTAMP, как определено в ODBC 3*.x*, и SQL_DATE, SQL_TIME и SQL_TIMESTAMP, как определено в ODBC 2. *x*.  
  
 Из-за как ODBC 3*.x* диспетчера драйверов выполняет сопоставление типов даты, времени и отметок времени данных, ODBC 3*.x* драйверы нужно будет только выбрать **#defines** 91, 92, и 93 для даты, времени и типы данных timestamp C введено в *TargetType* аргументы **SQLBindCol** и **SQLGetData** или  *ValueType* аргумент **SQLBindParameter**и нужно будет только выбрать **#defines** 91, 92 и 93 для даты, времени и типы данных timestamp SQL, введенных в *ParameterType* аргумент **SQLBindParameter** или *DataType* аргумент **SQLGetTypeInfo**. Дополнительные сведения см. в разделе [изменения типов данных даты и времени](../../../odbc/reference/develop-app/datetime-data-type-changes.md).

