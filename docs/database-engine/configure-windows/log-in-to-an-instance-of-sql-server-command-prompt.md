---
title: "Вход в экземпляр SQL Server (командная строка) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "имена для входа [SQL Server], именованный экземпляр SQL Server"
  - "имена входа [SQL Server]"
  - "имена для входа [SQL Server], экземпляр SQL Server по умолчанию"
  - "командная строка [SQL Server], имена для входа"
  - "вход в систему [SQL Server]"
ms.assetid: f67c11e3-c519-40c9-82c1-07efa9d9985e
caps.latest.revision: 26
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 26
---
# Вход в экземпляр SQL Server (командная строка)
  В этом разделе описывается, как проверить связь с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], используя программу **sqlcmd** .  
  
##  <a name="SSMSProcedure"></a>  
  
#### Вход в экземпляр SQL Server по умолчанию  
  
1.  В командной строке введите следующую команду для соединения с использованием проверки подлинности Windows:  
  
    ```  
    sqlcmd [ /E ] [ /S servername ]  
  
    ```  
  
#### Вход в именованный экземпляр SQL Server  
  
1.  В командной строке введите следующую команду для соединения с использованием проверки подлинности Windows:  
  
    ```  
    sqlcmd [ /E ] /S servername\instancename  
  
    ```  
  
## См. также:  
 [Программа sqlcmd](../../tools/sqlcmd-utility.md)   
 [Программа osql](../../tools/osql-utility.md)  
  
  