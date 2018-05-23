---
title: MSSQLSERVER_15599 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 15599 (Database Engine error)
ms.assetid: 97e427a9-8587-46ea-954b-974b5df9c223
caps.latest.revision: 8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 706b5a8d0750afcd04f2d7ff95800fb6d284345a
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
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
  
