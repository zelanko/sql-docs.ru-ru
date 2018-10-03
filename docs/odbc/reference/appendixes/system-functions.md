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
ms.openlocfilehash: 048db455419d2b74658b758f3a3c525b02bf37f3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47811412"
---
# <a name="system-functions"></a>Системные функции
В следующей таблице перечислены системные функции, включенные в набор скалярные функции ODBC. Путем вызова **SQLGetInfo** с *тип сведений* из SQL_SYSTEM_FUNCTIONS, приложение может определить, какие системные функции поддерживаются драйвером.  
  
 Аргументы обозначается как *exp* может быть именем столбца, в результате другой скалярной функции или литералом, где базовый тип данных может быть представлено как SQL_NUMERIC, SQL_DECIMAL, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL _BIGINT SQL_FLOAT, SQL_REAL, SQL_DOUBLE, SQL_TYPE_DATE, SQL_TYPE_TIME и SQL_TYPE_TIMESTAMP.  
  
 Аргументы обозначается как *значение* может быть константа-литерал, где базовый тип данных может быть представлено как SQL_NUMERIC, SQL_DECIMAL, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_FLOAT, SQL_REAL, SQL_DOUBLE, SQL_ TYPE_DATE SQL_TYPE_TIME и SQL_TYPE_TIMESTAMP.  
  
 Возвращаемые значения отображаются в виде типов данных ODBC.  
  
|Компонент|Описание|  
|--------------|-----------------|  
|**БАЗЫ ДАННЫХ ()** (ODBC 1.0)|Возвращает имя базы данных, соответствующей дескриптора соединения. (Имя базы данных доступен также при вызове **SQLGetConnectOption** с возможностью подключения SQL_CURRENT_QUALIFIER.)|  
|**IFNULL (** *exp*,*значение ***)** (ODBC 1.0)|Если *exp* имеет значение null, *значение* возвращается. Если *exp* не равно null, *exp* возвращается. Возможных типов данных или типы *значение* должен быть совместим с типом данных *exp*.|  
|**(ПОЛЬЗОВАТЕЛЬ)** (ODBC 1.0)|Возвращает имя пользователя в СУБД. (Имя пользователя также доступен посредством **SQLGetInfo** , указав тип сведений: SQL_USER_NAME.) Это может отличаться от имени входа.|
