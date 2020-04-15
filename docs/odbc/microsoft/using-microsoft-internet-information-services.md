---
title: Использование информационных служб Microsoft в Интернете Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], IIS
- internet information services [ODBC]
- IIS [ODBC]
ms.assetid: 3328f2f1-b34a-472f-82cf-ad49768ff061
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0c71babf933c2615e6c2464696c1023ccaf53dd7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282473"
---
# <a name="using-microsoft-internet-information-services"></a>Использование служб Microsoft IIS
> [!IMPORTANT]  
>  Эта функция будет удалена в будущей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставленный Oracle.  
  
 Если у вас возникают трудности с подключением из сценария IIS (особенно если вы получили ошибку ORA-12641), добавьте следующую строку в файл Sqlnet.ora:  
  
```  
SQLNET.AUTHENTICATION_SERVICES = (none)  
```  
  
 Это позволит отключить безопасные сетевые службы, чтобы вы могли подключиться с помощью анонимной аутентификации.
