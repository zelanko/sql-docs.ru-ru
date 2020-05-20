---
title: dbo. sysnotifications (Transact-SQL) | Документация Майкрософт
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
ms.openlocfilehash: 69a2c9dea5f2ce0745bf30cef9a99eb0b245c433
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82806838"
---
# <a name="dbosysnotifications-transact-sql"></a>dbo.sysnotifications (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит одну строку для каждого уведомления.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**alert_id**|**int**|Идентификатор предупреждения.|  
|**operator_id**|**int**|Идентификатор оператора, которому должно быть отправлено это уведомление.|  
|**notification_method**|**tinyint**|Способ уведомления:<br /><br /> **1** = электронная почта<br /><br /> **2** = пейджер<br /><br /> **4**  =  **NetSend**<br /><br /> **7** = все|  
  
  
