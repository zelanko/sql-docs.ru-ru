---
title: SQL Server, объект SQL Errors | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQL Errors object
- SQLServer:SQL Errors
ms.assetid: 6e5273ca-29cb-4618-88a2-70b9b8d6cf76
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f36cd694756544a44df657d97fd84e1967167b55
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63183007"
---
# <a name="sql-server-sql-errors-object"></a>SQL Server, объект SQL Errors
  Объект **SQLServer: ошибки SQL** в Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обеспечивает счетчики для контроля работы **SQL Errors**.  
  
 В этой таблице описаны счетчики [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **SQL Errors** .  
  
|Счетчики SQL Server SQL Errors|Description|  
|------------------------------------|-----------------|  
|**Ошибок в секунду**|Количество ошибок в секунду.|  
  
 Каждый из счетчиков объекта содержит следующие экземпляры.  
  
|Элемент|Определение|  
|----------|----------------|  
|**_Total**|Сведения обо всех ошибках.|  
|**Автономные ошибки базы данных**|Отслеживает серьезные ошибки, которые заставляют [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] переключать текущую базу данных в режим «вне сети».|  
|**Сведения об ошибках**|Сведения, связанные с сообщениями об ошибках, которые предоставляют данные пользователям, но не вызывают ошибок.|  
|**Ошибки при уничтожении соединения**|Отслеживает ошибки, которые заставляют [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] разорвать текущее соединение.|  
|**Ошибки пользователей**|Сведения об ошибках пользователя.|  
  
## <a name="see-also"></a>См. также:  
 [Мониторинг использования ресурсов &#40;системном мониторе&#41;](monitor-resource-usage-system-monitor.md)  
  
  
