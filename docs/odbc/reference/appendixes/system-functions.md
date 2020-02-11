---
title: Системные функции | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- system functions [ODBC]
- functions [ODBC], system functions
ms.assetid: 36614b4c-e037-43ef-8692-67f4861b144d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e0c7817d37e14ad07b9cc64f59691c27cf665177
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68070095"
---
# <a name="system-functions"></a>Системные функции
В следующей таблице перечислены системные функции, которые включены в набор скалярных функций ODBC. Вызывая **SQLGetInfo** с *типом сведений* SQL_SYSTEM_FUNCTIONS, приложение может определить, какие системные функции поддерживаются драйвером.  
  
 Аргументами, обозначенными как *exp* , может быть имя столбца, результат другой скалярной функции или литерал, где базовый тип данных может быть представлен как SQL_NUMERIC, SQL_DECIMAL, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_FLOAT, SQL_REAL, SQL_DOUBLE, SQL_TYPE_DATE, SQL_TYPE_TIME или SQL_TYPE_TIMESTAMP.  
  
 Аргументы, обозначенные как *value* , могут быть литеральной константой, где базовый тип данных может представляться как SQL_NUMERIC, SQL_DECIMAL, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_FLOAT, SQL_REAL, SQL_DOUBLE, SQL_TYPE_DATE, SQL_TYPE_TIME или SQL_TYPE_TIMESTAMP.  
  
 Возвращаемые значения представлены как типы данных ODBC.  
  
|Компонент|Description|  
|--------------|-----------------|  
|**База данных ()** (ODBC 1,0)|Возвращает имя базы данных, соответствующей обработчику соединения. (Имя базы данных также доступно путем вызова **SQLGetConnectOption** с параметром подключения SQL_CURRENT_QUALIFIER.)|  
|**Ифнулл (** _exp_,_значение_**)** (ODBC 1,0)|Если *exp* имеет значение null, возвращается *значение* . Если *exp* не равен null, возвращается *exp* . Допустимый тип данных или типы *значения* должны быть совместимы с типом данных *exp*.|  
|**User ()** (ODBC 1,0)|Возвращает имя пользователя в СУБД. (Имя пользователя также доступно для **SQLGetInfo** путем указания типа данных: SQL_USER_NAME.) Это значение может отличаться от имени входа.|
