---
title: "Параметр конфигурации сервера &#171;open objects&#187; | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "open objects, параметр"
ms.assetid: c8424d3c-86ba-4cc5-bf0c-be4ce44bdd04
caps.latest.revision: 26
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 26
---
# Параметр конфигурации сервера &#171;open objects&#187;
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Этот параметр по-прежнему поддерживается хранимой процедурой **sp_configure**, хотя его функциональность в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отключена. (Параметр не влияет на работу сервера.) В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] количество открытых объектов базы данных управляется динамически и ограничено только объемом доступной памяти. Параметр **open objects** поддерживается процедурой **SP_CONFIGURE** для обеспечения обратной совместимости с существующими скриптами.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
## См. также:  
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  