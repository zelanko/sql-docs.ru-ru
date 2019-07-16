---
title: Сообщения, возвращаемые драйвером ODBC для Oracle | Документация Майкрософт
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68045178"
---
# <a name="messages-returned-by-the-odbc-driver-for-oracle"></a>Сообщения, возвращаемые драйвером ODBC для Oracle
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 Если сообщение об ошибке Oracle доступен, он будет возвращен с [Microsoft] [драйвер ODBC для Oracle,] и [Oracle] тегов; в противном случае сообщение возвращается без тега [Oracle], как показано в следующих примерах:  
  
## <a name="oracle-error-message"></a>Сообщение об ошибке Oracle:  
  
```  
[Microsoft][ODBC driver for Oracle][Oracle]ORA-nnnnn message-text  
```  
  
## <a name="odbc-driver-for-oracle-error-message"></a>Драйвер ODBC для Oracle сообщение об ошибке:  
  
```  
[Microsoft][ODBC driver for Oracle]  
```
