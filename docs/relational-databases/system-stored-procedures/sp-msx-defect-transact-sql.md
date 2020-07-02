---
title: sp_msx_defect (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_msx_defect
- sp_msx_defect_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_msx_defect
ms.assetid: 0dfd963a-3bc5-4b58-94f7-aec976da2883
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 102698d7efffa753510f3e3b9af6fe40e35408fc
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85715157"
---
# <a name="sp_msx_defect-transact-sql"></a>sp_msx_defect (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Удаляет текущий сервер из многосерверных операций.  
  
> [!CAUTION]  
>  **sp_msx_defect** редактирует реестр. Редактировать реестр вручную не рекомендуется, так как неуместные или неверные изменения могут серьезно нарушить конфигурацию системы. Пользоваться программой редактирования реестра должны только опытные пользователи. Дополнительные сведения см. в документации по Microsoft Windows.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_msx_defect [@forced_defection =] forced_defection  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @forced_defection = ] forced_defection`Указывает, следует ли принудительно вызывать исключение в случае окончательного потери главного SQLServerAgent из-за необратимой поврежденной базы данных **msdb** или отсутствия резервной копии базы данных **msdb** . *forced_defection*имеет **бит**и значение по умолчанию **0**, что означает, что принудительное исключение не должно выполняться. Значение **1** вызывает исключение.  
  
 После принудительного исключения путем выполнения **sp_msx_defect**член предопределенной роли сервера **sysadmin** на главном SQLServerAgent должен выполнить следующую команду, чтобы завершить исключение:  
  
```  
EXECUTE msdb.dbo.sp_delete_targetserver @server_name = 'tsx-server', @post_defection =  0;  
```  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 Когда **sp_msx_defect** правильно завершается, возвращается сообщение.  
  
## <a name="permissions"></a>Разрешения  
 Для выполнения этой хранимой процедуры пользователь должен быть членом предопределенной роли сервера **sysadmin** .  
  
## <a name="see-also"></a>См. также  
 [sp_msx_enlist &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
