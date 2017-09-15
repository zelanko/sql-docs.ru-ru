---
title: "Типы драйвера - данных, дескриптор сведения диагностики | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- driver-specific diagnostic values [ODBC]
- diagnostic information [ODBC], driver-specific values
- ODBC drivers [ODBC], driver-specific diagnostic values
ms.assetid: ad4c76d3-5191-4262-b47c-5dd1d19d1154
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 05aaeca12342ec9d037595ff001a0d1edc745818
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="driver-specific-data-types-descriptor-types-information-types-diagnostic-types-and-attributes"></a>Типов данных драйвера, дескрипторов типов, типов данных, типы диагностики и атрибуты
Драйверы можно выделить драйвера значения для следующего:  
  
-   **Индикаторы тип данных SQL** они используются в *ParameterType* в **SQLBindParameter** и *DataType* в **SQLGetTypeInfo** и возвращенный **SQLColAttribute**, **SQLColumns**, **SQLDescribeCol**, **SQLGetTypeInfo**, ** SQLDescribeParam**, **SQLProcedureColumns**, и **SQLSpecialColumns**.  
  
-   **Поля дескриптора** они используются в *FieldIdentifier* в **SQLColAttribute**, **SQLGetDescField**, и **SQLSetDescField **.  
  
-   **Диагностические поля** они используются в *DiagIdentifier* в **SQLGetDiagField** и **SQLGetDiagRec**.  
  
-   **Сведения о типах** они используются в *свойство* в **SQLGetInfo**.  
  
-   **Инструкция атрибутов соединения и** они используются в *атрибута* в **SQLGetConnectAttr**, **SQLGetStmtAttr**, ** SQLSetConnectAttr**, и **SQLSetStmtAttr**.  
  
 Для каждого из этих элементов, есть два набора значений: Зарезервировано для использования в ODBC и значений зарезервировано для использования с помощью драйверов. Перед реализацией значения драйвера, создатель драйвера должен запросить значение для каждого типа, зависящего от драйвера, поля или атрибута из Open Group. Для новых разработок драйвер используется диапазон, описанные в следующей таблице. Диспетчер драйверов ODBC 3.8 не выдаст ошибку, если используется неизвестное значение, не находится в диапазоне, описанных ниже. Тем не менее более поздних версиях диспетчера драйверов может возникнуть ошибка, если неизвестные значения, которые не находятся в диапазоне принимаются.  
  
 Когда эти значения передается в функцию ODBC, драйвер должен проверять, является ли допустимым значение. Драйверы возвращают SQLSTATE HYC00 (дополнительная возможность не реализована) для конкретного драйвера значений, которые применяются для других драйверов.  
  
 Начиная с ODBC 3.8, драйвер записи можно выделить атрибутов драйвера в зарезервированном диапазоне.  
  
> [!NOTE]  
>  Диспетчер драйверов ODBC 3.8 не проверяет и не обеспечивает выполнение этих диапазонов для обеспечения обратной совместимости. Будущие версии диспетчера драйверов может применять их, однако.  
  
|Тип атрибута|Тип данных ODBC|Базовый диапазона драйвера|Размер диапазона драйвера|Константа ODBC для драйвера значение диапазона базового|  
|--------------------|--------------------|---------------------------------|----------------------------------|---------------------------------------------------------|  
|Индикаторы тип данных SQL|SQLSMALLINT|0x4000|0x7FFF|SQL_DRIVER_SQL_TYPE_BASE|  
|Поля дескриптора|SQLSMALLINT|0x4000|0x7FFF|SQL_DRIVER_DESCRIPTOR_BASE|  
|Диагностические поля|SQLSMALLINT|0x4000|0x7FFF|SQL_DRIVER_DIAGNOSTIC_BASE|  
|Типы данных|SQLUSMALLINT|0x4000|0x7FFF|SQL_DRIVER_INFO_TYPE_BASE|  
|Атрибуты соединения|SQLINTEGER|0x00004000|0x00007FFF|SQL_DRIVER_CONNECT_ATTR_BASE|  
|Атрибуты инструкции|SQLINTEGER|0x00004000|0x00007FFF|SQL_DRIVER_STATEMENT_ATTR_BASE|  
  
> [!NOTE]  
>  Типы данных, поля дескриптора, диагностические поля, типы информации, атрибутов инструкции и атрибуты соединения должны быть описаны в документации по драйверу. Когда эти значения передается в функцию ODBC, драйвер должен проверять, является ли допустимым значение. Драйверы возвращают SQLSTATE HYC00 (дополнительная возможность не реализована) для конкретного драйвера значений, которые применяются для других драйверов.  
  
 Базовые значения определены для упрощения разработки драйвера. Например можно определить определенные атрибуты диагностики драйвера в следующем формате:  
  
```  
SQL_DRIVER_DIAGNOSTIC_BASE+0, SQL_DRIVER_DIAGNOSTIC_BASE +1  
```
