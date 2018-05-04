---
title: С помощью Microsoft Internet Information Services | Документы Microsoft
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
- ODBC driver for Oracle [ODBC], IIS
- internet information services [ODBC]
- IIS [ODBC]
ms.assetid: 3328f2f1-b34a-472f-82cf-ad49768ff061
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6c1f0e1e4c21fc6e04bbaae7ec39d4b8d6ef1dd8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="using-microsoft-internet-information-services"></a>С помощью службы Microsoft IIS
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 Если возникли трудности при подключении из в скриптах IIS (особенно если появляется ошибка ORA-12641), добавьте следующую строку в файл Sqlnet.ora:  
  
```  
SQLNET.AUTHENTICATION_SERVICES = (none)  
```  
  
 Сетевые службы Secure будут отключены, чтобы подключиться с помощью анонимную проверку подлинности.
