---
title: sys. sp_rda_reconcile_batch (Transact-SQL) | Документация Майкрософт
description: Узнайте, как использовать sys. sp_rda_reconcile_batch для согласования идентификатора пакета в таблице SQL Server с поддержкой растяжения с ИДЕНТИФИКАТОРом пакета, хранящимся в удаленной таблице Azure.
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 744d863e22bad3dc84ed1fd46350926228b01607
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89541036"
---
# <a name="syssp_rda_reconcile_batch-transact-sql"></a>sys. sp_rda_reconcile_batch (Transact-SQL)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Согласовывает идентификатор пакета, хранящийся в таблице SQL Server с поддержкой растяжения, с ИДЕНТИФИКАТОРом пакета, хранящимся в удаленной таблице Azure.  
  
 Обычно необходимо запускать **sp_rda_reconcile_batch** только в том случае, если вы вручную удалили последние перенесенные данные из удаленной таблицы. При удалении вручную удаленных данных, содержащих самый последний пакет, идентификаторы пакетов не синхронизированы, и миграция прекращается.  
 
 Чтобы удалить данные, которые уже были перенесены в Azure, ознакомьтесь с примечаниями на этой странице.
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
   
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_rda_reconcile_batch @objname = '@objname'  
  
```  
  
## <a name="arguments"></a>Аргументы  
 \@objname = '* \@ objname*'  
 Имя таблицы SQL Server с поддержкой растяжения.  
  
## <a name="permissions"></a>Разрешения  
 Требуются db_owner разрешения.  
  
## <a name="remarks"></a>Примечания  
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
  
  
