---
title: Выполнение скриптов во время синхронизации (программирование репликации на языке Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
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
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 08c252c6b78c31a8221dbd969ddb49ba0abc647f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68128167"
---
# <a name="execute-scripts-during-synchronization-replication-transact-sql-programming"></a>Выполнение скриптов во время синхронизации (программирование репликации на языке Transact-SQL)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Выполнение скрипта по требованию на подписчике поддерживается для репликации транзакций и публикации слиянием. Эта функция осуществляет копирование скрипта в рабочий каталог репликации, а затем командой **sqlcmd** применяет скрипт на подписчике. По умолчанию при возникновении ошибки применения скрипта к подписке на публикацию транзакций работа агента распространителя будет остановлена. Программным путем можно задать скрипт [!INCLUDE[tsql](../../includes/tsql-md.md)] , который будет выполняться с помощью хранимых процедур репликации.  
  
### <a name="to-specify-a-script-to-run-for-all-subscribers-to-a-snapshot-transactional-or-merge-publication"></a>Настройка скрипта для выполнения всеми подписчиками на публикацию моментальных снимков, транзакций или слиянием  
  
1.  Создайте и протестируйте скрипт на языке [!INCLUDE[tsql](../../includes/tsql-md.md)] , который будет выполняться по запросу.  
  
2.  Сохраните файл скрипта в папке, доступной для агента моментальных снимков публикации.  
  
3.  В издателе в базе данных публикации выполните процедуру [sp_addscriptexec &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addscriptexec-transact-sql.md). Задайте параметр **@publication** и имя созданного на шаге 2 файла скрипта в полном UNC-формате в параметре **@scriptfile** , а в параметре **@skiperror** укажите одно из следующих значений.  
  
    -   **0** — выполнение скрипта агентом в случае ошибки будет остановлено.  
  
    -   **1** — при возникновении ошибки агент делает запись в журнал и продолжает выполнение скрипта.  
  
4.  Указанный скрипт будет выполнен на всех подписчиках при следующем сеансе синхронизации подписки.  
  
## <a name="see-also"></a>См. также:  
 [Синхронизация данных](../../relational-databases/replication/synchronize-data.md)  
  
  
