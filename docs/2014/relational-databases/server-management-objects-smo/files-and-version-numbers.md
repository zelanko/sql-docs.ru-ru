---
title: Файлы и номера версий | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, versions
- components [SMO]
- files [SMO], components
- SMO [SQL Server], versions
- versions [SMO]
ms.assetid: 510907b6-e7a9-41bd-b892-d6d99a5118e1
author: stevestein
ms.author: sstein
ms.openlocfilehash: f1a7286f15af28f97e488b8b40fd745a0d320108
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "84997139"
---
# <a name="files-and-version-numbers"></a>Файлы и номера версий
  Все необходимые [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компоненты объектов SMO устанавливаются как часть экземпляра [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] клиента или сервера. Объекты SMO реализованы в нескольких управляемых сборках. Можно разрабатывать приложения объектов SMO либо на клиенте, либо на сервере.  
  
|Каталог|Файл|Описание|  
|---------------|----------|-----------------|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|Microsoft.SqlServer.ConnectionInfo.dll|Содержит поддержку для соединения с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|Microsoft.SqlServer.ServiceBrokerEnum.dll|Содержит поддержку программирования компонента [!INCLUDE[msCoName](../../includes/msconame-md.md)] Service Broker. Это требуется только в программах, которые используют компонент Service Broker.|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|Microsoft.SqlServer.Smo.dll|Содержит большинство классов SMO.|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|Microsoft.SqlServer.SmoExtended.dll<br /><br /> Microsoft.SqlServer.Management.Sdk.Sfc.dll<br /><br /> Microsoft.SqlServer.SqlEnum.dll|Содержит поддержку для классов SMO.|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|Microsoft.SqlServer.WmiEnum.dll|Содержит классы поставщика инструментария управления Windows (WMI). Это требуется только для программ, которые используют классы поставщика WMI.|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|Microsoft.SqlServer.RegSvrEnum.dll|Содержит классы зарегистрированного сервера. Это требуется только для программ, которые используют классы зарегистрированного сервера.|  
  
  
