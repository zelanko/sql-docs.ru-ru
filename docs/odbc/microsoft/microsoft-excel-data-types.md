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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8574985e10e5aaa3ae5431af7ee1245643e20b60
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81283774"
---
# <a name="microsoft-excel-data-types"></a>Типы данных Microsoft Excel
В следующей таблице показано, как типы данных драйвера Microsoft Excel сопоставляются с типами данных ODBC SQL. Драйвер Microsoft Excel назначает эти типы данных столбцам в таблицах Microsoft Excel на основе данных в столбце.  
  
|Тип данных Microsoft Excel|Тип данных ODBC|  
|-------------------------------|--------------------|  
|CURRENCY|SQL_NUMERIC|  
|DATETIME|SQL_TIMESTAMP|  
|ЛОГИЧЕСКИЙ|SQL_BIT|  
|NUMBER|SQL_DOUBLE|  
|TEXT|SQL_VARCHAR|  
  
> [!NOTE]  
>  **SQLGetTypeInfo** возвращает типы данных ODBC SQL. Все преобразования в приложении D *Справочника программиста ODBC* поддерживаются для типов данных ODBC SQL, перечисленных ранее в этом разделе.  
  
 В следующей таблице приведены ограничения для типов данных Microsoft Excel.  
  
|Тип данных|Описание|  
|---------------|-----------------|  
|Зашифрованные данные|Драйвер Microsoft Excel не может считывать зашифрованные данные.|  
|Строки ошибок|Драйвер Microsoft Excel не может вернуть символьную строку для значений ошибок Microsoft Excel (#N/A!, #VALUE!, #REF!, #DIV/0!, #NUM!, #NAME? и #NULL!), но вместо этого возвращает значение NULL.|  
|ЛОГИЧЕСКИЙ|Значение в ЛОГИЧЕСКОМ столбце возвращается в буфере SQL_C_CHAR как 0 или 1.|  
|NUMBER|Если создается целочисленный столбец, можно ввести числа, которые слишком велики для целочисленного типа данных, и данные, содержащие Нецелочисленные значения, могут быть вставлены, в результате чего столбец можно преобразовать в SQL_DOUBLE.|  
|TEXT|Если строки столбца содержат более одного типа данных Microsoft Excel, драйвер ODBC Microsoft Excel присваивает столбцу SQL_VARCHAR тип данных. Существует одно исключение из этого: если столбец содержит только два или три типа данных DateTime (Дата, время и Дата и время), драйвер ODBC Microsoft Excel присваивает столбцу SQL_TIMESTAMP тип данных.<br /><br /> Создание ТЕКСТОВОГО столбца нулевой или неуказанной длины фактически возвращает 255-байтовый столбец.<br /><br /> Символьная строка символов может содержать любой символ ANSI (1-255 десятичное число). Используйте две последовательные одинарные кавычки (") для представления одной одинарной кавычки (').<br /><br /> Вставка значения NULL в столбец с типом данных, отличным от SQL_VARCHAR, приведет к изменению типа данных столбца на SQL_VARCHAR.|  
  
 Дополнительные ограничения для типов данных можно найти в [ограничениях типа данных](../../odbc/microsoft/data-type-limitations.md).
