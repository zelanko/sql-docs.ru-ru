---
title: "MSSQLSERVER_3437 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 3437 (Database Engine error)
ms.assetid: b38216e2-b650-43bd-97af-061d54f60031
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 62fcf4360a9b5eefc971bf0f5443a9e9e96004aa
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver3437"></a>MSSQLSERVER_3437
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|3437|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|NODTC|  
|Текст сообщения|При восстановлении базы данных «%.*ls» произошла ошибка. Невозможно подключиться к координатору распределенных транзакций Майкрософт (MS DTC) для проверки состояния завершения транзакции %S_XID. Исправьте MS DTC и запустите восстановление еще раз.|  
  
## <a name="explanation"></a>Объяснение  
На момент закрытия базы данных одна или несколько распределенных транзакций, использующих координатор распределенных транзакций [!INCLUDE[msCoName](../../includes/msconame-md.md)] (MS DTC), не были завершены. Восстановление этой базы данных завершилось неуспешно, так как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не удалось подключиться к MS DTC для завершения или отката транзакций.  
  
## <a name="user-action"></a>Действие пользователя  
Для восстановления этой базы данных сначала необходимо устранить неполадку с MS DTC. Для поиска проблемы, связанной с MS DTC, просмотрите журналы событий Windows. Если решить проблему с MS DTC и исправить базу данных невозможно, восстановите базу данных из резервной копии.  
  

