---
title: MSSQLSERVER_9955 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 9955 (Database Engine error)
ms.assetid: 77f30570-7790-4747-b372-eac71c036e19
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a7b77ea2e16a65d1fc93bc7199a8006c5e240561
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47640103"
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
  
