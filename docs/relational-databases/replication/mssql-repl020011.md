---
title: MSSQL_REPL020011 | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_REPL020011 error
ms.assetid: f72072d7-bbb6-48ad-ac88-afa74aeb4d58
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8e9d2e945a8313e025fdd9ee78d878264ef7369d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68020212"
---
# <a name="mssqlrepl020011"></a>MSSQL_REPL020011
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|20011|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Процессу не удалось выполнить '%1' на '%2'.|  
  
## <a name="explanation"></a>Объяснение  
 Эта ошибка может возникать в ряде случаев во время обработки репликации транзакций, например, когда агент чтения журнала выполняет хранимую процедуру **sp_replcmds** (Процесс не смог выполнить 'sp_replcmds' на \<ServerName>) или **sp_repldone** (Процесс не смог выполнить 'sp_repldone' на \<ServerName>).  
  
## <a name="user-action"></a>Действие пользователя  
 Если эта ошибка возникает в базе данных, которая только что была восстановлена из резервной копии, убедитесь, что были соблюдены инструкции, приведенные в документации по резервному копированию и восстановлению, включая выполнение хранимой процедуры **sp_replrestart** , если она необходима. Дополнительные сведения см. в статье [Стратегии резервного копирования и восстановления из копии репликации моментальных снимков и репликации транзакций](../../relational-databases/replication/administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md).  
  
 Эта ошибка является внутренней ошибкой обработки, и если она возникает в ситуациях, отличных от восстановления, то она обычно указывает на необходимость удаления и перенастройки репликации. Если не удается удалить репликацию, обратитесь за консультацией в службу поддержки пользователей.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и событиям (репликация)](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [sp_replcmds (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)   
 [sp_repldone &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)  
  
  
