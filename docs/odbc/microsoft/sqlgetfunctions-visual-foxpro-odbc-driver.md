---
title: SQLGetFunctions (драйвер ODBC для Visual FoxPro) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetFunctions function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 8102932a-88b3-49d8-bf7a-c766f54878c0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: da74bbb64a76f6c3ff6c55754798b975dab83826
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68003329"
---
# <a name="sqlgetfunctions-visual-foxpro-odbc-driver"></a>SQLGetFunctions (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения Visual FoxPro ODBC-драйвером. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: Полное  
  
 Соответствие API ODBC: уровне 1  
  
 Возвращает значение TRUE для всех поддерживаемых функций.  
  
 Драйвер ODBC для Visual FoxPro поддерживает все базовый ODBC API и уровня 1. Следующая таблица указывает, поддерживает ли драйвер определенной функции уровня 2.  
  
|*Function*|Поддерживается|  
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
  
 Дополнительные сведения см. в разделе [SQLGetFunctions](../../odbc/reference/syntax/sqlgetfunctions-function.md) в *Справочник по программированию ODBC*.
