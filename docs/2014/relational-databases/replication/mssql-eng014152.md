---
title: MSSQL_ENG014152 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG014152 error
ms.assetid: 4215e2b1-cd30-441f-9671-9afc742adf6e
caps.latest.revision: 10
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: b115ac5bcaee609dd56f3437141171f3b422a638
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36097040"
---
# <a name="mssqleng014152"></a>MSSQL_ENG014152
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|14152|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Репликация-%s: назначено повторное выполнение агента %s. %s|  
  
## <a name="explanation"></a>Объяснение  
 Для указанного агента репликации было запланировано повторное выполнение запрошенной операции. Повторные попытки продолжаются до тех пор, пока не будет достигнуто максимальное число попыток, настроенное для шага задания.  
  
 Причиной повторного выполнения обычно становится одно из следующего.  
  
-   Превышено значение **QueryTimeout** .  
  
-   Превышено значение **LoginTimeout** .  
  
-   Процесс репликации был выбран как жертва взаимоблокировки.  
  
## <a name="user-action"></a>Действие пользователя  
 Если сообщение о повторном выполнении появляется нечасто, никакие пользовательские действия не требуются.  
  
 Используйте процедуру [sp_help_jobstep](/sql/relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql) для проверки текущего значения максимального числа повторений шага **Запустить агент** для указанного агента репликации. Для корректировки допустимого числа повторений шага задания можно использовать параметр **@retry_attempts** хранимой процедуры [sp_update_jobstep](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql) .  
  
 Если сообщение о повторном выполнении появляется часто, способ устранения неполадок зависит от сообщения, вызывающего повтор. Проверьте в журнале агента наличие сообщений, указывающих причину назначения повторного выполнения. В некоторых случаях может потребоваться включить ведение более подробного журнала для агента репликации. Дополнительные сведения о настройке ведения журнала репликации см. в статье базы знаний Майкрософт [312292](http://support.microsoft.com/kb/312292).  
  
## <a name="see-also"></a>См. также  
 [Справочник по ошибкам и событиям (репликация)](errors-and-events-reference-replication.md)  
  
  
