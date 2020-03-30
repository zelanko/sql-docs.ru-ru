---
title: Политика правильного перекрытия параметров affinity mask и affinity input-output mask
description: Узнайте, как включить политику, которая проверяет, имеет ли экземпляр SQL Server один или несколько процессоров, назначенных для использования с параметрами affinity mask и affinity I/O mask для управления на основе политик в SQL Server.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 1a0da6df-57ff-4f3f-aae9-2fbc4897508c
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: b225710aaadf3ea605e3cffd91a5a4fea2a51e62
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "75557806"
---
# <a name="correct-affinity-mask-and-affinity-input-and-output-mask-overlap"></a>Правильное перекрытие параметров affinity mask и affinity input-output mask
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Это правило проверяет, имеет ли экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] один или несколько процессоров, назначенных для использования как с параметром «affinity mask», так и с параметром «affinity I/O mask». На многопроцессорном компьютере параметры «affinity mask» и «affinity I/O mask» используются для определения процессоров, работающих с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если для ЦП включены оба параметра, то это может привести к снижению производительности, поскольку вызовет перегрузку процессора.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Необходимо указывать оба параметра, «affinity mask» и «affinity I/O mask», но включать каждый ЦП только для одного параметра.  
  
 Не допускайте, чтобы один и тот же ЦП оказывался задействованным для обоих параметров. Биты, относящиеся к каждому ЦП, должны находиться в одном из следующих состояний:  
  
-   значение 0 для обоих параметров, «affinity mask» и «affinity I/O mask»;  
  
-   значение 0 для параметра «affinity mask» и 1 для параметра «affinity I/O mask»;  
  
-   значение 1 для параметра «affinity mask» и 0 для параметра «affinity I/O mask».  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Параметр конфигурации сервера «affinity mask»](../../database-engine/configure-windows/affinity-mask-server-configuration-option.md)  
  
 [Параметр конфигурации сервера "affinity Input-Output mask"](../../database-engine/configure-windows/affinity-input-output-mask-server-configuration-option.md)  
  
 [Параметр конфигурации сервера «affinity64 mask»](../../database-engine/configure-windows/affinity64-mask-server-configuration-option.md)  
  
 [Параметр конфигурации сервера "affinity64 Input-Output mask"](../../database-engine/configure-windows/affinity64-input-output-mask-server-configuration-option.md)  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
