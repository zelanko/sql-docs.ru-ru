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
ms.openlocfilehash: a738e4e1206c8df393fe7cfc5562fc72c080ba32
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47709732"
---
# <a name="sqlsetscrolloptions-function"></a>Функция SQLSetScrollOptions
**Соответствие стандартам**  
 Версия была введена: ODBC 1.0 соответствует стандартам: устарело  
  
 **Сводка**  
 В ODBC 3 *.x*, функция ODBC 2.0 **SQLSetScrollOptions** был заменен классом вызовы **SQLGetInfo** и **SQLSetStmtAttr**.  
  
> [!NOTE]  
>  Дополнительные сведения о что диспетчер драйверов сопоставляет эту функцию, чтобы при ODBC 2 *.x* при работе с ODBC 3 *.x* драйвера, см. в разделе [устаревшей функции сопоставления](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)в приложении G: драйвер рекомендации для обеспечения обратной совместимости.  
  
> [!NOTE]  
>  Когда диспетчер драйверов сопоставляет **SQLSetScrollOptions** для приложения, работа с ODBC 3 *.x* драйвер, который не поддерживает **SQLSetScrollOptions**, драйвер Диспетчер задает параметр инструкции SQL_ROWSET_SIZE, атрибут не SQL_ATTR_ROW_ARRAY_SIZE инструкции к *RowsetSize* аргумента в **SQLSetScrollOption**. В результате **SQLSetScrollOptions** не может использоваться приложением, при получении нескольких строк путем вызова **SQLFetch** или **SQLFetchScroll**. Он может использоваться только в том случае, если получение несколько строк с помощью вызова **SQLExtendedFetch**.  
  
## <a name="remarks"></a>Примечания  
 Если приложение выполняется в 64-разрядной операционной системе, см. в разделе [сведения о ODBC 64-разрядном](../../../odbc/reference/odbc-64-bit-information.md).  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
