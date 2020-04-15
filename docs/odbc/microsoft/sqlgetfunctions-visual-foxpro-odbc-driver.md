---
title: SLGetФункции (Визуальный водитель FoxPro ODBC) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: af7ad2368847ff271dcf81759d6fa06b8a79fb0a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298614"
---
# <a name="sqlgetfunctions-visual-foxpro-odbc-driver"></a>SQLGetFunctions (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Эта тема содержит Visual FoxPro ODBC Драйвер-специфической информации. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
 Поддержка: Полная  
  
 Соответствие API ODBC: Уровень 1  
  
 Возвращает TRUE для всех поддерживаемых функций.  
  
 Visual FoxPro ODBC Driver поддерживает все функции ODBC API Core и Level 1. В следующей таблице указывается, поддерживает ли драйвер определенную функцию уровня 2.  
  
|*Функция*|Поддерживается|  
|----------------|---------------|  
|SQL_API_SQLBROWSECONNECT|нет|  
|SQL_API_SQLCOLUMNPRIVELEGES|нет|  
|SQL_API_SQLDATASOURCES|Да|  
|SQL_API_SQLDESCRIBEPARAM|нет|  
|SQL_API_SQLDRIVERS|Да|  
|SQL_API_SQLEXTENDEDFETCH|Да|  
|SQL_API_SQLFOREIGNKEYS|нет|  
|SQL_API_SQLMORERESULTS|Да|  
|SQL_API_SQLNATIVESQL|нет|  
|SQL_API_SQLNUMPARAMS|Да|  
|SQL_API_SQLPARAMOPTIONS|Да|  
|SQL_API_SQLPRIMARYKEYS|Да|  
|SQL_API_SQLPROCEDURECOLUMNS|нет|  
|SQL_API_SQLPROCEDURES|нет|  
|SQL_API_SQLSETPOS|Да|  
|SQL_API_SQLSETSCROLLOPTIONS|Да|  
|SQL_API_SQLTABLEPRIVILEGES|нет|  
  
 Для получения более подробной информации, *ODBC Programmer's Reference*см. [SQLGetFunctions](../../odbc/reference/syntax/sqlgetfunctions-function.md)
