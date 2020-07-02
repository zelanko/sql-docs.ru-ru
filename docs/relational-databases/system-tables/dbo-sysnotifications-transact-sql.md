---
title: Уведомления dbo.sys(Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysnotifications_TSQL
- sysnotifications
- sysnotifications_TSQL
- dbo.sysnotifications
dev_langs:
- TSQL
helpviewer_keywords:
- sysnotifications system table
ms.assetid: c5150d18-e8b7-48a7-ada7-77c583af6e41
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ab37b30d501f84d3637df1410405c7554c5c8e22
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85750319"
---
# <a name="dbosysnotifications-transact-sql"></a>dbo.sysnotifications (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Содержит одну строку для каждого уведомления.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**alert_id**|**int**|Идентификатор предупреждения.|  
|**operator_id**|**int**|Идентификатор оператора, которому должно быть отправлено это уведомление.|  
|**notification_method**|**tinyint**|Способ уведомления:<br /><br /> **1** = электронная почта<br /><br /> **2** = пейджер<br /><br /> **4**  =  **NetSend**<br /><br /> **7** = все|  
  
  
