---
title: MSSQLSERVER_9692 | Документация Майкрософт
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
- 9692 (Database Engine error)
ms.assetid: 02399d6e-ab5e-4f30-8a3e-2bb1e8c135b5
caps.latest.revision: 15
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 85dcc73a02f7d25f3e0c6a77f6bdcc633449779c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver9692"></a>MSSQLSERVER_9692
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|9692|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SB2_CANT_LISTEN_PORT_IN_USE|  
|Текст сообщения|Транспортному протоколу %S_MSG не удается прослушать порт %d, поскольку он занят другим процессом.|  
  
## <a name="explanation"></a>Объяснение  
Указанный TCP-порт используется другим приложением или компьютером.  
  
## <a name="user-action"></a>Действие пользователя  
Выполните команду **netstat -aon**, чтобы выяснить, какая программа использует порт. Закройте это приложение или укажите другой порт для компонента Service Broker.  
  
