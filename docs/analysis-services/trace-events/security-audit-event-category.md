---
title: "Категория событий Security Audit | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- Security Audit event category [SQL Server]
- event classes [Analysis Services], security audit
- security events [Analysis Services]
ms.assetid: 9686a495-68d7-4137-8e30-2655aa519f6c
caps.latest.revision: "25"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8562e5c2ee33e2287ee961a0afc27ca7098b4819
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="security-audit-event-category"></a>Категория событий «Аудит безопасности»
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Категория событий «Аудит безопасности» содержит классы событий, описанные в следующей таблице.  
  
|Класс событий|Идентификатор события|Description|  
|-----------------|--------------|-----------------|  
|Аудит входа в систему|1|Записывает все новые события соединения с момента запуска трассировки, например запросы клиентов на соединение с сервером, на котором запущен экземпляр служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|Аудит выхода из системы|2|Записывает все новые события отключения с момента запуска трассировки, например выполнение клиентом команды отключения.|  
|Audit Server Starts and Stops|4|Записывает операции выключения, запуска и приостановки служб.|  
|Событие аудита разрешений на объекты|18|Записывает все изменения разрешений на объекты.|  
|Событие аудита операций администрирования|19|Записывает серверные операции резервного копирования, восстановления, синхронизации, присоединения, отсоединения, загрузки образа и сохранения образа.|  
  
 Дополнительные сведения о столбцах, связанных с каждым из классов событий «Аудит безопасности», см. в разделе [Security Audit Data Columns](../../analysis-services/trace-events/security-audit-data-columns.md).  
  
## <a name="see-also"></a>См. также  
 [События трассировки служб Analysis Services](../../analysis-services/trace-events/analysis-services-trace-events.md)  
  
  
