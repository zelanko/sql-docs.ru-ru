---
title: SQL Server, объект SQL Errors | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQL Errors object
- SQLServer:SQL Errors
ms.assetid: 6e5273ca-29cb-4618-88a2-70b9b8d6cf76
caps.latest.revision: 14
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a843a34c21cf6567c6f55f233dc56febbb265d6e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sql-server-sql-errors-object"></a>SQL Server, объект SQL Errors
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Объект **SQLServer: ошибки SQL** в Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обеспечивает счетчики для контроля работы **SQL Errors**.  
  
 В этой таблице описаны счетчики [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **SQL Errors** .  
  
|Счетчики SQL Server SQL Errors|Description|  
|------------------------------------|-----------------|  
|**Ошибок/с**|Количество ошибок в секунду.|  
  
 Каждый из счетчиков объекта содержит следующие экземпляры.  
  
|Элемент|Определение|  
|----------|----------------|  
|**_Total**|Сведения обо всех ошибках.|  
|**Ошибки DB в режиме «вне сети»**|Отслеживает серьезные ошибки, которые заставляют [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] переключать текущую базу данных в режим «вне сети».|  
|**Информационные ошибки**|Сведения, связанные с сообщениями об ошибках, которые предоставляют данные пользователям, но не вызывают ошибок.|  
|**Ошибки разрыва соединения**|Отслеживает ошибки, которые заставляют [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] разорвать текущее соединение.|  
|**Пользовательские ошибки**|Сведения об ошибках пользователя.|  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
