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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 17b96ad0b6674a2d120ef46d9bfa221e8df6d140
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307695"
---
# <a name="dbase-data-types"></a>Типы данных dBASE
В следующей таблице показано, как типы данных dBASE сопоставляются с типами данных ODBC SQL. Обратите внимание, что поддерживаются не все типы данных ODBC SQL.  
  
|тип данных dBASE|Тип данных ODBC|  
|---------------------|--------------------|  
|CHAR|SQL_VARCHAR|  
|DATE|SQL_DATE|  
|FLOAT [1]|SQL_DOUBLE|  
|ЛОГИЧЕСКИЙ|SQL_BIT|  
|ПОЛУЧЕНА|SQL_LONGVARCHAR|  
|NUMERIC (BCD)|SQL_DOUBLE|  
|OLECONTROL [1]|SQL_LONGBINARY|  
  
 [1] допустимо только для dBASE версии 5. *x*  
  
 Точность в dBASE III позволяет выполнять числа с экспонентой до двух цифр и в числах dBASE IV с экспонентой до трех цифр. Поскольку числа хранятся в виде текста, они преобразуются в числа. Если число для преобразования не умещается в поле, могут возникать необъяснимые результаты.  
  
 В то время как dBASE позволяет указывать точность и масштаб с ЧИСЛОВым типом данных, он не поддерживается драйвером ODBC dBASE. Драйвер ODBC dBASE всегда возвращает точность 15 и масштаб 0 для ЧИСЛового типа данных.  
  
 Столбец, созданный с использованием числового типа данных с помощью драйвера ODBC dBASE, сопоставляется с типом данных SQL_DOUBLE ODBC. Поэтому данные в этом столбце подчиняются округлению. Это поведение отличается от ЧИСЛового типа данных в dBASE (тип N), который является двоично-кодированной десятичной запятой (BCD).  
  
> [!NOTE]  
>  **SQLGetTypeInfo** возвращает типы данных ODBC SQL. Все преобразования в приложении D *Справочника программиста ODBC* поддерживаются для типов данных ODBC SQL, перечисленных ранее в этом разделе.  
  
 В следующей таблице приведены ограничения для типов данных dBASE.  
  
|Тип данных|Описание|  
|---------------|-----------------|  
|CHAR|Создание столбца CHAR нулевой или неуказанной длины фактически возвращает 254-байтовый столбец.|  
|Зашифрованные данные|Драйвер dBASE не поддерживает зашифрованные таблицы dBASE.|  
|ЛОГИЧЕСКИЙ|Драйверу dBASE не удается создать индекс для логического столбца.|  
|ПОЛУЧЕНА|Максимальная длина столбца МЕМО составляет 65 500 байт.|  
  
 Дополнительные ограничения для типов данных можно найти в [ограничениях типа данных](../../odbc/microsoft/data-type-limitations.md).
