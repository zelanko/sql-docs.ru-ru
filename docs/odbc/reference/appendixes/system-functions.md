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
manager: craigg
ms.openlocfilehash: 5870cb445d7afd098aba32ffd9be7a88c048bae5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62735060"
---
# <a name="system-functions"></a>Системные функции
В следующей таблице перечислены системные функции, включенные в набор скалярные функции ODBC. Путем вызова **SQLGetInfo** с *тип сведений* из SQL_SYSTEM_FUNCTIONS, приложение может определить, какие системные функции поддерживаются драйвером.  
  
 Аргументы обозначается как *exp* может быть именем столбца, в результате другой скалярной функции или литералом, где базовый тип данных может быть представлено как SQL_NUMERIC, SQL_DECIMAL, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL _BIGINT SQL_FLOAT, SQL_REAL, SQL_DOUBLE, SQL_TYPE_DATE, SQL_TYPE_TIME и SQL_TYPE_TIMESTAMP.  
  
 Аргументы обозначается как *значение* может быть константа-литерал, где базовый тип данных может быть представлено как SQL_NUMERIC, SQL_DECIMAL, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_FLOAT, SQL_REAL, SQL_DOUBLE, SQL_ TYPE_DATE SQL_TYPE_TIME и SQL_TYPE_TIMESTAMP.  
  
 Возвращаемые значения отображаются в виде типов данных ODBC.  
  
|Компонент|Описание|  
|--------------|-----------------|  
|**БАЗЫ ДАННЫХ ()** (ODBC 1.0)|Возвращает имя базы данных, соответствующей дескриптора соединения. (Имя базы данных доступен также при вызове **SQLGetConnectOption** с возможностью подключения SQL_CURRENT_QUALIFIER.)|  
|**IFNULL (** _exp_,_значение_**)** (ODBC 1.0)|Если *exp* имеет значение null, *значение* возвращается. Если *exp* не равно null, *exp* возвращается. Возможных типов данных или типы *значение* должен быть совместим с типом данных *exp*.|  
|**(ПОЛЬЗОВАТЕЛЬ)** (ODBC 1.0)|Возвращает имя пользователя в СУБД. (Имя пользователя также доступен посредством **SQLGetInfo** , указав тип сведений: SQL_USER_NAME.) Это может отличаться от имени входа.|
