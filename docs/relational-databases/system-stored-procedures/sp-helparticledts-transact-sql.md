---
title: sp_helparticledts (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helparticledts
- sp_helparticledts_TSQL
helpviewer_keywords:
- sp_helparticledts
ms.assetid: cd1aed60-e056-4ff3-86ee-62b19433d890
author: stevestein
ms.author: sstein
ms.openlocfilehash: a9c489a08291aea3d1c50a6418dc8e1e853dce12
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68771072"
---
# <a name="sp_helparticledts-transact-sql"></a>sp_helparticledts (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Используется для получения сведений о правильных именах пользовательских задач, используемых при создании подписки преобразования при помощи [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helparticledts [ @publication = ] 'publication', [ @article = ] 'article'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'`Имя публикации. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @article = ] 'article'`Имя статьи в публикации. Аргумент *article* имеет тип **sysname**и не имеет значения по умолчанию.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**pre_script_ignore_error_task_name**|**имеет sysname**|Имя программной задачи, выполняемой перед копированием данных моментального снимка. При возникновении ошибки скрипта выполнение программы должно продолжаться.|  
|**pre_script_task_name**|**имеет sysname**|Имя программной задачи, выполняемой перед копированием данных моментального снимка. При возникновении ошибки выполнение программы прекращается.|  
|**transformation_task_name**|**имеет sysname**|Имя программной задачи при использовании задачи запроса, управляемого данными.|  
|**post_script_ignore_error_task_name**|**имеет sysname**|Имя программной задачи, выполняемой после копирования данных моментального снимка. При возникновении ошибки скрипта выполнение программы должно продолжаться.|  
|**post_script_task_name**|**имеет sysname**|Имя программной задачи, выполняемой после копирования данных моментального снимка. При возникновении ошибки выполнение программы прекращается.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_helparticledts** используется в репликации моментальных снимков и репликации транзакций.  
  
 При именовании задач в программе репликации служб DTS должны соблюдаться соглашения по именованию, необходимые агентам репликации. Для пользовательских задач, таких как задача «Выполнение SQL», именем является объединенная строка, состоящая из имени статьи, префикса и необязательной части. При написании кода, если нет уверенности в верности имен задач, результирующий набор дает имена задач, которые должны использоваться.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** и **db_owner** предопределенной роли базы данных могут выполнять **sp_helparticledts**.  
  
  
