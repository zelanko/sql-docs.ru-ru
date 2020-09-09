---
description: sp_cycle_errorlog (Transact-SQL)
title: sp_cycle_errorlog (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cycle_errorlog_TSQL
- sp_cycle_errorlog
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cycle_errorlog
ms.assetid: 61a12cbf-78a3-4052-8604-3b29d07573fd
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 433accd75ac9bf5c5f2e390aa1bcbf0a1c5e0a6e
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89549928"
---
# <a name="sp_cycle_errorlog-transact-sql"></a>sp_cycle_errorlog (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Закрывает текущий файл журнала ошибок и зацикливает номера расширений журнала ошибок, подобно перезапуску сервера. Новый журнал ошибок содержит версию и сведения об авторских правах и строку, в которой сказано, что был создан новый журнал.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_cycle_errorlog  
```  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 При каждом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запуске текущий журнал ошибок переименовывается в **ErrorLog. 1**; **Журнал** ErrorLog. 1 превращается в **ErrorLog. 2**, **ErrorLog. 2** — **ErrorLog. 3**и т. д. **sp_cycle_errorlog** позволяет циклически запускать файлы журнала ошибок без остановки и запуска сервера.  
  
## <a name="permissions"></a>Разрешения  
 Разрешения на выполнение **sp_cycle_errorlog** ограничены членами предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере показан циклический просмотр журнала ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
EXEC sp_cycle_errorlog ;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sp_cycle_agent_errorlog &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cycle-agent-errorlog-transact-sql.md)  
  
  
