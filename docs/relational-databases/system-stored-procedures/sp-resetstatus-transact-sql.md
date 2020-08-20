---
description: sp_resetstatus (Transact-SQL)
title: sp_resetstatus (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_resetstatus
- sp_resetstatus_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_resetstatus
ms.assetid: b892727f-ea3b-4b94-88d9-f2386ad4962c
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 7b933535fb9c1d4cf06fa52be6ccf6dbba61ff2d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88464037"
---
# <a name="sp_resetstatus-transact-sql"></a>sp_resetstatus (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Сбрасывает состояние SUSPECT для базы данных.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Вместо этого используйте [инструкцию ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md) .  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_resetstatus [ @dbname = ] 'database'  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @dbname =] "*база данных*"  
 Имя базы данных, состояние которой сбрасывается. Аргумент *Database* имеет тип **sysname**и не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Remarks  
 Процедура sp_resetstatus сбрасывает флаг SUSPECT в базе данных. Эта процедура обновляет столбцы режима и состояния названной базы данных в представлении каталога sys.databases. Перед выполнением этой процедуры в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимо просмотреть журнал ошибок и устранить все проблемы. После выполнения процедуры sp_resetstatus следует остановить и перезапустить экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 База данных может перейти в состояние SUSPECT по нескольким причинам. Среди вероятных причин — отказ в доступе к ресурсам базы данных операционной системе и недоступность или повреждение одного или нескольких файлов базы данных.  
  
## <a name="permissions"></a>Разрешения  
 Требует членства в предопределенной роли сервера sysadmin.  
  
## <a name="examples"></a>Примеры  
 В следующем примере сбрасывается состояние базы данных `AdventureWorks2012`.  
  
```  
EXEC sp_resetstatus 'AdventureWorks2012';  
```  
  
## <a name="see-also"></a>См. также:  
 [Системные хранимые процедуры &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Ядро СУБД хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)  
  
  
