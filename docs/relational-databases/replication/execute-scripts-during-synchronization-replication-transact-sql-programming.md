---
title: "Выполнение скриптов во время синхронизации (программирование репликации на языке Transact-SQL) | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- TSQL
helpviewer_keywords:
- synchronization [SQL Server replication], scripts
- scripts [SQL Server replication], synchronization and
- sp_addscriptexec
ms.assetid: b58a0877-4e43-4fab-a281-24e6022d3fb1
caps.latest.revision: 34
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: deef18b1b37375e659dd0412dd7b69f10b8a3bdf
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="execute-scripts-during-synchronization-replication-transact-sql-programming"></a>Выполнение скриптов во время синхронизации (программирование репликации на языке Transact-SQL)
  Выполнение скрипта по требованию на подписчике поддерживается для репликации транзакций и публикации слиянием. Эта функция осуществляет копирование скрипта в рабочий каталог репликации, а затем командой **sqlcmd** применяет скрипт на подписчике. По умолчанию при возникновении ошибки применения скрипта к подписке на публикацию транзакций работа агента распространителя будет остановлена. Программным путем можно задать скрипт [!INCLUDE[tsql](../../includes/tsql-md.md)] , который будет выполняться с помощью хранимых процедур репликации.  
  
### <a name="to-specify-a-script-to-run-for-all-subscribers-to-a-snapshot-transactional-or-merge-publication"></a>Настройка скрипта для выполнения всеми подписчиками на публикацию моментальных снимков, транзакций или слиянием  
  
1.  Создайте и протестируйте скрипт на языке [!INCLUDE[tsql](../../includes/tsql-md.md)] , который будет выполняться по запросу.  
  
2.  Сохраните файл скрипта в папке, доступной для агента моментальных снимков публикации.  
  
3.  В издателе в базе данных публикации выполните процедуру [sp_addscriptexec &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addscriptexec-transact-sql.md). Задайте параметр **@publication**и имя созданного на шаге 2 файла скрипта в полном UNC-формате в параметре **@scriptfile**, а в параметре **@skiperror**укажите одно из следующих значений.  
  
    -   **0** — выполнение скрипта агентом в случае ошибки будет остановлено.  
  
    -   **1** — при возникновении ошибки агент делает запись в журнал и продолжает выполнение скрипта.  
  
4.  Указанный скрипт будет выполнен на всех подписчиках при следующем сеансе синхронизации подписки.  
  
## <a name="see-also"></a>См. также:  
 [Синхронизация данных](../../relational-databases/replication/synchronize-data.md)  
  
  

