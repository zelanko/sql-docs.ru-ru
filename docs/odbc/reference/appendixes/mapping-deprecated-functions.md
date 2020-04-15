---
title: Картирование депрепроизмированных функций (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], about mapping deprecated functions
- backward compatibility [ODBC], mapping deprecated functions
- deprecated functions [ODBC]
- compatibility [ODBC], mapping deprecated functions
- functions [ODBC], mapping deprecated functions
- mapping deprecated functions [ODBC]
ms.assetid: ee462617-1d79-4c88-afeb-b129cff34cc6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a4e89cd9281520e70ec5fb289c6050e77ec6194c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299884"
---
# <a name="mapping-deprecated-functions"></a>Сопоставление нерекомендуемых функций
В этом разделе описывается, как амортизированные функции отображаются менеджером драйверов ODBC *3.x,* чтобы гарантировать обратную совместимость драйверов ODBC *3.x,* которые используются с приложениями ODBC *2.x.* Менеджер драйвера выполняет это отображение независимо от версии приложения. Поскольку каждая из функций ODBC *2.x* в следующем списке отображается на соответствующую функцию ODBC *3.x* при вызове драйвера ODBC *3.x,* драйвер ODBC *3.x* не должен реализовывать функции ODBC *2.x.*  
  
 Отображение в списке срабатывает, когда драйвер омовающий *3.x* и драйвер не поддерживает функцию, которая отображается.  
  
 В следующей таблице перечислены все дублированные функциональные возможности, которые были введены в ODBC *3.x*.  
  
|Функция ODBC *2.x*|Функция ODBC *3.x*|  
|-------------------------|-------------------------|  
|**СЗЛАллокКоннект**|**СЗЛАллокХэндл**|  
|**СЗЛАллокЕнв**|**СЗЛАллокХэндл**|  
|**СЗЛАлокСтмт**|**СЗЛАллокХэндл**|  
|**СЗЛБиндпарам**|**SQLBindParameter**|  
|**СЗЛКолАтрибуты**|**SQLColAttribute**|  
|**Sqlerror**|**Функции SQLGetDiagRec**|  
|**СЗЛФриКоннект**|**SQLFreeHandle**|  
|**СЗЛФриЕнв**|**SQLFreeHandle**|  
|**СЗЛФриСтмт** с *опцией* SQL_DROP|**SQLFreeHandle**|  
|**СЗЛГетКоннектОпция**|**SQLGetConnectAttr**|  
|**СЗЛГетСтмтOption**|**SQLGetStmtAttr**|  
|**СЗЛПарамОпции**|**SQLSetStmtAttr**|  
|**СЗЛЕтКоннектОпция**|**SQLSetConnectAttr**|  
|**СЗЛСетПарам**|**SQLBindParameter**|  
|**СЗЛСетПрокрутОпция**|**SQLSetStmtAttr**|  
|**СЗЛСетСтмтOption**|**SQLSetStmtAttr**|  
|**СЗЛТрансакт**|**SQLEndTran**|  
  
 Несмотря на то, что эта функция не существовала в ODBC *2.x,* она находится в стандартах Open Group и ISO.  
  
 Это функция ODBC 1.0.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Сопоставление SQLAllocConnect](../../../odbc/reference/appendixes/sqlallocconnect-mapping.md)  
  
-   [Сопоставление SQLAllocEnv](../../../odbc/reference/appendixes/sqlallocenv-mapping.md)  
  
-   [Сопоставление SQLAllocStmt](../../../odbc/reference/appendixes/sqlallocstmt-mapping.md)  
  
-   [Сопоставление SQLBindParam](../../../odbc/reference/appendixes/sqlbindparam-mapping.md)  
  
-   [Сопоставление SQLColAttributes](../../../odbc/reference/appendixes/sqlcolattributes-mapping.md)  
  
-   [Сопоставление SQLError](../../../odbc/reference/appendixes/sqlerror-mapping.md)  
  
-   [Сопоставление SQLFreeConnect](../../../odbc/reference/appendixes/sqlfreeconnect-mapping.md)  
  
-   [Сопоставление SQLFreeEnv](../../../odbc/reference/appendixes/sqlfreeenv-mapping.md)  
  
-   [Сопоставление SQLFreeStmt](../../../odbc/reference/appendixes/sqlfreestmt-mapping.md)  
  
-   [Функция SQLGetConnectOption](../../../odbc/reference/appendixes/sqlgetconnectoption-mapping.md)  
  
-   [Сопоставление SQLGetStmtOption](../../../odbc/reference/appendixes/sqlgetstmtoption-mapping.md)  
  
-   [Сопоставление SQLInstallTranslator](../../../odbc/reference/appendixes/sqlinstalltranslator-mapping.md)  
  
-   [Сопоставление SQLParamOptions](../../../odbc/reference/appendixes/sqlparamoptions-mapping.md)  
  
-   [Сопоставление SQLSetConnectOption](../../../odbc/reference/appendixes/sqlsetconnectoption-mapping.md)  
  
-   [Сопоставление SQLSetParam](../../../odbc/reference/appendixes/sqlsetparam-mapping.md)  
  
-   [Сопоставление SQLSetScrollOptions](../../../odbc/reference/appendixes/sqlsetscrolloptions-mapping.md)  
  
-   [Сопоставление SQLSetStmtOption](../../../odbc/reference/appendixes/sqlsetstmtoption-mapping.md)  
  
-   [Сопоставление SQLTransact](../../../odbc/reference/appendixes/sqltransact-mapping.md)
