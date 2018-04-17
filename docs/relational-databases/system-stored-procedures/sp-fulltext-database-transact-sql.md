---
title: sp_fulltext_database (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_fulltext_database_TSQL
- sp_fulltext_database
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fulltext_database
ms.assetid: eeb1e151-eb00-484c-8fd1-5641e621ffc6
caps.latest.revision: 45
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 868dd07e13c60303622392fc1bf348d59b4a6ab9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="spfulltextdatabase-transact-sql"></a>sp_fulltext_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Не влияет на полнотекстовые каталоги в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях и поддерживается только для обеспечения обратной совместимости. **sp_fulltext_database** не отключает средство полнотекстового поиска для конкретной базы данных. В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] полнотекстовое индексирование всегда включено для всех баз данных, созданных пользователем.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Используйте [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] вместо него.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_fulltext_database [@action=] 'action'  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@action=**] **"***действия***"**  
 Действие, которое должно быть выполнено. **Действие** — **varchar(20)**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Включить**|Поддерживается только для обеспечения обратной совместимости. Не действует на полнотекстовые каталоги в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях.|  
|**Отключить**|Поддерживается только для обеспечения обратной совместимости. Не действует на полнотекстовые каталоги в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="remarks"></a>Замечания  
 В [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях полнотекстовое индексирование отключить нельзя. Отключение полнотекстового индексирования не удаляет строки из **sysfulltextcatalogs** и не означает, что таблицы с включенным полнотекстового больше таковыми не помечены для полнотекстового индексирования. Все определения полнотекстовых метаданных продолжают храниться в системных таблицах.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера и **db_owner** предопределенной роли базы данных могут выполнять **sp_fulltext_database**.  
  
## <a name="see-also"></a>См. также  
 [DATABASEPROPERTYEX (Transact-SQL)](../../t-sql/functions/databasepropertyex-transact-sql.md)   
 [FULLTEXTSERVICEPROPERTY (Transact-SQL)](../../t-sql/functions/fulltextserviceproperty-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
