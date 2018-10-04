---
title: Функция SQLSetConnectOption | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetConnectOption
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetConnectOption
helpviewer_keywords:
- SQLSetConnectOption function [ODBC]
ms.assetid: 8cd2c2a2-25c8-4aff-951c-b593bbfc90ad
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f2a4965fedc7da47751742e863119b818a9fcba9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47646362"
---
# <a name="sqlsetconnectoption-function"></a>Функция SQLSetConnectOption
**Соответствие стандартам**  
 Версия была введена: ODBC 1.0 соответствует стандартам: устарело  
  
 **Сводка**  
 В ODBC 3 *.x*, функция ODBC 2.0 **SQLSetConnectOption** был заменен классом **SQLSetConnectAttr**. Дополнительные сведения см. в разделе [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
> [!NOTE]  
>  Дополнительные сведения о что диспетчер драйверов сопоставляет эту функцию, чтобы при ODBC 2 *.x* при работе с ODBC 3 *.x* драйвера, см. в разделе [устаревшей функции сопоставления](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)".  
  
## <a name="remarks"></a>Примечания  
 См. в разделе [сведения о ODBC 64-разрядном](../../../odbc/reference/odbc-64-bit-information.md), если приложение выполняется в 64-разрядной операционной системе.  
  
> [!NOTE]  
>  Атрибут SQL_ASYNC_DBC_FUNCTION_ENABLE, представленные в ODBC 3.8 не поддерживается в **SQLSetConnectOption**. Приложения, использующие асинхронной операции на дескрипторе соединения необходимо использовать **SQLSetConnectAttr**.  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
