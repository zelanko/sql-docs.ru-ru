---
title: MSSQLSERVER_15599 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 15599 (Database Engine error)
ms.assetid: 97e427a9-8587-46ea-954b-974b5df9c223
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 35ad5fd021845a0f528ed1a46aac61b93da015c8
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68100415"
---
# <a name="mssqlserver_15599"></a>MSSQLSERVER_15599
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
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
  
