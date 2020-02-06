---
title: MSSQLSERVER_18264 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 18264 (Database Engine error)
ms.assetid: 3050fc56-2be5-43cf-916b-50a3ac5f89aa
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: df0bd7c7093aeb46421fca75c9e9233f2b1f4263
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68137134"
---
# <a name="mssqlserver_18264"></a>MSSQLSERVER_18264
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
  
