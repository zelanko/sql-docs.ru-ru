---
title: sp_changearticlecolumndatatype (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_changearticlecolumndatatype
- sp_changearticlecolumndatatype_TSQL
helpviewer_keywords:
- sp_changearticlecolumndatatype
ms.assetid: 0db80e08-fb77-4d0c-aa41-455b13ffa9b4
caps.latest.revision: 30
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 08ed5f6f79b78dcb251ebd632f0cf6c70ffec1ee
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="spchangearticlecolumndatatype-transact-sql"></a>sp_changearticlecolumndatatype (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Меняет сопоставление типа данных столбца статьи для публикации Oracle. Эта хранимая процедура выполняется на распространителе в любой базе данных.  
  
> [!NOTE]  
>  Сопоставления типов данных между поддерживаемыми типами издателей обеспечиваются по умолчанию. Используйте **sp_changearticlecolumndatatype** только в том случае, если переопределение параметров по умолчанию.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_changearticlecolumndatatype [ @publication= ] 'publication'  
    [ @article = ] 'article'   
    [ @column = ] 'column'  
    [ , [ @type = ] 'type' ]  
    [ , [ @length = ] length ]  
    [ , [ @precision = ] precision ]  
    [ , [ @scale = ] scale ]  
    [ , [ @publisher = ] 'publisher'  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publication=** ] **"***публикации***"**  
 Имя публикации Oracle. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@article =** ] **"***статьи***"**  
 Имя статьи. *статья* — **sysname**, не имеет значения по умолчанию.  
  
 [ **@column**=] **"***столбца***"**  
 Имя столбца, для которого изменяется сопоставление типа данных. *столбец* — **sysname**, не имеет значения по умолчанию.  
  
 [ **@type** =] **"***типа***"**  
 Имя [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных в целевом столбце. *Тип* — **sysname**, значение по умолчанию NULL.  
  
 [ **@length** =] *длина*  
 Длина типа данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в целевом столбце. *Длина* — **bigint**, значение по умолчанию NULL.  
  
 [ **@precision**=] *точности*  
 Точность типа данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в целевом столбце. *точность* — **bigint**, значение по умолчанию NULL.  
  
 [ **@publisher**=] **"***издатель***"**  
 Задает издателя, отличного от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *издатель* — **sysname**, значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **Sp_changearticlecolumndatatype** используется для переопределения сопоставлений типов данных между поддерживаемыми типами издателей (Oracle и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]). Чтобы просмотреть эти сопоставления типов данных по умолчанию, необходимо выполнить [sp_getdefaultdatatypemapping](../../relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql.md).  
  
 **sp_changearticlecolumndatatype** поддерживается только для издателей Oracle. Выполнение этой хранимой процедуры для публикации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] завершится ошибкой.  
  
 **sp_changearticlecolumndatatype** должна выполняться для каждого сопоставления столбцов статьи, который необходимо изменить.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять **sp_changearticlecolumndatatype**.  
  
## <a name="see-also"></a>См. также  
 [Изменение свойств публикации и статьи](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Data Type Mapping for Oracle Publishers](../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
