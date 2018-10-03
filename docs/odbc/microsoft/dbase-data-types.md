---
title: Типы данных dBASE | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], DBasedriver
- desktop database drivers [ODBC], DBasedriver
- DBase driver [ODBC], data types
- data types [ODBC], DBase driver
- dbase data types [ODBC]
- ODBC desktop database drivers [ODBC], DBasedriver
ms.assetid: a0e31e6b-d02b-4ee2-9b37-5baf6a11c0a6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fc4b4c7a5c1074a62bf0e84d265840109f65ea55
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47626272"
---
# <a name="dbase-data-types"></a>Типы данных dBASE
В следующей таблице показаны как типы данных dBASE сопоставляются типы данных ODBC SQL. Обратите внимание на то, что поддерживаются не все типы данных ODBC SQL.  
  
|Тип данных dBASE|Тип данных ODBC|  
|---------------------|--------------------|  
|CHAR|SQL_VARCHAR|  
|DATE|SQL_DATE|  
|ЧИСЛО С ПЛАВАЮЩЕЙ ЗАПЯТОЙ [1]|SQL_DOUBLE|  
|ЛОГИЧЕСКИЙ|SQL_BIT|  
|MEMO|SQL_LONGVARCHAR|  
|ЧИСЛОВОЙ (BCD)|SQL_DOUBLE|  
|КЛАССЫ OLEOBJECT [1]|SQL_LONGBINARY|  
  
 [1] допустимо только для dBASE версии 5. *x*  
  
 Точность в dBASE III допускает чисел с копии показатели степени с двумя цифрами и dBASE IV чисел с до степени из трех цифр. Поскольку числа хранятся в виде текста, они преобразуются в числа. Если число для преобразования не помещается в поле, могут возникнуть необъяснимых результаты.  
  
 Хотя dBASE позволяет точностью и масштабом указывать с ЧИСЛОВЫМ типом данных, не поддерживается драйвером ODBC для dBASE. Драйвер для dBASE ODBC всегда возвращает точностью 15 и масштабом 0 для ЧИСЛОВОГО типа данных.  
  
 Столбец, созданных с помощью числового типа данных с использованием карт, драйвер ODBC для dBASE, к типу данных SQL_DOUBLE ODBC. Таким образом данные в этот столбец является округления. Это поведение отличается при вводе, ЧИСЛОВЫХ данных в dBASE (тип N), который является двоично-десятичный (BCD).  
  
> [!NOTE]  
>  **SQLGetTypeInfo** возвращает типы данных ODBC SQL. Все преобразования в приложении D *Справочник по программированию ODBC* поддерживаются для типов данных ODBC SQL, перечисленных ранее в этом разделе.  
  
 Ниже приведены ограничения на dBASE типов данных.  
  
|Тип данных|Описание|  
|---------------|-----------------|  
|CHAR|Создание столбца данных типа CHAR нулевое или неизвестной длины на самом деле возвращает 254-байтовый столбец.|  
|Зашифрованные данные|Драйвер для dBASE не поддерживает зашифрованные dBASE таблицы.|  
|ЛОГИЧЕСКИЙ|Драйвер для dBASE невозможно создать индекс по столбцу ЛОГИЧЕСКИХ.|  
|MEMO|Максимальная длина столбца типа MEMO составляет 65 500 байт.|  
  
 Дополнительные ограничения на типы данных можно найти в [ограничения типов данных](../../odbc/microsoft/data-type-limitations.md).
