---
title: "Создание файлов подключения сервера (AccessToSQL) | Документы Microsoft"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 08/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 829153be-aa8e-4162-87e8-69882feecf19
caps.latest.revision: "10"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 085b89aa994ddd7b94353ab2a4e075d837298643
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="creating-the-server-connection-files-accesstosql"></a>При создании сервера файлы подключения (AccessToSQL)
Сведения о сервере может быть указано либо в разделе серверы файла скрипта. Сведения о сервере также можно указать в файле подключения отдельный сервер. Параметр командной строки файла подключения к серверу `-c <serverconnectionfile>`. Если один и тот же идентификатор сервера в файлы подключения скрипта и сервера отсутствует, то считается определение сервера в файле скрипта.  
  
```xml  
<!--Sample of server connection file commands -->  
<!--Connection to SQL Server-->  
  
<sql-server name="target_3">  
  
  <sql-server-authentication>  
  
    <server value="$TargetServerName$"/>  
  
    <database value="$TargetDB$"/>  
  
    <user-id value="$TargetUserName$"/>  
  
    <password value="$TargetPassword$"/>  
  
    <encrypt value="true"/>  
  
    <trust-server-certificate value="true"/>  
  
  </sql-server-authentication>  
  
</sql-server>  
```  
  
```xml  
<!--Connection to SQL Azure-->  
  
<sql-azure name="target_azure">  
  
  <server value="$TargetAzureServerName$"/>  
  
  <database value="$TargetAzureDB$"/>  
  
  <user-id value="$TargetAzureUserName$"/>  
  
  <password value="$TargetAzurePassword$"/>  
  
</sql-azure>  
```  
  
## <a name="server-connection-file-validation"></a>Проверка файла подключения сервера  
Пользователь легко может проверить свой файл подключения сервера соответствие файлу определения схемы **«A2SSConsoleScriptServersSchema.xsd»** доступны в папке «Схемы».  
  
## <a name="next-step"></a>Следующий шаг  
Следующий шаг в работе консоли — [выполнение консоли SSMA &#40; AccessToSQL &#41;](../../ssma/access/executing-the-ssma-console-accesstosql.md)  
  
## <a name="see-also"></a>См. также:  
[Выполнение консоли SSMA (Access)](http://msdn.microsoft.com/aa1bf665-8dc0-4259-b36f-46ae67197a43)  
  
