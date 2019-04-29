---
title: Функция SQLSetScrollOptions | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetScrollOptions
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetScrollOptions
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC]
ms.assetid: 2a825ba7-7942-4c23-bcdb-c80dc12f8c86
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dbdd2038bc217a7ca2a2efe08940c03c5da5d8f0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62985237"
---
# <a name="sqlsetscrolloptions-function"></a>Функция SQLSetScrollOptions
**Соответствие стандартам**  
 Представленные версии: Соответствие стандартам 1.0 ODBC: Устарело  
  
 **Сводка**  
 В ODBC 3 *.x*, функция ODBC 2.0 **SQLSetScrollOptions** был заменен классом вызовы **SQLGetInfo** и **SQLSetStmtAttr**.  
  
> [!NOTE]
>  Дополнительные сведения о что диспетчер драйверов сопоставляет эту функцию, чтобы при ODBC 2 *.x* при работе с ODBC 3 *.x* драйвера, см. в разделе [устаревшей функции сопоставления](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)в приложение ж Рекомендации по драйверов для обеспечения обратной совместимости.  
> 
> [!NOTE]
>  Когда диспетчер драйверов сопоставляет **SQLSetScrollOptions** для приложения, работа с ODBC 3 *.x* драйвер, который не поддерживает **SQLSetScrollOptions**, драйвер Диспетчер задает параметр инструкции SQL_ROWSET_SIZE, атрибут не SQL_ATTR_ROW_ARRAY_SIZE инструкции к *RowsetSize* аргумента в **SQLSetScrollOption**. В результате **SQLSetScrollOptions** не может использоваться приложением, при получении нескольких строк путем вызова **SQLFetch** или **SQLFetchScroll**. Он может использоваться только в том случае, если получение несколько строк с помощью вызова **SQLExtendedFetch**.  
  
## <a name="remarks"></a>Примечания  
 Если приложение выполняется в 64-разрядной операционной системе, см. в разделе [сведения о ODBC 64-разрядном](../../../odbc/reference/odbc-64-bit-information.md).  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
