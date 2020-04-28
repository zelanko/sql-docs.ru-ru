---
title: Файлы и номера версий | Документация Майкрософт
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
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
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7a7d7e7dd9bf7e6d5ad6dfa5776d76892f96ad05
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "70148660"
---
# <a name="files-and-version-numbers"></a>Файлы и номера версий
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Все SQL Server необходимые компоненты объектов SMO включены в пакет NuGet Microsoft. SqlServer. Склманажементобжектс. Объекты SMO реализованы в нескольких управляемых сборках. Можно разрабатывать приложения объектов SMO либо на клиенте, либо на сервере.  

> > [!Important]
> > Версия файла сборок SMO отображается как основная. **0**. Сборка. Редакция. Однако версия внедренной сборки является основной. **100**. Сборка. Редакция. Это делается для того, чтобы версия объектов SMO, используемая в каждом приложении, была раздельной, поэтому обновления для одного из них не влияют на другие.
> > 
> > Поэтому **не** следует устанавливать эти версии сборок в глобальный кэш сборок (GAC). Это может привести к сбою других приложений, например [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio. 
  
|Файл|Описание|  
|-----------|-----------------|  
|Microsoft.SqlServer.ConnectionInfo.dll|Содержит поддержку для соединения с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|Microsoft.SqlServer.ServiceBrokerEnum.dll|Содержит поддержку программирования компонента [!INCLUDE[msCoName](../../includes/msconame-md.md)] Service Broker. Это требуется только в программах, которые используют компонент Service Broker.|  
|Microsoft.SqlServer.Smo.dll|Содержит большинство классов SMO.|  
|Microsoft.SqlServer.SmoExtended.dll<br /><br /> Microsoft.SqlServer.Management.Sdk.Sfc.dll<br /><br /> Microsoft.SqlServer.SqlEnum.dll|Содержит поддержку для классов SMO.|  
|Microsoft.SqlServer.WmiEnum.dll|Содержит классы поставщика инструментария управления Windows (WMI). Это требуется только для программ, которые используют классы поставщика WMI.|  
|Microsoft.SqlServer.RegSvrEnum.dll|Содержит классы зарегистрированного сервера. Это требуется только для программ, которые используют классы зарегистрированного сервера.|  
  
  
