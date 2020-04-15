---
title: Типы данных Microsoft Excel Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283774"
---
# <a name="microsoft-excel-data-types"></a>Типы данных Microsoft Excel
В следующей таблице показано, как типы данных драйверов Microsoft Excel отображаются с типами данных ODBC S-L. Драйвер Microsoft Excel присваивает эти типы данных столбикам в таблицах Microsoft Excel на основе данных в столбце.  
  
|Тип данных Microsoft Excel|Тип данных ODBC|  
|-------------------------------|--------------------|  
|CURRENCY|SQL_NUMERIC|  
|DATETIME|SQL_TIMESTAMP|  
|Логических|SQL_BIT|  
|NUMBER|SQL_DOUBLE|  
|TEXT|SQL_VARCHAR|  
  
> [!NOTE]  
>  **SLGetTypeInfo** возвращает типы данных ODBC S'L. Все преобразования в приложении D *Справочника программиста ODBC* поддерживаются для типов данных ODBC S'L, перечисленных ранее в этой теме.  
  
 В следующей таблице отображается ограничения на типы данных Microsoft Excel.  
  
|Тип данных|Описание|  
|---------------|-----------------|  
|Зашифрованные данные|Драйвер Microsoft Excel не может считывать зашифрованные данные.|  
|Строки ошибок|Водитель Microsoft Excel не может вернуть строку символов для значений ошибок Microsoft Excel (#N/A!, #VALUE!, #REF!, #DIV/0!, #NUM!, #NAME?, и #NULL!), но возвращает NULL вместо этого.|  
|Логических|Значение в столбце LOGICAL возвращается в буфер SQL_C_CHAR как 0 или 1.|  
|NUMBER|При создании столбца рядовможно ежей можно ввести слишком большие числа для типа данных рядового числа и вставить данные, содержащие значения, не связанные с числом, в результате чего столбец может быть преобразован в SQL_DOUBLE.|  
|TEXT|Когда строки столбца содержат более одного типа данных Microsoft Excel, драйвер ODBC Microsoft Excel присваивает столбцодуву SQL_VARCHAR тип данных. Исключение из этого имеется одно: если столбец содержит только два или три типа данных по дате (DATE, TIME и DATETIME), то драйвер ODBC Microsoft присваивает столбику SQL_TIMESTAMP тип данных.<br /><br /> Создание столбца TEXT нулевой или неопределенной длины фактически возвращает столбец 255 байт.<br /><br /> Строка символа буквально может содержать любой символ ANSI (1-255 десятичных знаков). Используйте два последовательных одиночных метки () для обозначения одной отметки котировок (').<br /><br /> Вставка NULL в столбец с типом данных, не SQL_VARCHAR приведет к изменению типа данных столбца на SQL_VARCHAR.|  
  
 Дополнительные ограничения на типы данных можно найти в [ограничениях типа данных.](../../odbc/microsoft/data-type-limitations.md)
