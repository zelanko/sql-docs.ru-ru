---
title: "Системные функции | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- system functions [ODBC]
- functions [ODBC], system functions
ms.assetid: 36614b4c-e037-43ef-8692-67f4861b144d
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 79cbe8677ba4401fb779dc9765d639b1d86a0f5f
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="system-functions"></a>Системные функции
В следующей таблице перечислены системные функции, включенные в набор скалярные функции ODBC. Путем вызова **SQLGetInfo** с *типу информации* из SQL_SYSTEM_FUNCTIONS, приложение может определить, какие системные функции поддерживаются драйвером.  
  
 Аргументы обозначается как *exp* может быть имя столбца, в результате выполнения другого скалярной функции или литералом, где базовый тип данных может быть представлено как SQL_NUMERIC, SQL_DECIMAL, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL _BIGINT SQL_FLOAT, SQL_REAL, SQL_DOUBLE, SQL_TYPE_DATE, SQL_TYPE_TIME и SQL_TYPE_TIMESTAMP.  
  
 Аргументы обозначается как *значение* может быть константа, где базовый тип данных может быть представлено как SQL_NUMERIC, SQL_DECIMAL, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_FLOAT, SQL_REAL, SQL_DOUBLE, SQL_ TYPE_DATE SQL_TYPE_TIME и SQL_TYPE_TIMESTAMP.  
  
 Возвращаемые значения представлены в виде типов данных ODBC.  
  
|Компонент|Description|  
|--------------|-----------------|  
|**БАЗЫ ДАННЫХ ()** (ODBC 1.0)|Возвращает имя базы данных, соответствующий дескриптор соединения. (Имя базы данных можно получить, вызвав **SQLGetConnectOption** с параметром SQL_CURRENT_QUALIFIER.)|  
|**IFNULL (** *exp*,*значение***)** (ODBC 1.0)|Если *exp* имеет значение null, *значение* возвращается. Если *exp* не равно null, *exp* возвращается. Тип данных или типы *значение* должен быть совместим с типом данных *exp*.|  
|**(ПОЛЬЗОВАТЕЛЬ)** (ODBC 1.0)|Возвращает имя пользователя в СУБД. (Имя пользователя можно получить посредством **SQLGetInfo** , указав тип данных: SQL_USER_NAME.) Это может отличаться от имени входа.|
