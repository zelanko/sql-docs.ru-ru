---
title: "MSSQLSERVER_18264 | Документация Майкрософт"
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
- 18264 (Database Engine error)
ms.assetid: 3050fc56-2be5-43cf-916b-50a3ac5f89aa
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5bcae15f84f9bdc33de072f2df2d5acb0cc9b59a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver18264"></a>MSSQLSERVER_18264
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|Microsoft SQL Server|  
|Идентификатор события|18264|  
|Источник события|MSSQLENGINE|  
|Компонент|SQLEngine|  
|Символическое имя|STRMIO_DBDUMP|  
|Текст сообщения|Выполнено резервное копирование базы данных. База данных: %s, дата (время) создания: % s(%s), страниц в дампе: %d, первый номер LSN: %s, последний номер LSN: %s, число устройств хранения: %d, сведения об устройствах: (%s). Это информационное сообщение. Вмешательство пользователя не требуется.|  
  
## <a name="explanation"></a>Объяснение  
По умолчанию после каждого успешного создания резервной копии это информационное сообщение добавляется к журналу регистрации ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и к журналу системных событий. Если резервные копии журнала транзакций создаются очень часто, эти сообщения могут быстро накапливаться, создавая весьма крупные журналы регистрации ошибок, из-за чего возникают затруднения при поиске других сообщений.  
  
## <a name="user-action"></a>Действие пользователя  
Вы можете отключить эти записи журнала в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью флага трассировки **3226**. Включение этого флага трассировки может потребоваться, если резервное копирование журналов выполняется часто и если ни один из применяемых скриптов не зависит от указанных записей.  
  
Сведения об использовании флагов трассировки см. в электронной документации по SQL Server.  
  
## <a name="see-also"></a>См. также:  
[Флаги трассировки (Transact-SQL)](~/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)  
  
