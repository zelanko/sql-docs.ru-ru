---
description: Сообщения, возвращаемые драйвером ODBC для Oracle
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 90f6ed20dfa954925b94e212c172ba9b69ef9596
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88412480"
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
