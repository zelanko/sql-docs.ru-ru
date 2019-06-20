---
title: MSSQL_REPL020011 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_REPL020011 error
ms.assetid: f72072d7-bbb6-48ad-ac88-afa74aeb4d58
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 481e0b383fd877ec81385bcd4ca4ee37106bb298
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63022770"
---
# <a name="mssqlrepl020011"></a>MSSQL_REPL020011
    
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
 Если эта ошибка возникает в базе данных, которая только что была восстановлена из резервной копии, убедитесь, что были соблюдены инструкции, приведенные в документации по резервному копированию и восстановлению, включая выполнение хранимой процедуры **sp_replrestart** , если она необходима. Дополнительные сведения см. в статье [Стратегии резервного копирования и восстановления из копии репликации моментальных снимков и репликации транзакций](administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md).  
  
 Эта ошибка является внутренней ошибкой обработки, и если она возникает в ситуациях, отличных от восстановления, то она обычно указывает на необходимость удаления и перенастройки репликации. Если не удается удалить репликацию, обратитесь за консультацией в службу поддержки пользователей.  
  
## <a name="see-also"></a>См. также  
 [Справочник по ошибкам и событиям (репликация)](errors-and-events-reference-replication.md)   
 [sp_replcmds (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql)   
 [sp_repldone &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-repldone-transact-sql)  
  
  
