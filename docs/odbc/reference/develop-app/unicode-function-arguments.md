---
description: Аргументы функции Юникода
title: Аргументы функции Юникода | Документация Майкрософт
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
ms.openlocfilehash: 54d79e59ac779efdb1a347531b7f536a074e9686
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424446"
---
# <a name="unicode-function-arguments"></a>Аргументы функции Юникода
Диспетчер драйверов ODBC 3,5 (или более поздней версии) поддерживает версии ANSI и Юникод всех функций, которые принимают указатели на символьные строки или СКЛПОИНТЕР в своих аргументах. Функции Юникода реализуются как функции (с суффиксом *W*), а не как макросы. Функции ANSI (которые могут вызываться с суффиксом или без *него) идентичны*текущим ФУНКЦИЯМ API ODBC.  
  
## <a name="remarks"></a>Remarks  
 Для функций Юникода, которые всегда возвращают или принимают строки или аргументы длины, аргументы передаются как количество символов. Для функций, возвращающих сведения о длине данных сервера, размер и точность отображения описаны в разделе число символов. Если длина (размер перемещения данных) может ссылаться на строковые или нестроковые данные, длина описана в октетах. Например, **склжетинфов** будет по-прежнему иметь длину в виде количества байт, но **склексекдиректв** будет использовать количество символов.  
  
 Количество символов — это число байтов (октетов) для функций ANSI и число WCHAR (16-разрядных слов) для функций Юникода. В частности, двойная последовательность символов (DBCS) или многобайтовая кодировка (MBCS) может состоять из нескольких байтов. Последовательность символов Юникода UTF-16 может состоять из нескольких Вчарс.  
  
 Ниже приведен список функций API ODBC, поддерживающих версии Юникода (W) и ANSI (A).  
  
|||  
|-|-|  
|**SQLBrowseConnect**|**Функции SQLGetDiagRec**|  
|**SQLColAttribute**|**SQLGetInfo**|  
|**SQLColAttributes**|**SQLGetStmtAttr**|  
|**SQLColumnPrivileges**|**SQLGetTypeInfo**|  
|**SQLColumns**|**SQLNativeSQL**|  
|**SQLConnect**|**SQLPrepare**|  
|**SQLDataSources**|**SQLPrimaryKeys**|  
|**SQLDescribeCol**|**SQLProcedureColumns**|  
|**SQLDriverConnect**|**SQLProcedures**|  
|**SQLDrivers**|**SQLSetConnectAttr**|  
|**SQLError**|**SQLSetConnectOption**|  
|**SQLExecDirect**|**SQLSetCursorName**|  
|**SQLForeignKeys**|**SQLSetDescField**|  
|**SQLGetConnectAttr**|**SQLSetStmtAttr**|  
|**SQLGetConnectOption**|**SQLSpecialColumns**|  
|**SQLGetCursorName**|**SQLStatistics**|  
|**SQLGetDescField**|**SQLTablePrivileges**|  
|**SQLGetDescRec**|**SQLTables**|  
|**SQLGetDiagField**||  
  
 Ниже приведен список функций установщика ODBC и ODBC-переводчиков, поддерживающих версии Юникода (W) и ANSI (A).  
  
|||  
|-|-|  
|**SQLConfigDataSource**|**склинсталлдриверманажер**|  
|**склкреатедатасаурце**|**склинсталлереррор**|  
|**склдатасаурцетодривер**|**склинсталлодбк**|  
|**склдривертодатасаурце**|**склреадфиледсн**|  
|**склжетаваилабледриверс**|**склремоведснфромини**|  
|**склжетинсталледдриверс**|**склвалиддсн**|  
|**склжеттранслатор**|**склвритедснтоини**|  
|**склинсталлдривер**||  
  
> [!NOTE]
>  Устаревшие функции имеют поддержку сопоставления Юникода и ANSI, так как диспетчер драйверов ODBC *3. x* поддерживает перекомпиляцию приложений ODBC *2. x* с помощью Юникода **#define**.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Приложения на базе Юникода](../../../odbc/reference/develop-app/unicode-applications.md)  
  
-   [Драйверы Юникода](../../../odbc/reference/develop-app/unicode-drivers.md)  
  
-   [Сопоставление функции в диспетчере драйверов](../../../odbc/reference/develop-app/function-mapping-in-the-driver-manager.md)
