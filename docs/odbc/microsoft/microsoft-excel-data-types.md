---
title: "Типы данных Microsoft Excel | Документы Microsoft"
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
- data types [ODBC], Excel driver
- Excel data types [ODBC]
- Jet-based ODBC drivers [ODBC], Excel driver
- desktop database drivers [ODBC], Excel driver
- ODBC desktop database drivers [ODBC], Excel driver
- Excel driver [ODBC], data types
ms.assetid: 7b44c8e5-0bc3-4912-8a5d-56f4d5562fe6
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: eeb2bc72ce34141eb3dbdca3f952dca0c476c2dd
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="microsoft-excel-data-types"></a>Типы данных Microsoft Excel
Следующая таблица показывает сопоставление типов данных драйвера Microsoft Excel в типы данных ODBC SQL. Драйвер Microsoft Excel назначает эти типы данных столбцов в таблицы Microsoft Excel на основе данных в столбце.  
  
|Тип данных Microsoft Excel|Тип данных ODBC|  
|-------------------------------|--------------------|  
|CURRENCY|SQL_NUMERIC|  
|DATETIME|SQL_TIMESTAMP|  
|ЛОГИЧЕСКИЙ|SQL_BIT|  
|NUMBER|SQL_DOUBLE|  
|TEXT|SQL_VARCHAR|  
  
> [!NOTE]  
>  **SQLGetTypeInfo** возвращает типы данных ODBC SQL. Все преобразования в приложении D *справочнике программиста ODBC* поддерживается для типов данных ODBC SQL, перечисленных ранее в этом разделе.  
  
 Ниже приведены ограничения на типы данных Microsoft Excel.  
  
|Тип данных|Description|  
|---------------|-----------------|  
|Зашифрованные данные|Драйвер Microsoft Excel не удается прочитать зашифрованные данные.|  
|Строки сообщений об ошибках|Драйвер Microsoft Excel не может возвращать строку символов для значения ошибок Microsoft Excel (# н/д!, #VALUE!, #REF!, #DIV/0!, #NUM!, #NAME? и #NULL!), но вместо этого возвращает значение NULL.|  
|ЛОГИЧЕСКИЙ|Значение в ЛОГИЧЕСКИЙ столбец возвращается в буфере SQL_C_CHAR как 0 или 1.|  
|NUMBER|Если создается целочисленном столбце, можно ввести номера, которые слишком велики для типа данных integer и не целочисленные значения, содержащие данные могут быть вставлены с результатом, что столбец может быть преобразован в SQL_DOUBLE.|  
|TEXT|Если строки столбца содержат более одного типа данных Microsoft Excel, драйвер ODBC Microsoft Excel присваивает столбцу типа данных SQL_VARCHAR. Есть одно исключение: Если столбец содержит только двух-трех типов данных даты и времени (даты, времени и даты и времени), драйвер ODBC Microsoft Excel присваивает тип данных SQL_TIMESTAMP столбцу.<br /><br /> Создание ТЕКСТОВОГО столбца, равную нулю или неизвестной длины фактически возвращает столбец 255 байт.<br /><br /> Символьного литерала могут содержать любой символ ANSI (1-255 в десятичном формате). Используйте две стоящие рядом одинарные кавычки ("") для представления символ одинарной кавычки (').<br /><br /> Вставка значения NULL в столбец с типом данных, отличный от SQL_VARCHAR вызовет тип данных столбца, который следует изменить на SQL_VARCHAR.|  
  
 Дополнительные ограничения на типы данных можно найти в [ограничения типа данных](../../odbc/microsoft/data-type-limitations.md).
