---
title: Параметр конфигурации сервера "open objects" | Документы Майкрософт
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.suite: sql
ms.technology: configuration
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- open objects option
ms.assetid: c8424d3c-86ba-4cc5-bf0c-be4ce44bdd04
caps.latest.revision: 26
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 5eaa343040d5cda4afd499eee8a3a1fee8406154
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32863829"
---
# <a name="open-objects-server-configuration-option"></a>Параметр конфигурации сервера «open objects»
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Этот параметр по-прежнему поддерживается хранимой процедурой **sp_configure**, хотя его функциональность в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]отключена. (Параметр не влияет на работу сервера.) В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] количество открытых объектов базы данных управляется динамически и ограничено только объемом доступной памяти. Параметр **open objects** поддерживается процедурой **SP_CONFIGURE** для обеспечения обратной совместимости с существующими скриптами.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  
