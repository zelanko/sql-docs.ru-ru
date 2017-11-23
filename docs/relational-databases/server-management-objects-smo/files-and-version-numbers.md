---
title: "Файлы и номера версий | Документы Microsoft"
ms.custom: 
ms.date: 08/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, versions
- components [SMO]
- files [SMO], components
- SMO [SQL Server], versions
- versions [SMO]
ms.assetid: 510907b6-e7a9-41bd-b892-d6d99a5118e1
caps.latest.revision: "34"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1a81684285e79e8e79ca1eca79ef24310d64502e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="files-and-version-numbers"></a>Файлы и номера версий
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Все необходимые компоненты управляющих объектов SQL Server (SMO) входят в пакет Microsoft.SqlServer.SqlManagementObjects NuGet. Объекты SMO реализованы в нескольких управляемых сборках. Можно разрабатывать приложения объектов SMO либо на клиенте, либо на сервере.  

>>[!Important]
Версия файла сборки объектов SMO отображается как основной. **0**. Build.Revision. Но версия внедренную сборку основной. **100**. Build.Revision. Это позволяет отделить версия объектов SMO, используемые в каждом приложении, поэтому одного обновления не влияют на других.
>>
>>По этой причине следует **не** установить эти версии сборок в глобальный кэш сборок (GAC). Это может привести к другим приложениям, например [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio, чтобы приостановить выполнение. 
  
|Файл|Description|  
|-----------|-----------------|  
|Microsoft.SqlServer.ConnectionInfo.dll|Содержит поддержку для соединения с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|Microsoft.SqlServer.ServiceBrokerEnum.dll|Содержит поддержку программирования компонента [!INCLUDE[msCoName](../../includes/msconame-md.md)] Service Broker. Это требуется только в программах, которые используют компонент Service Broker.|  
|Microsoft.SqlServer.Smo.dll|Содержит большинство классов SMO.|  
|Microsoft.SqlServer.SmoExtended.dll<br /><br /> Microsoft.SqlServer.Management.Sdk.Sfc.dll<br /><br /> Microsoft.SqlServer.SqlEnum.dll|Содержит поддержку для классов SMO.|  
|Microsoft.SqlServer.WmiEnum.dll|Содержит классы поставщика инструментария управления Windows (WMI). Это требуется только для программ, которые используют классы поставщика WMI.|  
|Microsoft.SqlServer.RegSvrEnum.dll|Содержит классы зарегистрированного сервера. Это требуется только для программ, которые используют классы зарегистрированного сервера.|  
  
  
