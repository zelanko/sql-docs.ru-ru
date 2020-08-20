---
description: Функция SQLSetScrollOptions
title: Функция SQLSetScrollOptions | Документация Майкрософт
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetScrollOptions
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLSetScrollOptions
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC]
ms.assetid: 2a825ba7-7942-4c23-bcdb-c80dc12f8c86
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0197c3756b76b480cd5370b5edff9d6fc88b201c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88491211"
---
# <a name="sqlsetscrolloptions-function"></a>Функция SQLSetScrollOptions
**Соответствия**  
 Введенная версия: соответствие стандартам ODBC 1,0: не рекомендуется  
  
 **Сводка**  
 В ODBC *3. x*функция ODBC 2,0 **SQLSetScrollOptions** была заменена вызовами функций **SQLGetInfo** и **SQLSetStmtAttr**.  
  
> [!NOTE]
>  Дополнительные сведения о том, как диспетчер драйверов сопоставляет эту функцию, когда приложение ODBC *2. x* работает с драйвером ODBC *3. x* , см. в разделе [сопоставление устаревших функций](../../../odbc/reference/appendixes/mapping-deprecated-functions.md) в приложении G: рекомендации по драйверу для обеспечения обратной совместимости.  
> 
> [!NOTE]
>  Когда диспетчер драйверов сопоставляет **SQLSetScrollOptions** для приложения, работающего с драйвером ODBC *3. x* , который не поддерживает **SQLSetScrollOptions**, диспетчер драйверов устанавливает параметр инструкции SQL_ROWSET_SIZE, а не атрибут SQL_ATTR_ROW_ARRAY_SIZE инструкции, в аргумент *ровсетсизе* в **склсетскроллоптион**. В результате **SQLSetScrollOptions** не может использоваться приложением при выборке нескольких строк путем вызова **SQLFetch** или **SQLFetchScroll**. Его можно использовать только при выборке нескольких строк путем вызова **SQLExtendedFetch**.  
  
## <a name="remarks"></a>Remarks  
 Если приложение будет работать в 64-разрядной операционной системе, см. раздел [сведения о ODBC 64-bit](../../../odbc/reference/odbc-64-bit-information.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
