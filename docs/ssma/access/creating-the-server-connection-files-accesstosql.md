---
description: Создание файлов подключения к серверу (Акцесстоскл)
title: Создание файлов подключения к серверу (Акцесстоскл) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 08/17/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 829153be-aa8e-4162-87e8-69882feecf19
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 20c47935963473b7b6aced7d6b3eed4a53afbeac
ms.sourcegitcommit: a41e1f4199785a2b8019a419a1f3dcdc15571044
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/13/2020
ms.locfileid: "91987520"
---
# <a name="creating-the-server-connection-files-accesstosql"></a>Создание файлов подключения к серверу (Акцесстоскл)
Сведения о сервере можно указать в разделе Servers файла скрипта. Сведения о сервере также можно указать в отдельном файле соединения сервера. Параметр командной строки для файла соединения с сервером — `-c <serverconnectionfile>` . Если один и тот же идентификатор сервера имеется в файлах соединения скрипта и сервера, то считается, что определение сервера в файле сценария.  
  
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
  
## <a name="server-connection-file-validation"></a>Проверка файлов подключения к серверу  
Пользователь может легко проверить файл подключения своего сервера по отношению к файлу определения схемы **"A2SSConsoleScriptServersSchema. xsd"** , доступному в папке "Schemas".  
  
## <a name="next-step"></a>Следующий шаг  
Следующий шаг в работе консоли заключается [в выполнении консоли SSMA &#40;акцесстоскл&#41;](../../ssma/access/executing-the-ssma-console-accesstosql.md)  
  
## <a name="see-also"></a>См. также статью  
[Запуск консоли SSMA (доступ)](./executing-the-ssma-console-accesstosql.md)  
