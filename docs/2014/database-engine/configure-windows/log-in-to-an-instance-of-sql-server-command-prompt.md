---
title: Вход в экземпляр SQL Server (командная строка) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- logins [SQL Server], named instance of SQL Server
- log ins [SQL Server]
- logins [SQL Server], default instance of SQL Server
- command prompt [SQL Server], logins
- logging in [SQL Server]
ms.assetid: f67c11e3-c519-40c9-82c1-07efa9d9985e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2687668f7cd825f51297d186a11d65d4f0c53d77
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84935225"
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
  
## <a name="see-also"></a>См. также:  
 [sqlcmd Utility](../../tools/sqlcmd-utility.md)   
 [Программа osql](../../tools/osql-utility.md)  
  
  
