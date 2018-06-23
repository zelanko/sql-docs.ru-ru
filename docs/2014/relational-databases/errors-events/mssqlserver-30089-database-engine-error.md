---
title: MSSQLSERVER_30089 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 9992 (Database Engine error)
ms.assetid: 188e5bde-6865-4740-a2b2-582be8f55c77
caps.latest.revision: 16
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 5035b8c20cdb2492004346b87d8a3af9a56ab65c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101090"
---
# <a name="mssqlserver30089"></a>MSSQLSERVER_30089
    
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
  
## <a name="see-also"></a>См. также  
 [sp_help_fulltext_system_components &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql)   
 [Настройка и управление средством разбиения на слова и парадигматические модули для поиска](../search/configure-and-manage-word-breakers-and-stemmers-for-search.md)   
 [Настройка поисковых фильтров и управление ими](../search/configure-and-manage-filters-for-search.md)  
  
  
