---
title: Категория событий Security Audit | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Security Audit event category [SQL Server]
- event classes [Analysis Services], security audit
- security events [Analysis Services]
ms.assetid: 9686a495-68d7-4137-8e30-2655aa519f6c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9d52589fc39376d5dfdfa3f540d3d1d47e89f448
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48224244"
---
# <a name="security-audit-event-category"></a>Категория событий «Аудит безопасности»
  Категория событий «Аудит безопасности» содержит классы событий, описанные в следующей таблице:  
  
|Класс событий|Идентификатор события|Описание|  
|-----------------|--------------|-----------------|  
|Аудит входа в систему|1|Записывает все новые события соединения с момента запуска трассировки, например запросы клиентов на соединение с сервером, на котором запущен экземпляр служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|Аудит выхода из системы|2|Записывает все новые события отключения с момента запуска трассировки, например выполнение клиентом команды отключения.|  
|Audit Server Starts and Stops|4|Записывает операции выключения, запуска и приостановки служб.|  
|Событие аудита разрешений на объекты|18|Записывает все изменения разрешений на объекты.|  
|Событие аудита операций администрирования|19|Записывает серверные операции резервного копирования, восстановления, синхронизации, присоединения, отсоединения, загрузки образа и сохранения образа.|  
  
 Дополнительные сведения о столбцах, связанных с каждым из классов событий «Аудит безопасности», см. в разделе [Security Audit Data Columns](security-audit-data-columns.md).  
  
## <a name="see-also"></a>См. также  
 [События трассировки служб Analysis Services](analysis-services-trace-events.md)  
  
  
