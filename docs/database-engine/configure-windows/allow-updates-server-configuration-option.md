---
title: Параметр конфигурации сервера "allow updates" | Документы Майкрософт
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- allow updates option
ms.assetid: 3967c3ed-280a-4de8-a2ce-393e82745a7b
author: MikeRayMSFT
ms.author: mikeray
manager: jroth
ms.openlocfilehash: 2be9a6eb16bf2b4f481faf6409b28da11eb39eb5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66799568"
---
# <a name="allow-updates-server-configuration-option"></a>Параметр конфигурации сервера «allow updates»
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Этот параметр по-прежнему присутствует в хранимой процедуре **sp_configure** , хотя его функции недоступны в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Параметр не влияет на работу сервера. Непосредственные обновления системных таблиц не поддерживаются.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
 Изменение параметра **allow updates** приведет к сбою при выполнении инструкции RECONFIGURE. Изменения параметра **allow updates** необходимо удалить из всех скриптов.  
  
## <a name="see-also"></a>См. также:  
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  
