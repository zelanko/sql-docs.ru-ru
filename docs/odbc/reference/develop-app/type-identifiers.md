---
description: Идентификаторы типов
title: Идентификаторы типов | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], identifiers
- type identifiers [ODBC]
- identifiers [ODBC], type
- type identifiers [ODBC], about type identifiers
ms.assetid: 1d9fdfa2-e378-44fe-ac66-9743d9bbdd5a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4ed41716cd351631578d01027663aa9e0f028c7d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487447"
---
# <a name="type-identifiers"></a>Идентификаторы типов
Для описания типов данных SQL и C ODBC определяет два набора *идентификаторов типов*. Идентификатор типа описывает тип столбца SQL или буфера C. Это **#define** значение, которое обычно передается в качестве аргумента функции или возвращается в метаданных.  
  
 Например, следующий вызов **SQLBindParameter** привязывает переменную типа SQL_DATE_STRUCT к параметру даты в инструкции SQL. Идентификатор типа C SQL_C_TYPE_DATE задает тип переменной *даты* , а идентификатор типа SQL SQL_TYPE_DATE задает тип динамического параметра.  
  
```  
SQL_DATE_STRUCT Date;  
SQLINTEGER  DateInd = 0;  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_TYPE_DATE, SQL_TYPE_DATE, 0, 0,  
                  &Date, 0, &DateInd);  
```
