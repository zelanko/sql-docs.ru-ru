---
title: Сообщения, возвращенные драйвером ODBC для Oracle | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- error messages [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], error messages
ms.assetid: 150bde1d-adb6-4e77-90e9-4dc93499a746
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bb2fc54692a77441bb2516ad72c0c44951152f56
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68045178"
---
# <a name="messages-returned-by-the-odbc-driver-for-oracle"></a>Сообщения, возвращаемые драйвером ODBC для Oracle
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемый Oracle.  
  
 Если сообщение об ошибке Oracle доступно, оно будет возвращено перед тегами [Microsoft], [ODBC Driver for Oracle] и [Oracle]. в противном случае сообщение возвращается без тега [Oracle], как показано в следующих примерах:  
  
## <a name="oracle-error-message"></a>Сообщение об ошибке Oracle:  
  
```  
[Microsoft][ODBC driver for Oracle][Oracle]ORA-nnnnn message-text  
```  
  
## <a name="odbc-driver-for-oracle-error-message"></a>Сообщение об ошибке ODBC Driver для Oracle:  
  
```  
[Microsoft][ODBC driver for Oracle]  
```
