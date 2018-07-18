---
title: Параметр конфигурации сервера "allow updates" | Документы Майкрософт
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
- allow updates option
ms.assetid: 3967c3ed-280a-4de8-a2ce-393e82745a7b
caps.latest.revision: 32
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: df8f7533f3e0ff76117d6a0e343d72a761708352
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32863099"
---
# <a name="allow-updates-server-configuration-option"></a>Параметр конфигурации сервера «allow updates»
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Этот параметр по-прежнему присутствует в хранимой процедуре **sp_configure** , хотя его функции недоступны в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Параметр не влияет на работу сервера. Непосредственные обновления системных таблиц не поддерживаются.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
 Изменение параметра **allow updates** приведет к сбою при выполнении инструкции RECONFIGURE. Изменения параметра **allow updates** необходимо удалить из всех скриптов.  
  
## <a name="see-also"></a>См. также:  
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  
