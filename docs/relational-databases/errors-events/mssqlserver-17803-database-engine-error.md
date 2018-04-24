---
title: MSSQLSERVER_17803 | Документация Майкрософт
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
- 17803 (Database Engine error)
ms.assetid: 28591a19-258d-4891-b78a-4686789bb2d7
caps.latest.revision: 14
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 84dad82e56f418813c5a6ddfaf5425b3b9aec9f8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver17803"></a>MSSQLSERVER_17803
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|17803|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SRV_NOMEMORY|  
|Текст сообщения|Во время установления соединения произошла ошибка выделения памяти. Сократите необязательный расход памяти или увеличьте объем системной памяти. Соединение было закрыто.%.*ls|  
  
## <a name="explanation"></a>Объяснение  
Серверу не хватает памяти.  
  
## <a name="user-action"></a>Действие пользователя  
Определите причину нехватки памяти на сервере. Возможно, окажутся полезными общие шаги по устранению неполадок с памятью.  
  
