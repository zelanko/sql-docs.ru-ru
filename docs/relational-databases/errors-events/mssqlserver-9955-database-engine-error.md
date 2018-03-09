---
title: "MSSQLSERVER_9955 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 9955 (Database Engine error)
ms.assetid: 77f30570-7790-4747-b372-eac71c036e19
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b5ac734473c592a347c8c954d7815b43869d3b9c
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver9955"></a>MSSQLSERVER_9955
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|9955|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|FTXT2_MSSEARCHACCESSDENY|  
|Текст сообщения|SQL Server не удалось создать именованный канал "%ls" для обмена данными с управляющей программой полнотекстовой фильтрации (ошибка Windows: %d). Именованный канал для процесса узла управляющей программы фильтрации уже существует, системе не хватает ресурсов или не удалось найти идентификатор безопасности для ее группы учетной записи. чтобы решить эту проблему, завершите все запущенные процессы управляющей программы полнотекстовой фильтрации и при необходимости измените конфигурацию учетной записи службы запуска этой программы.|  
  
## <a name="explanation"></a>Объяснение  
Это сообщение возникло потому, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не удалось создать именованный канал для обмена данными с управляющей программой полнотекстовой фильтрации. Именованный канал для процесса узла управляющей программы фильтрации уже существует, системе не хватает ресурсов или не удалось найти идентификатор безопасности для ее группы учетной записи.  
  
## <a name="user-action"></a>Действие пользователя  
Чтобы устранить эту ошибку, завершите все запущенные процессы управляющей программы полнотекстовой фильтрации и при необходимости измените конфигурацию учетной записи этой программы с помощью диспетчера конфигурации SQL Server.  
  
## <a name="see-also"></a>См. также:  
[Диспетчер конфигурации SQL Server](~/relational-databases/sql-server-configuration-manager.md)  
[Настройка учетной записи службы средства запуска управляющей программы полнотекстовой фильтрации](~/relational-databases/search/set-the-service-account-for-the-full-text-filter-daemon-launcher.md)  
[Полнотекстовый поиск](~/relational-databases/search/full-text-search.md)  
  
