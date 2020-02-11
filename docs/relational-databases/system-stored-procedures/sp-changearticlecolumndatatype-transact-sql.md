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
ms.openlocfilehash: f101d9081c7eb898d43c461a3bd64eca0c043b64
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67995513"
---
# <a name="sp_changearticlecolumndatatype-transact-sql"></a>sp_changearticlecolumndatatype (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Меняет сопоставление типа данных столбца статьи для публикации Oracle. Эта хранимая процедура выполняется на распространителе в любой базе данных.  
  
> [!NOTE]  
>  Сопоставления типов данных между поддерживаемыми типами издателей обеспечиваются по умолчанию. Используйте **sp_changearticlecolumndatatype** только при переопределении этих параметров по умолчанию.  
  
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
`[ @publication = ] 'publication'`Имя публикации Oracle. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @article = ] 'article'`Имя статьи. Аргумент *article* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @column = ] 'column'`Имя столбца, для которого необходимо изменить сопоставление типов данных. *столбец* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @type = ] 'type'`Имя [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типа данных в целевом столбце. Аргумент *Type имеет тип* **sysname**и значение по умолчанию NULL.  
  
`[ @length = ] length`Длина типа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] данных в целевом столбце. *length* имеет тип **bigint**и значение по умолчанию NULL.  
  
`[ @precision = ] precision`Точность типа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] данных в целевом столбце. *точность* имеет тип **bigint**и значение по умолчанию NULL.  
  
`[ @publisher = ] 'publisher'`Указывает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя, отличного от. Аргумент *Publisher* имеет тип **sysname**и значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **Sp_changearticlecolumndatatype** используется для переопределения сопоставлений типов данных по умолчанию между поддерживаемыми типами издателей [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)](Oracle и). Чтобы просмотреть сопоставления типов данных по умолчанию, выполните [sp_getdefaultdatatypemapping](../../relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql.md).  
  
 **sp_changearticlecolumndatatype** поддерживается только для издателей Oracle. Выполнение этой хранимой процедуры для публикации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] завершится ошибкой.  
  
 **sp_changearticlecolumndatatype** должны выполняться для каждого сопоставления столбцов статьи, которое необходимо изменить.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_changearticlecolumndatatype**.  
  
## <a name="see-also"></a>См. также:  
 [Изменение свойств публикации и статьи](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Сопоставление типов данных для издателей Oracle](../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md)   
 [Хранимые процедуры репликации &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
