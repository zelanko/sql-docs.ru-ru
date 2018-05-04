---
title: Сообщения, возвращаемые драйвером ODBC для Oracle | Документы Microsoft
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
helpviewer_keywords:
- error messages [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], error messages
ms.assetid: 150bde1d-adb6-4e77-90e9-4dc93499a746
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3bcf1e257d075d2202b1096f0d497e41d7fe79f1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="messages-returned-by-the-odbc-driver-for-oracle"></a>Сообщения, возвращаемые драйвером ODBC для Oracle
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 Если сообщение об ошибке Oracle доступен, он будет возвращен предшествует [Microsoft] [драйвер ODBC для Oracle,] и [Oracle] тегов; в противном случае сообщение возвращается без тега [Oracle], как показано в следующих примерах:  
  
## <a name="oracle-error-message"></a>Oracle сообщение об ошибке:  
  
```  
[Microsoft][ODBC driver for Oracle][Oracle]ORA-nnnnn message-text  
```  
  
## <a name="odbc-driver-for-oracle-error-message"></a>Драйвер ODBC Oracle сообщения об ошибке:  
  
```  
[Microsoft][ODBC driver for Oracle]  
```
