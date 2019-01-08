---
title: sp_changearticlecolumndatatype (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changearticlecolumndatatype
- sp_changearticlecolumndatatype_TSQL
helpviewer_keywords:
- sp_changearticlecolumndatatype
ms.assetid: 0db80e08-fb77-4d0c-aa41-455b13ffa9b4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e93025676d451444140fad80a993813c0463a2f6
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2018
ms.locfileid: "53206763"
---
# <a name="spchangearticlecolumndatatype-transact-sql"></a>sp_changearticlecolumndatatype (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Меняет сопоставление типа данных столбца статьи для публикации Oracle. Эта хранимая процедура выполняется на распространителе в любой базе данных.  
  
> [!NOTE]  
>  Сопоставления типов данных между поддерживаемыми типами издателей обеспечиваются по умолчанию. Используйте **sp_changearticlecolumndatatype** только тогда, когда эти параметры по умолчанию.  
  
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
  
 [  **@article =** ] **"***статье***"**  
 Имя статьи. *статья* — **sysname**, не имеет значения по умолчанию.  
  
 [ **@column**=] **"***столбец***"**  
 Имя столбца, для которого изменяется сопоставление типа данных. *столбец* — **sysname**, не имеет значения по умолчанию.  
  
 [ **@type** =] **"***тип***"**  
 Имя [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных в целевом столбце. *Тип* — **sysname**, значение по умолчанию NULL.  
  
 [ **@length** =] *длина*  
 Длина типа данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в целевом столбце. *Длина* — **bigint**, значение по умолчанию NULL.  
  
 [ **@precision**=] *точности*  
 Точность типа данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в целевом столбце. *точность* — **bigint**, значение по умолчанию NULL.  
  
 [ **@publisher**=] **"***издателя***"**  
 Указывает, отличный от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя. *издатель* — **sysname**, значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **Sp_changearticlecolumndatatype** используется для переопределения сопоставления типа данных по умолчанию между поддерживаемыми типами издателей (Oracle и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]). Чтобы просмотреть эти сопоставления типов данных по умолчанию, выполните [sp_getdefaultdatatypemapping](../../relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql.md).  
  
 **sp_changearticlecolumndatatype** поддерживается только для издателей Oracle. Выполнение этой хранимой процедуры для публикации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] завершится ошибкой.  
  
 **sp_changearticlecolumndatatype** необходимо выполнить для каждого сопоставления столбцов статьи, который должен быть изменен.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_changearticlecolumndatatype**.  
  
## <a name="see-also"></a>См. также  
 [Изменение свойств публикации и статьи](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Data Type Mapping for Oracle Publishers](../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
