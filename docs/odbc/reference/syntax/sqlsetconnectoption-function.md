---
title: Функция S'LSetConnectOption (англ.) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 263b15cb75fb5c0c7c1d7aa630a8da171b9765a7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301599"
---
# <a name="sqlsetconnectoption-function"></a>Функция SQLSetConnectOption
**Соответствия**  
 Версия Введена: Соответствие стандартам ODBC 1.0: Deprecated  
  
 **Сводка**  
 В ODBC 3 *.x,* функция ODBC 2.0 **S'LSetConnectOption** была заменена **на S'LSetConnectAttr**. Дополнительные сведения см. в разделе [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
> [!NOTE]
>  Для получения дополнительной информации о том, что менеджер драйвера драйвера драйвера драйвера ODBC 2 *.x* работает с помощью [драйвера](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)ODBC 3 *.x,* см.  
  
## <a name="remarks"></a>Remarks  
 Смотрите [информацию ODBC 64-Bit,](../../../odbc/reference/odbc-64-bit-information.md)если ваше приложение будет работать на 64-битной операционной системе.  
  
> [!NOTE]  
>  Атрибут SQL_ASYNC_DBC_FUNCTION_ENABLE, введенный в ODBC 3.8, не поддерживается **S'LSetConnectOption**. Приложения, которые используют асинхронную операцию на ручке соединения, должны использовать **S'LSetConnectAttr.**  
  
## <a name="see-also"></a>См. также:  
 [Справка aPI ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
