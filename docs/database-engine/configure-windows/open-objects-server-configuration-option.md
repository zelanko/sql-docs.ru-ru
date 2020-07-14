---
title: Параметр конфигурации сервера "open objects" | Документы Майкрософт
description: Изучите отключенный параметр конфигурации open objects. Узнайте, как SQL Server управляет количеством открытых объектов базы данных.
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- open objects option
ms.assetid: c8424d3c-86ba-4cc5-bf0c-be4ce44bdd04
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 0bbcb11a80f06eae10e5481c965e9216cc84695e
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85773620"
---
# <a name="open-objects-server-configuration-option"></a>Параметр конфигурации сервера «open objects»
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Этот параметр по-прежнему поддерживается хранимой процедурой **sp_configure**, хотя его функциональность в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отключена. (Параметр не влияет на работу сервера.) В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] количество открытых объектов базы данных управляется динамически и ограничено только объемом доступной памяти. Параметр **open objects** поддерживается процедурой **SP_CONFIGURE** для обеспечения обратной совместимости с существующими скриптами.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  
