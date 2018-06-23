---
title: Альтернативные расположения папки моментальных снимков | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snapshots [SQL Server replication], alternate folder locations
- snapshot replication [SQL Server], alternate folder locations
- alternate snapshot folders [SQL Server replication]
ms.assetid: 437553b0-19df-4522-8f27-06b5bc747c69
caps.latest.revision: 35
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: a227b6226bfa3a38cd0566b64f8aa68aad42770f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101529"
---
# <a name="alternate-snapshot-folder-locations"></a>Альтернативные расположения папки моментальных снимков
  Альтернативные местоположения папки моментальных снимков позволяют хранить файлы моментальных снимков в местоположении, отличном от местоположения по умолчанию, которое обычно находится на распространителе. Альтернативным местоположением может быть другой сервер, сетевой диск или сменные носители, такие как компакт-диски или съемные диски.  
  
 Альтернативные папки моментальных снимков хранятся в виде свойства публикации. Так как альтернативное местоположение папки моментальных снимков является свойством публикации, агент распространителя и агент слияния могут найти надлежащий моментальный снимок в ходе процесса синхронизации.  
  
 Если хотите указать альтернативное расположение папки моментальных снимков или планируете сжимать файлы моментальных снимков, создайте публикацию без немедленного создания исходного моментального снимка, задайте в свойствах публикации расположение папки моментальных снимков, а затем запустите для этой публикации агент моментальных снимков. Если альтернативное местоположение изменено после создания исходного моментального снимка, снимки, уже созданные для публикации, не будут перемещены в новое альтернативное местоположение. В этом случае в зависимости от настроек публикации агент слияния или агент распространителя не смогут найти файлы моментальных снимков в новом альтернативном местоположении.  
  
> [!NOTE]  
>  Не указывайте альтернативное расположение (в диалоговом окне **Свойства публикации** или в процедуре [sp_changepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)), если оно совпадает с расположением папки моментальных снимков по умолчанию.  
  
> [!CAUTION]  
>  Не используйте одновременно и расположение WebSync, и альтернативное расположение папки моментальных снимков.  
  
 **Указание альтернативных местоположений моментальных снимков**  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: [Изменение расположения папки моментальных снимков (среда SQL Server Management Studio)](publish/specify-an-alternate-snapshot-folder-location-sql-server-management-studio.md) 
  
-   Программирование репликации на [!INCLUDE[tsql](../../includes/tsql-md.md)]: [Настройка свойств моментального снимка &#40;программирование репликации на языке Transact-SQL&#41;](publish/configure-snapshot-properties-replication-transact-sql-programming.md)  
  
## <a name="see-also"></a>См. также  
 [Инициализация подписки с помощью моментального снимка](initialize-a-subscription-with-a-snapshot.md)   
 [Параметры моментального снимка](snapshot-options.md)  
  
  
