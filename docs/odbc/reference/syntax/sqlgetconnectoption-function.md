---
title: Функция SQLGetConnectOption | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetConnectOption
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetConnectOption
helpviewer_keywords:
- SQLGetConnectOption function [ODBC]
ms.assetid: 59cde899-7957-4b5e-8677-f34d3b859bfd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 947a7ea107e334eb393248f7d368fe958e6229c0
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2019
ms.locfileid: "67792583"
---
# <a name="sqlgetconnectoption-function"></a>Функция SQLGetConnectOption
**Соответствие стандартам**  
 Представленные версии: Соответствие стандартам 1.0 ODBC: Устарело  
  
 **Сводка**  
 В ODBC *3.x*, ODBC *2.x* функция **SQLGetConnectOption** был заменен классом **SQLGetConnectAttr**. Дополнительные сведения см. в разделе [SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md).  
  
> [!NOTE]
>  Дополнительные сведения о что диспетчер драйверов сопоставляет эту функцию, чтобы при ODBC *2.x* при работе с ODBC *3.x* драйвера, см. в разделе [устаревшей функции сопоставления](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)в приложение ж Рекомендации по драйверов для обеспечения обратной совместимости.  
> 
> [!NOTE]
>  Атрибут SQL_ASYNC_DBC_FUNCTION_ENABLE, представленные в ODBC 3.8 не поддерживается в **SQLGetConnectOption**. Приложения, использующие асинхронной операции на дескрипторе соединений необходимо использовать **SQLGetConnectAttr**.  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
