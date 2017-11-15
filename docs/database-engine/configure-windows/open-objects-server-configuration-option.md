---
title: "Параметр конфигурации сервера \"open objects\" | Документы Майкрософт"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: open objects option
ms.assetid: c8424d3c-86ba-4cc5-bf0c-be4ce44bdd04
caps.latest.revision: "26"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d0c744f522f3ed900d7da97d8486a99a9288258c
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="open-objects-server-configuration-option"></a>Параметр конфигурации сервера «open objects»
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Этот параметр по-прежнему поддерживается хранимой процедурой **sp_configure**, хотя его функциональность в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отключена. (Параметр не влияет на работу сервера.) В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] количество открытых объектов базы данных управляется динамически и ограничено только объемом доступной памяти. Параметр **open objects** поддерживается процедурой **SP_CONFIGURE** для обеспечения обратной совместимости с существующими скриптами.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  
