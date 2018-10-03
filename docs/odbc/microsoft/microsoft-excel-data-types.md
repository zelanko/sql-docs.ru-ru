---
title: Типы данных Microsoft Excel | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], Excel driver
- Excel data types [ODBC]
- Jet-based ODBC drivers [ODBC], Excel driver
- desktop database drivers [ODBC], Excel driver
- ODBC desktop database drivers [ODBC], Excel driver
- Excel driver [ODBC], data types
ms.assetid: 7b44c8e5-0bc3-4912-8a5d-56f4d5562fe6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 10695dd9bf044e270bb1ce1d26de78e53a1dd85a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47656762"
---
# <a name="microsoft-excel-data-types"></a>Типы данных Microsoft Excel
В следующей таблице показаны в сопоставлении типов данных драйвера Microsoft Excel в типы данных ODBC SQL. Драйвер Microsoft Excel назначает эти типы данных столбцов в таблицы Microsoft Excel на основе данных в столбце.  
  
|Тип данных Microsoft Excel|Тип данных ODBC|  
|-------------------------------|--------------------|  
|CURRENCY|SQL_NUMERIC|  
|DATETIME|SQL_TIMESTAMP|  
|ЛОГИЧЕСКИЙ|SQL_BIT|  
|NUMBER|SQL_DOUBLE|  
|TEXT|SQL_VARCHAR|  
  
> [!NOTE]  
>  **SQLGetTypeInfo** возвращает типы данных ODBC SQL. Все преобразования в приложении D *Справочник по программированию ODBC* поддерживаются для типов данных ODBC SQL, перечисленных ранее в этом разделе.  
  
 Ниже приведены ограничения на типы данных Microsoft Excel.  
  
|Тип данных|Описание|  
|---------------|-----------------|  
|Зашифрованные данные|Драйвер Microsoft Excel не удается прочитать зашифрованные данные.|  
|Строки сообщений об ошибках|Драйвер Microsoft Excel не может возвращать строку символов для значения ошибок Microsoft Excel (#N/A!, #VALUE!, #REF!, #DIV/0!, #NUM!, #NAME? и #NULL!), но вместо этого возвращает значение NULL.|  
|ЛОГИЧЕСКИЙ|Значение в ЛОГИЧЕСКИЙ столбец возвращается в буфере SQL_C_CHAR как 0 или 1.|  
|NUMBER|Если создан целочисленного столбца, можно ввести номера, которые слишком большое значение для типа данных integer, и данные, содержащие не целочисленные значения могут быть вставлены с результатом, что столбец может быть преобразовано в SQL_DOUBLE.|  
|TEXT|Если строк в столбце содержится более одного типа данных в Microsoft Excel, драйвер ODBC Microsoft Excel устанавливает тип данных SQL_VARCHAR к столбцу. Есть одно исключение: Если столбец содержит только двух-трех типов данных даты и времени (даты, времени и даты и времени), драйвер ODBC Microsoft Excel устанавливает тип данных SQL_TIMESTAMP для столбца.<br /><br /> Создание ТЕКСТОВОГО столбца нулевое или неизвестной длины на самом деле возвращает столбец 255 байт.<br /><br /> Символ строковый литерал может содержать любой символ ANSI (десятичное число от 1 до 255). Используйте две стоящие рядом одинарные кавычки ("") для представления одинарной кавычки (').<br /><br /> Вставка значения NULL в столбец с типом данных, отличных от SQL_VARCHAR вызовет тип данных столбца, чтобы изменить для SQL_VARCHAR.|  
  
 Дополнительные ограничения на типы данных можно найти в [ограничения типов данных](../../odbc/microsoft/data-type-limitations.md).
