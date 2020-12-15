---
description: Файлы и номера версий
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
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e82feaa49d5474cd0f621b36b3099dc6f97c8e65
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97467215"
---
# <a name="files-and-version-numbers"></a>Файлы и номера версий
[!INCLUDE [SQL Server ASDB, ASDBMI, ASDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa.md)]

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
  
  
