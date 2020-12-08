---
title: SQL Server, объект SQL Errors | Документация Майкрософт
description: Сведения об объекте SQLServer:SQL Errors, который предоставляет счетчики для отслеживания ошибок SQL в SQL Server.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQL Errors object
- SQLServer:SQL Errors
ms.assetid: 6e5273ca-29cb-4618-88a2-70b9b8d6cf76
author: WilliamDAssafMSFT
ms.author: wiassaf
ms.openlocfilehash: e0433802954301c9ea5a9e483c0e54ca893f6b2d
ms.sourcegitcommit: 0e0cd9347c029e0c7c9f3fe6d39985a6d3af967d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2020
ms.locfileid: "96505589"
---
# <a name="sql-server-sql-errors-object"></a>SQL Server, объект SQL Errors
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Объект **SQLServer: ошибки SQL** в Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обеспечивает счетчики для контроля работы **SQL Errors**.  
  
 В этой таблице описаны счетчики [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Ошибки SQL**.  
  
|Счетчики SQL Server SQL Errors|Описание|  
|------------------------------------|-----------------|  
|**Ошибок/с**|Количество ошибок в секунду.|  
  
 Каждый из счетчиков объекта содержит следующие экземпляры.  
  
|Item|Определение|  
|----------|----------------|  
|**_Total**|Сведения обо всех ошибках.|  
|**Ошибки DB в режиме «вне сети»**|Отслеживает серьезные ошибки, которые заставляют [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] переключать текущую базу данных в режим «вне сети».|  
|**Информационные ошибки**|Сведения, связанные с сообщениями об ошибках, которые предоставляют данные пользователям, но не вызывают ошибок.|  
|**Ошибки разрыва соединения**|Отслеживает ошибки, которые заставляют [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] разорвать текущее соединение.|  
|**Пользовательские ошибки**|Сведения об ошибках пользователя.|  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
