---
title: "Типы данных dBASE | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], DBasedriver
- desktop database drivers [ODBC], DBasedriver
- DBase driver [ODBC], data types
- data types [ODBC], DBase driver
- dbase data types [ODBC]
- ODBC desktop database drivers [ODBC], DBasedriver
ms.assetid: a0e31e6b-d02b-4ee2-9b37-5baf6a11c0a6
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 49fb588f5793eb3ee2fce7417632301794a65a22
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="dbase-data-types"></a>Типы данных dBASE
Следующая таблица показывает, как типы данных dBASE сопоставляются с типами данных ODBC SQL. Обратите внимание, что поддерживаются не все типы данных ODBC SQL.  
  
|Тип данных dBASE|Тип данных ODBC|  
|---------------------|--------------------|  
|CHAR|SQL_VARCHAR|  
|DATE|SQL_DATE|  
|ЧИСЛО С ПЛАВАЮЩЕЙ ЗАПЯТОЙ [1]|SQL_DOUBLE|  
|ЛОГИЧЕСКИЙ|SQL_BIT|  
|MEMO|SQL_LONGVARCHAR|  
|ЧИСЛОВОЙ (BCD)|SQL_DOUBLE|  
|OLEOBJECT [1]|SQL_LONGBINARY|  
  
 [1] допустимо только для dBASE версии 5. *x*  
  
 Точность dBASE III допускает чисел с вверх в показатели степени с двумя цифрами, а числа dBASE IV до степени из трех цифр. Поскольку числа хранятся в виде текста, они преобразуются в числа. Если число для преобразования не помещается в поле, могут возникнуть: необъяснимые результаты.  
  
 Хотя dBASE позволяет точностью и масштабом должен быть задан с ЧИСЛОВЫМ типом данных, не поддерживается драйвером ODBC для dBASE. Драйвер ODBC dBASE всегда возвращает точностью 15 и масштабом 0 для ЧИСЛОВОГО типа данных.  
  
 Столбец, созданных с помощью числового типа данных с использованием карт, драйвер ODBC dBASE, в тип данных SQL_DOUBLE ODBC. Таким образом данные в этом столбце — после округления. Такое поведение не соответствует вводе, ЧИСЛОВЫЕ данные в dBASE (тип N), который является двоично-десятичный (BCD).  
  
> [!NOTE]  
>  **SQLGetTypeInfo** возвращает типы данных ODBC SQL. Все преобразования в приложении D *справочнике программиста ODBC* поддерживается для типов данных ODBC SQL, перечисленных ранее в этом разделе.  
  
 В следующей таблице показаны ограничения на dBASE типы данных.  
  
|Тип данных|Description|  
|---------------|-----------------|  
|CHAR|Создание столбца данных типа CHAR нулевое или неизвестной длины фактически возвращает 254-байтовый столбец.|  
|Зашифрованные данные|Драйвер dBASE не поддерживает зашифрованные dBASE таблицы.|  
|ЛОГИЧЕСКИЙ|Драйвер dBASE невозможно создать индекс для ЛОГИЧЕСКОГО столбца.|  
|MEMO|Максимальная длина столбца типа MEMO составляет 65 500 байт.|  
  
 Дополнительные ограничения на типы данных можно найти в [ограничения типа данных](../../odbc/microsoft/data-type-limitations.md).

