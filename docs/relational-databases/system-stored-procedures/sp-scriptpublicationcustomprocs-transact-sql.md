---
description: sp_scriptpublicationcustomprocs (Transact-SQL)
title: sp_scriptpublicationcustomprocs (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_scriptpublicationcustomprocs
- sp_scriptpublicationcustomprocs_TSQL
helpviewer_keywords:
- sp_scriptpublicationcustomprocs
ms.assetid: b06102d5-4284-4834-b126-bc0baea49be5
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d31a6f58b62d242fd6fe056eaac198fb0a7b7738
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88481066"
---
# <a name="sp_scriptpublicationcustomprocs-transact-sql"></a>sp_scriptpublicationcustomprocs (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Записывает в скрипт пользовательские процедуры INSERT, UPDATE и DELETE для всех статей таблиц из публикации, в которой включен параметр автоматического создания схемы пользовательской процедуры. **sp_scriptpublicationcustomprocs** особенно удобно использовать для настройки подписок, для которых моментальный снимок применяется вручную.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_scriptpublicationcustomprocs [ @publication = ] 'publication_name'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication_name'` Имя публикации. *publication_name* имеет тип **sysname** и не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Возвращает результирующий набор, состоящий из одного столбца **nvarchar (4000)** . Результирующий набор формирует полную инструкцию CREATE PROCEDURE, необходимую для создания пользовательской хранимой процедуры.  
  
## <a name="remarks"></a>Комментарии  
 Пользовательские процедуры не вносятся в сценарии для статей, для которых не задан параметр автоматического создания схемы пользовательской процедуры (0x2).  
  
 Следующие процедуры используются **sp_scriptpublicationcustomprocs** для создания процедур подписчика и не должны выполняться напрямую:  
  
 **sp_script_reconciliation_delproc;**  
  
 **sp_script_reconciliation_insproc;**  
  
 **sp_script_reconciliation_vdelproc;**  
  
 **sp_script_reconciliation_xdelproc;**  
  
 **sp_scriptdelproc;**  
  
 **sp_scriptinsproc;**  
  
 **sp_scriptmappedupdproc;**  
  
 **sp_scriptupdproc;**  
  
 **sp_scriptvdelproc;**  
  
 **sp_scriptvupdproc;**  
  
 **sp_scriptxdelproc;**  
  
 **sp_scriptxupdproc.**  
  
## <a name="permissions"></a>Разрешения  
 Разрешение EXECUTE предоставляется **Public**; в этой хранимой процедуре выполняется процедура проверки безопасности для ограничения доступа к членам предопределенной роли сервера **sysadmin** и **db_owner** предопределенной роли базы данных в текущей базе данных.  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
