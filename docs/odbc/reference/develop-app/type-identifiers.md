---
title: Введите идентификаторы | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], identifiers
- type identifiers [ODBC]
- identifiers [ODBC], type
- type identifiers [ODBC], about type identifiers
ms.assetid: 1d9fdfa2-e378-44fe-ac66-9743d9bbdd5a
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 87bf03fca6ccf3a5066d2aaeaff5bebd28c005b7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="type-identifiers"></a>Идентификаторы типа
Для описания типов данных SQL и C, ODBC определяет два набора *идентификаторы типов*. Идентификатор типа описывает тип SQL столбца или C буфера. Это **#define** значение обычно передается как аргумент функции и возвращаются в метаданных.  
  
 Например, в следующем вызове **SQLBindParameter** привязывает переменную типа SQL_DATE_STRUCT параметр даты в инструкции SQL. Тип идентификатора типа C SQL_C_TYPE_DATE *даты* переменной и идентификатора SQL типа SQL_TYPE_DATE указывает тип динамического параметра.  
  
```  
SQL_DATE_STRUCT Date;  
SQLINTEGER  DateInd = 0;  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_TYPE_DATE, SQL_TYPE_DATE, 0, 0,  
                  &Date, 0, &DateInd);  
```
