---
title: MSSQLSERVER_1807 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 1807 (Database Engine error)
ms.assetid: 13c1b240-098b-4d9e-89aa-21599548e074
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 11203fe6329c373d46185f84920e60d3802f5c55
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver1807"></a>MSSQLSERVER_1807
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|1807|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|CANNOT_EX_LOCK|  
|Текст сообщения|Не удалось получить монопольную блокировку для базы данных «%.*ls». Повторите операцию позже.|  
  
## <a name="explanation"></a>Объяснение  
Операция, которой необходима монопольная блокировка базы данных, не смогла получить ее.  
  
## <a name="user-action"></a>Действие пользователя  
Отключите все соединения с базой данных и повторите запрос.  
  
