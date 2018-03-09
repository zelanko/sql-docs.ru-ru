---
title: "MSSQLSERVER_3413 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 3413 (Database Engine error)
ms.assetid: 3fa07637-ba93-4633-aaf2-ade7d18bc487
caps.latest.revision: "16"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a80a7910d387e31efd48e487761a133c9598dfbd
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver3413"></a>MSSQLSERVER_3413
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|3413|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|MARKDB|  
|Текст сообщения|Идентификатор базы данных %d. Не удалось пометить базу данных как подозрительную. Не удалось выполнить просмотр Getnext NC по sys.databases.database_id. Просмотрите предыдущие ошибки в журнале ошибок для определения причины и устраните выявленные проблемы.|  
  
## <a name="explanation"></a>Объяснение  
При попытке пометить в каталоге пользовательскую базу данных признаком SUSPECT произошел непредвиденный сбой. Состояние SUSPECT установлено не будет.  
  
## <a name="user-action"></a>Действие пользователя  
Для исправления этой неполадки см. предыдущие ошибки.  
  
