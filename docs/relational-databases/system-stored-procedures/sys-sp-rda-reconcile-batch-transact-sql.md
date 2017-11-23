---
title: "sys.sp_rda_reconcile_batch (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-stretch
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_reconcile_batch
- sys.sp_rda_reconcile_batch_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.sp_rda_reconcile_batch stored procedure
ms.assetid: 6d21eac3-7b6c-4fe0-8bc4-bf503f3948a6
caps.latest.revision: "12"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ba2e281c7f5593425bd67b817e02d81ee29a4742
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="syssprdareconcilebatch-transact-sql"></a>sys.sp_rda_reconcile_batch (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Согласовывает идентификатор пакета, который хранится в таблице с включенным Stretch SQL Server с Идентификатором пакета, хранимые в удаленной таблице Azure.  
  
 Обычно достаточно для запуска **sp_rda_reconcile_batch** Если наиболее недавно перенесенные данные вручную удалены из удаленной таблицы. При удалении вручную удаленных данных, включающий последнего пакета, не синхронизированы, ИД пакета и останавливает миграции.  
 
 Чтобы удалить данные, уже перенесенные в Azure, см. заметки на этой странице.
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
   
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_rda_reconcile_batch @objname = '@objname'  
  
```  
  
## <a name="arguments"></a>Аргументы  
 @objname = '*@objname*'  
 Имя таблицы с включенным Stretch SQL Server.  
  
## <a name="permissions"></a>Permissions  
 Требуются права db_owner.  
  
## <a name="remarks"></a>Замечания  
 Если вы хотите удалить данные, уже перенесенные в Azure, выполните следующие действия.  
  
1.  Приостановить перенос данных. Дополнительные сведения см. в разделе [Приостановка и возобновление переноса данных &#40; База данных Stretch &#41; ](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md).  
  
2.  Удалите данные из промежуточной таблицы SQL Server при выполнении определенной команды DELETE с подсказку STAGE_ONLY. Дополнительные сведения см. в разделе [выполнение административных обновлений и удалений](../../sql-server/stretch-database/manage-and-troubleshoot-stretch-database.md#adminHints).
  
3.  Удаление тех же данных из удаленной таблицы Azure при выполнении определенной команды DELETE с указанием REMOTE_ONLY.  
  
4.  Запустите **sp_rda_reconcile_batch**.  
  
5.  Возобновление переноса данных. Дополнительные сведения см. в разделе [Приостановка и возобновление переноса данных &#40; База данных Stretch &#41; ](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md).  
  
## <a name="example"></a>Пример  
 Чтобы согласовать идентификаторов пакетов, выполните следующую инструкцию.  
  
```tsql  
EXEC sp_rda_reconcile_batch @objname = N'StretchEnabledTableName';  
```  
  
  
