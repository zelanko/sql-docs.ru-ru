---
title: MSSQLSERVER_15599 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 15599 (Database Engine error)
ms.assetid: 97e427a9-8587-46ea-954b-974b5df9c223
caps.latest.revision: 8
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4a5e9dadf7e4e7d726ec7943712cf2053d2bc728
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver15599"></a>MSSQLSERVER_15599
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|15599|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SEC_LOCAL_TEMP_AUDIT_PERMISSIONS|  
|Текст сообщения|Аудит и разрешения нельзя задать для локальных временных объектов.|  
  
## <a name="explanation"></a>Объяснение  
Аудит и разрешения не работают при установке для локальных или глобальных временных объектов. Инструкция не завершилась ошибкой (возвращен успешный код), но не имела никакого эффекта.  
  
Это поведение не изменилось, хотя, начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], это информационное сообщение предупреждает пользователя.  
  
## <a name="user-action"></a>Действие пользователя  
Действия не требуются, но подумайте над удалением инструкций, которые пытаются установить аудит или разрешения на локальных или глобальных временных объектах.  
  
