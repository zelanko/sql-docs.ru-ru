---
title: SQL Server, объект SQL Errors | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
s.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQL Errors object
- SQLServer:SQL Errors
ms.assetid: 6e5273ca-29cb-4618-88a2-70b9b8d6cf76
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 0372670c89a2367bf12bc646d6aada5ceba29776
ms.sourcegitcommit: ca038f1ef180e4e1b27910bbc5d87822cd1ed176
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2018
ms.locfileid: "52158592"
---
# <a name="sql-server-sql-errors-object"></a>SQL Server, объект SQL Errors
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Объект **SQLServer: ошибки SQL** в Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обеспечивает счетчики для контроля работы **SQL Errors**.  
  
 В этой таблице описаны счетчики [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **SQL Errors** .  
  
|Счетчики SQL Server SQL Errors|Описание|  
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
  
  
