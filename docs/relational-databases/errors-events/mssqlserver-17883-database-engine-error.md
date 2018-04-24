---
title: MSSQLSERVER_17883 | Документация Майкрософт
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
- 17883 (Database Engine error)
ms.assetid: adaf1c04-e397-4a69-90b8-9353a37277ea
caps.latest.revision: 15
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 61ef7828090bb4992a8475ef7197d61e0a627577
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver17883"></a>MSSQLSERVER_17883
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|17883|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SRV_SCHEDULER_NONYIELDING|  
|Текст сообщения|Процесс %ld:%ld:%ld (0x%lx) Worker 0x%p, по-видимому, не возвращает управление планировщику %ld. Время создания потока: %I64d. Примерная загрузка ЦП для потока: ядро %I64d мс, пользователь %I64d мс. Эффективность использования процесса %d%%. Бездействие системы %d%%. Интервал: %I64d мс.|  
  
## <a name="explanation"></a>Объяснение  
Указывает на возможную проблему, в результате которой поток не возвращает управление планировщику.  Возможно, это сбой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] либо [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не получает достаточно циклов процессора для выполнения.  Эта ошибка может исчезнуть, если поток, в конце концов, передаст управление.  
  
## <a name="user-action"></a>Действие пользователя  
В случае избыточной нагрузки на систему уменьшите ее. В противном случае обратитесь в службу поддержки пользователей Майкрософт.  
  
