---
title: "MSSQLSERVER_30089 | Документация Майкрософт"
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
- 9992 (Database Engine error)
ms.assetid: 188e5bde-6865-4740-a2b2-582be8f55c77
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: c42bbbb05ba2cb78628433815effb5ef7ce48132
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver30089"></a>MSSQLSERVER_30089
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|30089|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|IFTS_FDHOST_TERMINATEDABNORMAL|  
|Текст сообщения|Процесс узла управляющей программы полнотекстовой фильтрации (FDHost) завершился аварийно. Причиной этого может быть неустранимая ошибка при полнотекстовом индексировании или обработке запроса, вызванная неверной настройкой или ошибкой в работе лингвистического компонента — средства разбиения по словам, парадигматического модуля или фильтра. Процесс будет перезапущен автоматически.|  
  
## <a name="explanation"></a>Объяснение  
На узле управляющей программы полнотекстовой фильтрации обнаружена какая-то проблема, которая привела к принудительному аварийному останову. Причиной проблемы может оказаться неправильно отформатированный документ, ошибка в фильтре или разделителе слов, а также нарушение в работе управляющей программы фильтрации.  
  
## <a name="user-action"></a>Действие пользователя  
Как правило, работа управляющей программы после подобной ошибки восстанавливается. Если же в процессе выполнения управляющей программы снова и снова происходит неуспешное завершение, необходимо устранение неполадок. Для выявления причин проблемы попробуйте выполнить следующие действия.  
  
1.  Если недавно установлен новый лингвистический компонент, удалите его из системы.  
  
2.  Просмотрите журнал сканирования, чтобы выявить какой-либо из новых документов, для которого не удалось провести полнотекстовую индексацию, и удалите его.  
  
## <a name="see-also"></a>См. также:  
[sp_help_fulltext_system_components (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql.md)  
[Настройка средств разбиения текста на слова и парадигматических модулей и управление ими для поиска](~/relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)  
[Настройка поисковых фильтров и управление ими](~/relational-databases/search/configure-and-manage-filters-for-search.md)  
  

