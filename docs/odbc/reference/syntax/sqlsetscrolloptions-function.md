---
title: Функция SQLSetScrollOptions | Документы Microsoft
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
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 79ab0c408748fcbea30fdc2c792e433db8a4309d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlsetscrolloptions-function"></a>Функция SQLSetScrollOptions
**Соответствия**  
 Появился в версии: Полное соответствие стандартам 1.0 ODBC: рекомендуется к использованию  
  
 **Сводка**  
 В ODBC 3 *.x*, функция ODBC 2.0 **SQLSetScrollOptions** будет заменен вызовы **SQLGetInfo** и **SQLSetStmtAttr**.  
  
> [!NOTE]  
>  Дополнительные сведения о том, что диспетчер драйверов преобразует эту функцию для при ODBC 2 *.x* при работе с ODBC 3 *.x* драйвера, в разделе [сопоставление устаревшие функции](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)в приложении G: драйвер рекомендации для обеспечения обратной совместимости.  
  
> [!NOTE]  
>  Когда диспетчер драйверов сопоставляет **SQLSetScrollOptions** для приложения, работа с ODBC 3 *.x* драйвер, который не поддерживает **SQLSetScrollOptions**, драйвер Диспетчер задает параметр инструкции SQL_ROWSET_SIZE атрибут не SQL_ATTR_ROW_ARRAY_SIZE инструкции к *RowsetSize* аргумент в **SQLSetScrollOption**. В результате **SQLSetScrollOptions** не может использоваться приложением при их получении нескольких строк путем вызова **SQLFetch** или **SQLFetchScroll**. Он может использоваться только в том случае, если извлечение нескольких строк путем вызова **SQLExtendedFetch**.  
  
## <a name="remarks"></a>Замечания  
 Если приложение будет выполняться на 64-разрядной операционной системе, см. раздел [сведения ODBC 64-разрядных](../../../odbc/reference/odbc-64-bit-information.md).  
  
## <a name="see-also"></a>См. также  
 [Справочник по API-интерфейса ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
