---
title: "Функция SQLSetConnectOption | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLSetConnectOption
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLSetConnectOption
helpviewer_keywords: SQLSetConnectOption function [ODBC]
ms.assetid: 8cd2c2a2-25c8-4aff-951c-b593bbfc90ad
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b133c5a34dd37f02dd930d2a035c6b69ea49b093
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="sqlsetconnectoption-function"></a>Функция SQLSetConnectOption
**Соответствия**  
 Появился в версии: Полное соответствие стандартам 1.0 ODBC: рекомендуется к использованию  
  
 **Сводка**  
 В ODBC 3*.x*, функция ODBC 2.0 **SQLSetConnectOption** будет заменен **SQLSetConnectAttr**. Дополнительные сведения см. в разделе [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
> [!NOTE]  
>  Дополнительные сведения о том, что диспетчер драйверов преобразует эту функцию для при ODBC 2*.x* при работе с ODBC 3*.x* драйвера, в разделе [сопоставление устаревшие функции](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)".  
  
## <a name="remarks"></a>Замечания  
 В разделе [сведения ODBC 64-разрядных](../../../odbc/reference/odbc-64-bit-information.md), если приложение будет выполняться на 64-разрядной операционной системе.  
  
> [!NOTE]  
>  Атрибут SQL_ASYNC_DBC_FUNCTION_ENABLE появились в ODBC 3.8 не поддерживается в **SQLSetConnectOption**. Приложения, использующие асинхронной операции на дескрипторе соединения необходимо использовать **SQLSetConnectAttr**.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API-интерфейса ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
