---
title: Аргументы функции Unicode Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Unicode [ODBC], functions
- functions [ODBC], Unicode functions
ms.assetid: eafe8c7e-f6d2-44d7-99ee-cf2148a30f4f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a25dd6fe0a77aad5c5ec9ba15eaf12bd2ec3fc18
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284294"
---
# <a name="unicode-function-arguments"></a>Аргументы функции Юникода
Менеджер драйверов ODBC 3.5 (или выше) поддерживает как версии ANSI, так и Unicode всех функций, которые принимают указатели на строки символов или S'LPOINTER в своих аргументах. Функции Unicode реализованы как функции (с суффиксом *W),* а не как макросы. Функции ANSI (которые можно назвать с суффиксом *A*или без), идентичны текущим функциям ODBC API.  
  
## <a name="remarks"></a>Remarks  
 Функции Unicode, которые всегда возвращаются или берут строки или аргументы длины, передаются как количество символов. Для функций, возвращающие информацию о длине сервера, размер и точность дисплея описываются в количестве символов. Когда длина (размер передачи данных) может относиться к строке или неструнным данным, длина описывается в длинах октета. Например, **sLGetInfoW** по-прежнему будет использовать длину в качестве подсчета байт, но **S'LExecDirectW** будет использовать количество символов.  
  
 Количество символов относится к числу байтов (октетов) для функций ANSI и числу WCHAR (16-битные слова) для функций UNICODE. В частности, двухбайтная последовательность символов (DBCS) или многобайтная последовательность символов (MBCS) могут состоять из нескольких байтов. Последовательность символов UTF-16 Unicode может состоять из нескольких WCHARs.  
  
 Ниже приводится список функций ODBC API, которые поддерживают как версии Unicode (W) и ANSI (A):  
  
|||  
|-|-|  
|**SQLBrowseConnect**|**Функции SQLGetDiagRec**|  
|**SQLColAttribute**|**SQLGetInfo**|  
|**СЗЛКолАтрибуты**|**SQLGetStmtAttr**|  
|**SQLColumnPrivileges**|**SQLGetTypeInfo**|  
|**SQLColumns**|**СЗЛНаТИЗа**|  
|**SQLConnect**|**SQLPrepare**|  
|**Источники данных S'LData**|**SQLPrimaryKeys**|  
|**SQLDescribeCol**|**SQLProcedureColumns**|  
|**SQLDriverConnect**|**SQLProcedures**|  
|**SQLDrivers**|**SQLSetConnectAttr**|  
|**Sqlerror**|**СЗЛЕтКоннектОпция**|  
|**SQLExecDirect**|**СЗЛСетКурсОрНамейм**|  
|**SQLForeignKeys**|**SQLSetDescField**|  
|**SQLGetConnectAttr**|**SQLSetStmtAttr**|  
|**СЗЛГетКоннектОпция**|**SQLSpecialColumns**|  
|**SQLGetCursorName**|**SQLStatistics**|  
|**SQLGetDescField**|**SQLTablePrivileges**|  
|**SQLGetDescRec**|**SQLTables**|  
|**SQLGetDiagField**||  
  
 Ниже приводится список функций ODBC Installer и ODBC Translator, которые поддерживают версии Unicode (W) и ANSI (A):  
  
|||  
|-|-|  
|**SQLConfigDataSource**|**СЗЛУстановитьДрайверМенеджер**|  
|**СЗЛСоздатьДатаИсточник**|**СЗЛУСтангерОшибка**|  
|**СЗЛДатаИсточникТоДрайвер**|**СЗЛУСтантлТОДБ**|  
|**СЗЛДрайверТоДатаИсточник**|**СЗЛРедРедЕДСН**|  
|**S'LGetAvailableDrivers**|**СЗЛССНФризиНИИ**|  
|**СЗЛТЕтАзидДрайвери**|**СЗЛЛиАДСН**|  
|**СЗЛГетПереводчик**|**СЗЛДуНТСНОНИНИ**|  
|**СЗЛУстансулДрайвер**||  
  
> [!NOTE]
>  Удзагированные функции имеют поддержку отображения Unicode-TO-ANSI, поскольку диспетчер драйверов ODBC *3.x* поддерживает перекомпиляцию приложений ODBC *2.x* с **помощью #define**UNICODE.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Приложения на базе Юникода](../../../odbc/reference/develop-app/unicode-applications.md)  
  
-   [Драйверы Юникода](../../../odbc/reference/develop-app/unicode-drivers.md)  
  
-   [Сопоставление функции в диспетчере драйверов](../../../odbc/reference/develop-app/function-mapping-in-the-driver-manager.md)
