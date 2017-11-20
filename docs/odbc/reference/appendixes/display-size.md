---
title: "Размер изображения | Документы Microsoft"
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
- display size of data types [ODBC]
- size of data types [ODBC]
- data types [ODBC], display size
- SQL data types [ODBC], column characteristics
ms.assetid: 9f7f766f-2492-463c-aab7-f2476e222042
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3faac66828cdc408f9bd153377a3aefe74b882b0
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="display-size"></a>Размер экрана
Отображаемый размер столбца является максимальное количество символов, необходимых для отображения данных в виде символа. Следующая таблица определяет размер экрана для каждого типа данных ODBC SQL.  
  
|Идентификатор типа SQL|Размер экрана|  
|-------------------------|------------------|  
|Все символьные типы []|Определен (для основных типов) или максимальное значение (для типов переменных) количество символов, необходимых для отображения данных в виде символа.|  
|SQL_DECIMAL SQL_NUMERIC|Точность столбца, плюс 2 (a знака, *точности* знаков и десятичной запятой). Например отображаемый размер столбца, определенного как NUMERIC(10,3) — 12.|  
|SQL_BIT|1 (1 цифр).|  
|SQL_TINYINT|4, если подписанные (знак и 3 цифры) или 3, если без учета знака (3 цифры).|  
|SQL_SMALLINT|6 Если подписанные (знак и 5 цифр) или 5, если без учета знака (5 цифр).|  
|SQL_INTEGER|11, если подписанные (знак и 10 цифр) или 10, если без учета знака (10 цифр).|  
|SQL_BIGINT|20 (знак и 19 цифр, если подпись или 20 символов, если без знака).|  
|SQL_REAL|14 (знак, 7 цифр, десятичного разделителя, буквы *E*, знак и 2 цифры).|  
|SQL_FLOAT SQL_DOUBLE|24 (знак, 15 цифр, десятичного разделителя, буквы *E*, знак и 3 цифры).|  
|Все двоичные типы []|Определен или максимальное значение (для типов переменных) длина столбца время 2. (Каждый двоичного байтового представлен 2-разрядное шестнадцатеричное число.)|  
|SQL_TYPE_DATE|10 (дату в формате *гггг мм дд*).|  
|SQL_TYPE_TIME|8 (время в формате *чч*)<br /><br /> — или —<br /><br /> 9 + *s* (время в формате *чч*[.fff...], где *s* имеет точность в долях секунды).|  
|SQL_TYPE_TIMESTAMP|19 (для отметка времени в *гггг мм дд чч* формат)<br /><br /> — или —<br /><br /> 20 + *s* (метки времени, в *гггг мм дд чч*формат [.fff], где *s* имеет точность в долях секунды).|  
|Все типы данных интервала|В разделе [длина типа данных Interval](../../../odbc/reference/appendixes/interval-data-type-length.md).|  
|SQL_GUID|36 (количество символов в *aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee* формат|  
  
 [] Если драйвер не может определить длину столбца или параметра типы переменных, возвращается значение SQL_NO_TOTAL.

