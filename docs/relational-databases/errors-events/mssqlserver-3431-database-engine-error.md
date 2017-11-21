---
title: "MSSQLSERVER_3431 | Документация Майкрософт"
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
- 3431 (Database Engine error)
ms.assetid: 9541217f-e5c6-4a12-a19a-006058f1d3f3
caps.latest.revision: 18
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: e7f4faa34293cba8f9b14e8b4d4b2c998f1eb12e
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver3431"></a>MSSQLSERVER_3431
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|3431|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|UNRESOLVED_XACT|  
|Текст сообщения|Не удалось восстановить базу данных «%.*ls» (идентификатор базы данных — %d) из-за неразрешенных результатов транзакций. Были подготовлены транзакции координатора распределенных транзакций Майкрософт (MS DTC), но координатору MS DTC не удалось выполнить разрешение. Для разрешения транзакций исправьте MS DTC, выполните восстановление из полной резервной копии или исправьте базу данных.|  
  
## <a name="explanation"></a>Объяснение  
На момент закрытия базы данных одна или несколько распределенных транзакций, использующих координатор распределенных транзакций [!INCLUDE[msCoName](../../includes/msconame-md.md)] (MS DTC), не были завершены. Восстановление этой базы данных завершилось неуспешно, так как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не удалось завершить или произвести откат транзакции, не имея дополнительной информации от MS DTC.  
  
## <a name="user-action"></a>Действие пользователя  
Для восстановления этой базы данных сначала необходимо устранить неполадку с MS DTC. Для поиска проблемы, связанной с MS DTC, просмотрите журналы событий Windows. Если решить проблему с MS DTC и исправить базу данных невозможно, восстановите базу данных из резервной копии.  
  

