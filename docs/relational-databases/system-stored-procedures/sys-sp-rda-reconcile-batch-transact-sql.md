---
title: sys. sp_rda_reconcile_batch (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_reconcile_batch
- sys.sp_rda_reconcile_batch_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_reconcile_batch stored procedure
ms.assetid: 6d21eac3-7b6c-4fe0-8bc4-bf503f3948a6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 98094273d37bf0622eb903b9ad177817e4bb12d1
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "67905089"
---
# <a name="syssp_rda_reconcile_batch-transact-sql"></a>sys. sp_rda_reconcile_batch (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Согласовывает идентификатор пакета, хранящийся в таблице SQL Server с поддержкой растяжения, с ИДЕНТИФИКАТОРом пакета, хранящимся в удаленной таблице Azure.  
  
 Обычно необходимо запускать **sp_rda_reconcile_batch** только в том случае, если вы вручную удалили последние перенесенные данные из удаленной таблицы. При удалении вручную удаленных данных, содержащих самый последний пакет, идентификаторы пакетов не синхронизированы, и миграция прекращается.  
 
 Чтобы удалить данные, которые уже были перенесены в Azure, ознакомьтесь с примечаниями на этой странице.
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
   
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_rda_reconcile_batch @objname = '@objname'  
  
```  
  
## <a name="arguments"></a>Аргументы  
 \@objname = '*\@objname*'  
 Имя таблицы SQL Server с поддержкой растяжения.  
  
## <a name="permissions"></a>Разрешения  
 Требуются db_owner разрешения.  
  
## <a name="remarks"></a>Remarks  
 Если вы хотите удалить данные, которые уже были перенесены в Azure, выполните следующие действия.  
  
1.  Приостановка переноса данных. Дополнительные сведения см. в разделе [Приостановка и возобновление переноса данных (Stretch Database)](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md).  
  
2.  Удалите данные из промежуточной таблицы SQL Server, выполнив команду DELETE с указанием STAGE_ONLY. Дополнительные сведения см. в разделе [внесение административных обновлений и удалений](../../sql-server/stretch-database/manage-and-troubleshoot-stretch-database.md#adminHints).
  
3.  Удалите те же данные из удаленной таблицы Azure, выполнив команду DELETE с указанием REMOTE_ONLY.  
  
4.  Запустите **sp_rda_reconcile_batch**.  
  
5.  Возобновление переноса данных. Дополнительные сведения см. в разделе [Приостановка и возобновление переноса данных (Stretch Database)](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md).  
  
## <a name="example"></a>Пример  
 Чтобы согласовать идентификаторы пакетов, выполните следующую инструкцию.  
  
```sql  
EXEC sp_rda_reconcile_batch @objname = N'StretchEnabledTableName';  
```  
  
  
