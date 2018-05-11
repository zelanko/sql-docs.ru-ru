---
title: MSSQLSERVER_5554 | Документация Майкрософт
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
- 5554 (Database Engine error)
ms.assetid: 7134bbe5-d240-4a98-85ce-b13cc8ae9b0e
caps.latest.revision: 12
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 496718ec066f690ddd6e14e9937e356b40ef819b
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver5554"></a>MSSQLSERVER_5554
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|MSSQLSERVER|  
|Идентификатор события|5554|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|FS_MINIVER_OVERFLOW|  
|Текст сообщения|Достигнут максимальный предел общего числа версий одного файла, установленный для файловой системы.|  
  
## <a name="explanation"></a>Объяснение  
В режиме MARS и скриптах триггера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует мини-версию, указанную операционной системой.  
  
## <a name="user-action"></a>Действие пользователя  
Постарайтесь избежать повторного обновления данных в одной транзакции.  
  
