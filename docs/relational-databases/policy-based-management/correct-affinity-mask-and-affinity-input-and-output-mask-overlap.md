---
title: "Correct Affinity Mask and Affinity Input and Output Mask Overlap | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Лучшие решения [компонент Database Engine]"
ms.assetid: 1a0da6df-57ff-4f3f-aae9-2fbc4897508c
caps.latest.revision: 11
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 11
---
# Correct Affinity Mask and Affinity Input and Output Mask Overlap
  Это правило проверяет, имеет ли экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] один или несколько процессоров, назначенных для использования как с параметром «affinity mask», так и с параметром «affinity I/O mask». На многопроцессорном компьютере параметры «affinity mask» и «affinity I/O mask» используются для определения процессоров, работающих с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если для ЦП включены оба параметра, то это может привести к снижению производительности, поскольку вызовет перегрузку процессора.  
  
## Рекомендации  
 Необходимо указывать оба параметра, «affinity mask» и «affinity I/O mask», но включать каждый ЦП только для одного параметра.  
  
 Не допускайте, чтобы один и тот же ЦП оказывался задействованным для обоих параметров. Биты, относящиеся к каждому ЦП, должны находиться в одном из следующих состояний:  
  
-   значение 0 для обоих параметров, «affinity mask» и «affinity I/O mask»;  
  
-   значение 0 для параметра «affinity mask» и 1 для параметра «affinity I/O mask»;  
  
-   значение 1 для параметра «affinity mask» и 0 для параметра «affinity I/O mask».  
  
## Дополнительные сведения см. в разделе  
 [Параметр конфигурации сервера «affinity mask»](../../database-engine/configure-windows/affinity-mask-server-configuration-option.md)  
  
 [Параметр конфигурации сервера "affinity Input-Output mask"](../../database-engine/configure-windows/affinity-input-output-mask-server-configuration-option.md)  
  
 [Параметр конфигурации сервера «affinity64 mask»](../../database-engine/configure-windows/affinity64-mask-server-configuration-option.md)  
  
 [Параметр конфигурации сервера "affinity64 Input-Output mask"](../../database-engine/configure-windows/affinity64-input-output-mask-server-configuration-option.md)  
  
## См. также:  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  