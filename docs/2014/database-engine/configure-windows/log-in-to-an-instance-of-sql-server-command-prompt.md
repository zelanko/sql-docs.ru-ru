---
title: Вход в экземпляр SQL Server (командная строка) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- logins [SQL Server], named instance of SQL Server
- log ins [SQL Server]
- logins [SQL Server], default instance of SQL Server
- command prompt [SQL Server], logins
- logging in [SQL Server]
ms.assetid: f67c11e3-c519-40c9-82c1-07efa9d9985e
caps.latest.revision: 23
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 496f9c15e344577918045fe8cabca6f901019a3d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37282060"
---
# <a name="log-in-to-an-instance-of-sql-server-command-prompt"></a>Вход в экземпляр SQL Server (командная строка)
  В этом разделе описывается, как проверить связь с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], используя программу **sqlcmd** .  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-log-in-to-the-default-instance-of-sql-server"></a>Вход в экземпляр SQL Server по умолчанию  
  
1.  В командной строке введите следующую команду для соединения с использованием проверки подлинности Windows:  
  
    ```  
    sqlcmd [ /E ] [ /S servername ]  
  
    ```  
  
#### <a name="to-log-in-to-a-named-instance-of-sql-server"></a>Вход в именованный экземпляр SQL Server  
  
1.  В командной строке введите следующую команду для соединения с использованием проверки подлинности Windows:  
  
    ```  
    sqlcmd [ /E ] /S servername\instancename  
  
    ```  
  
## <a name="see-also"></a>См. также  
 [Программа sqlcmd](../../tools/sqlcmd-utility.md)   
 [Программа osql](../../tools/osql-utility.md)  
  
  
