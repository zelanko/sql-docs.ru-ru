---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 77a85caefadb54c3db2716c4db18b504e02da996
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/19/2019
ms.locfileid: "68342939"
---
# <a name="sqlsetscrolloptions-function"></a>Функция SQLSetScrollOptions
**Соответствия**  
 Представленная версия: Соответствие стандартам ODBC 1,0: Устарело  
  
 **Сводка**  
 В ODBC *3. x*функция ODBC 2,0 **SQLSetScrollOptions** была заменена вызовами функций **SQLGetInfo** и **SQLSetStmtAttr**.  
  
> [!NOTE]
>  Дополнительные сведения о том, как диспетчер драйверов сопоставляет эту функцию, когда приложение ODBC *2. x* работает с драйвером ODBC *3. x* , см. в разделе [сопоставление устаревших функций](../../../odbc/reference/appendixes/mapping-deprecated-functions.md) в приложении ж: Рекомендации по драйверу для обеспечения обратной совместимости.  
> 
> [!NOTE]
>  Когда диспетчер драйверов сопоставляет **SQLSetScrollOptions** для приложения, работающего с драйвером ODBC *3. x* , который не поддерживает **SQLSetScrollOptions**, диспетчер драйверов устанавливает параметр инструкции SQL_ROWSET_SIZE, а не SQL_ATTR_ROW_ Атрибут инструкции ARRAY_SIZE для аргумента *ровсетсизе* в **склсетскроллоптион**. В результате **SQLSetScrollOptions** не может использоваться приложением при выборке нескольких строк путем вызова **SQLFetch** или **SQLFetchScroll**. Его можно использовать только при выборке нескольких строк путем вызова **SQLExtendedFetch**.  
  
## <a name="remarks"></a>Примечания  
 Если приложение будет работать в 64-разрядной операционной системе, см. раздел [сведения о ODBC 64-bit](../../../odbc/reference/odbc-64-bit-information.md).  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
