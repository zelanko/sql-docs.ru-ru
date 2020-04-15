---
title: dBASE Типы данных Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307695"
---
# <a name="dbase-data-types"></a>Типы данных dBASE
В следующей таблице показано, как типы данных dBASE отображаются к типам данных ODBC S'L. Обратите внимание, что не все типы данных ODBC S'L поддерживаются.  
  
|тип данных dBASE|Тип данных ODBC|  
|---------------------|--------------------|  
|CHAR|SQL_VARCHAR|  
|DATE|SQL_DATE|  
|ПОПЛАВОК|SQL_DOUBLE|  
|Логических|SQL_BIT|  
|Памятка|SQL_LONGVARCHAR|  
|NUMERIC (BCD)|SQL_DOUBLE|  
|ОЛЕОБЪЕКТ|SQL_LONGBINARY|  
  
 Действительно только для dBASE версии 5. *x*  
  
 Точность в dBASE III позволяет номера с до двузначных экспонентов и в dBASE IV номера с до трехзначных экспонентов. Поскольку числа хранятся как текст, они преобразуются в числа. Если число для преобразования не вписывается в поле, могут возникнуть необъяснимые результаты.  
  
 Хотя dBASE позволяет указывать точность и шкалу с типом данных NUMERIC, она не поддерживается драйвером ODBC dBASE. Драйвер ODBC dBASE всегда возвращает точность 15 и шкалу 0 для типа данных NUMERIC.  
  
 Столбец, созданный с помощью типа численных данных с использованием карт драйверов ODBC dBASE для SQL_DOUBLE типа данных ODBC. Таким образом, данные в этой колонке подлежат округлениям. Это поведение не то же самое, что и тип данных NUMERIC в dBASE (тип N), который является двоичным кодом десятичной (BCD).  
  
> [!NOTE]  
>  **SLGetTypeInfo** возвращает типы данных ODBC S'L. Все преобразования в приложении D *Справочника программиста ODBC* поддерживаются для типов данных ODBC S'L, перечисленных ранее в этой теме.  
  
 В следующей таблице отображается ограничения на типы данных dBASE.  
  
|Тип данных|Описание|  
|---------------|-----------------|  
|CHAR|Создание столбца CHAR нулевой или неопределенной длины фактически возвращает столбец 254 байт.|  
|Зашифрованные данные|Драйвер dBASE не поддерживает зашифрованные таблицы dBASE.|  
|Логических|Драйвер dBASE не может создать индекс на столбце LOGICAL.|  
|Памятка|Максимальная длина колонны MEMO составляет 65 500 байтов.|  
  
 Дополнительные ограничения на типы данных можно найти в [ограничениях типа данных.](../../odbc/microsoft/data-type-limitations.md)
