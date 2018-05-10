---
title: MSSQLSERVER_2546 | Документация Майкрософт
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
- 2546 (Database Engine error)
ms.assetid: c8f0e1b4-c7c4-45f2-9221-746714172313
caps.latest.revision: 20
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: aa504a0068e444ca0c423791000582bee782fb40
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver2546"></a>MSSQLSERVER_2546
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|2546|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC_INDEX_MARKED_DISABLED|  
|Текст сообщения|Индекс «INDEX_NAME» для таблицы «OBJECT_NAME» помечен как отключенный. Перестройте индекс и переведите его в режим «в сети».|  
  
## <a name="explanation"></a>Объяснение  
Указанный индекс помечен как находящийся в режиме «вне сети» или как отключенный. Таким образом, данный индекс не может быть проверен.  
  
## <a name="user-action"></a>Действие пользователя  
Перестройте индекс с помощью оператора ALTER INDEX.  
  
## <a name="see-also"></a>См. также:  
[ALTER INDEX &#40;Transact-SQL&#41;](~/t-sql/statements/alter-index-transact-sql.md)  
[Реорганизация и перестроение индексов](~/relational-databases/indexes/reorganize-and-rebuild-indexes.md)  
  
