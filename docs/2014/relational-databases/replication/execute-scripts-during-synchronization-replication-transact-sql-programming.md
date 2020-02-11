---
title: Выполнение скриптов во время синхронизации (программирование репликации на языке Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- synchronization [SQL Server replication], scripts
- scripts [SQL Server replication], synchronization and
- sp_addscriptexec
ms.assetid: b58a0877-4e43-4fab-a281-24e6022d3fb1
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2565eb2be68c1e964b82d46d9aa8fc9f39a01f70
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "74165021"
---
# <a name="execute-scripts-during-synchronization-replication-transact-sql-programming"></a>Выполнение скриптов во время синхронизации (программирование репликации на языке Transact-SQL)
  Выполнение скрипта по требованию на подписчике поддерживается для репликации транзакций и публикации слиянием. Эта функция осуществляет копирование скрипта в рабочий каталог репликации, а затем командой **sqlcmd** применяет скрипт на подписчике. По умолчанию при возникновении ошибки применения скрипта к подписке на публикацию транзакций работа агента распространителя будет остановлена. Программным путем можно задать скрипт [!INCLUDE[tsql](../../includes/tsql-md.md)] , который будет выполняться с помощью хранимых процедур репликации.  
  
### <a name="to-specify-a-script-to-run-for-all-subscribers-to-a-snapshot-transactional-or-merge-publication"></a>Настройка скрипта для выполнения всеми подписчиками на публикацию моментальных снимков, транзакций или слиянием  
  
1.  Создайте и протестируйте скрипт на языке [!INCLUDE[tsql](../../includes/tsql-md.md)] , который будет выполняться по запросу.  
  
2.  Сохраните файл скрипта в папке, доступной для агента моментальных снимков публикации.  
  
3.  В издателе в базе данных публикации выполните процедуру [sp_addscriptexec &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addscriptexec-transact-sql). Укажите ** \@публикацию**, имя файла скрипта с полным UNC-путем, созданным на шаге 2 для ** \@scriptfile**, и одно из следующих значений для ** \@skiperror**:  
  
    -   **0** — агент прекратит выполнение скрипта в случае возникновения ошибки.  
  
    -   **1** — агент будет регистрировать ошибки и продолжать выполнение сценария при возникновении ошибок.  
  
4.  Указанный скрипт будет выполнен на всех подписчиках при следующем сеансе синхронизации подписки.  
  
## <a name="see-also"></a>См. также:  
 [Синхронизация данных](synchronize-data.md)  
  
  
