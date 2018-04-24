---
title: MSSQLSERVER_9790 | Документация Майкрософт
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
- 9790 (Database Engine error)
ms.assetid: 83fd379f-5deb-4f97-8cb4-282e3d3fed94
caps.latest.revision: 13
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 27f8ec87871d65f93aec1ed4c4914e3c7511fb56
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver9790"></a>MSSQLSERVER_9790
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|9790|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SB3_XMIT_ERROR_ENTRANCE_BROKER_SINGLE_USER|  
|Текст сообщения|Не удалось найти маршрут для входящего сообщения. Системная база данных MSDB, содержащая сведения о маршрутах, находится в режиме SINGLE USER.|  
  
## <a name="explanation"></a>Объяснение  
Произошла ошибка при попытке определения категории сообщения, полученного в автономном режиме, поскольку база данных MSDB находилась в однопользовательском режиме.  
  
## <a name="user-action"></a>Действие пользователя  
С помощью команды ALTER DATABASE измените режим MSDB на MULTI USER.  
  
