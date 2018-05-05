---
title: SQLGetFunctions (драйвер ODBC для Visual FoxPro) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLGetFunctions function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 8102932a-88b3-49d8-bf7a-c766f54878c0
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c17cbabc7f07fa079ef2c635ac7652a072943186
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlgetfunctions-visual-foxpro-odbc-driver"></a>SQLGetFunctions (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения по Visual FoxPro ODBC драйвера. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: полный  
  
 Соответствия ODBC API: 1 уровень  
  
 Возвращает значение TRUE для всех поддерживаемых функций.  
  
 Драйвер ODBC для Visual FoxPro поддерживает функции всех основных компонентов ODBC API и уровня 1. Следующая таблица указывает, поддерживает ли драйвер определенной функции уровня 2.  
  
|*Функция*|Поддерживается|  
|----------------|---------------|  
|SQL_API_SQLBROWSECONNECT|Нет|  
|SQL_API_SQLCOLUMNPRIVELEGES|Нет|  
|SQL_API_SQLDATASOURCES|Да|  
|SQL_API_SQLDESCRIBEPARAM|Нет|  
|SQL_API_SQLDRIVERS|Да|  
|SQL_API_SQLEXTENDEDFETCH|Да|  
|SQL_API_SQLFOREIGNKEYS|Нет|  
|SQL_API_SQLMORERESULTS|Да|  
|SQL_API_SQLNATIVESQL|Нет|  
|SQL_API_SQLNUMPARAMS|Да|  
|SQL_API_SQLPARAMOPTIONS|Да|  
|SQL_API_SQLPRIMARYKEYS|Да|  
|SQL_API_SQLPROCEDURECOLUMNS|Нет|  
|SQL_API_SQLPROCEDURES|Нет|  
|SQL_API_SQLSETPOS|Да|  
|SQL_API_SQLSETSCROLLOPTIONS|Да|  
|SQL_API_SQLTABLEPRIVILEGES|Нет|  
  
 Дополнительные сведения см. в разделе [SQLGetFunctions](../../odbc/reference/syntax/sqlgetfunctions-function.md) в *справочнике программиста ODBC*.
