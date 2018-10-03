---
title: MSSQLSERVER_15599 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 15599 (Database Engine error)
ms.assetid: 97e427a9-8587-46ea-954b-974b5df9c223
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e1e4988bea932b8279a1d5b754ef3d0271e3aa1c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48100594"
---
# <a name="mssqlserver15599"></a>MSSQLSERVER_15599
    
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
  
  
