---
title: sp_cycle_agent_errorlog (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cycle_agent_errorlog
- sp_cycle_agent_errorlog_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cycle_agent_errorlog
ms.assetid: 8aa96182-60b7-4d7b-b2a7-ccce70378c6e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: dfb1f3ef9dc8bdac81ed7c3a3a490ca91f73ff23
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62507194"
---
# <a name="spcycleagenterrorlog-transact-sql"></a>sp_cycle_agent_errorlog (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Закрывает текущий файл журнала ошибок агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и циклически меняет номера расширений журнала ошибок агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], как при перезапуске системы. Новый журнал ошибок агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] содержит строку, указывающую на создание нового журнала.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_cycle_agent_errorlog  
```  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Примечания  
 Каждый раз [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агент запускается, текущий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] журнала ошибок агента переименовывается в **SQLAgent.1**; **SQLAgent.1** становится **SQLAgent.2**, **SQLAgent.2** становится **SQLAgent.3**, и т. д. **sp_cycle_agent_errorlog** позволяет Зацикливать файлы журналов ошибок без остановки и запуска сервера.  
  
 Эта хранимая процедура должна запускаться из **msdb** базы данных.  
  
## <a name="permissions"></a>Разрешения  
 Разрешения на выполнение **sp_cycle_agent_errorlog** , ограничены членами **sysadmin** предопределенной роли сервера.  
  
## <a name="examples"></a>Примеры  
 На следующем примере показано, как производится циклическое переименование журнала ошибок агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_cycle_agent_errorlog ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_cycle_errorlog &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cycle-errorlog-transact-sql.md)  
  
  
