---
title: sp_dropextendedproc (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 10/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_dropextendedproc
- sp_dropextendedproc_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dropextendedproc
ms.assetid: dd93af2c-1b7d-4e39-af23-2d21d270a381
caps.latest.revision: 36
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 23361e6f28bdb87ab35a39ec68b448a60ad677d0
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38049392"
---
# <a name="spdropextendedproc-transact-sql"></a>sp_dropextendedproc (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет расширенную хранимую процедуру.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Используйте вместо этого [интеграцию со средой CLR](../../relational-databases/clr-integration/common-language-runtime-integration-overview.md) .  
  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sp_dropextendedproc [ @functname = ] 'procedure'   
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@functname =**] **"***процедуры***"**  
 Имя расширенной хранимой процедуры, которую необходимо удалить. *процедура* — **nvarchar(517)**, не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Примечания  
 Выполнение **sp_dropextendedproc** удаляет имя пользовательской расширенной хранимой процедуры из [sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) представления каталога и удаляет запись из [sys.extended_procedures ](../../relational-databases/system-catalog-views/sys-extended-procedures-transact-sql.md) представления каталога. Эта хранимая процедура может быть запущена только в **master** базы данных.  
  
**sp_dropextendedproc** не удаляет Системные расширенные хранимые процедуры. Вместо этого системный администратор должен запретить разрешение EXECUTE на расширенную хранимую процедуру для **открытый** роли.  
  
 **sp_dropextendedproc** не может быть выполнена внутри транзакции.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять процедуру **sp_dropextendedproc**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере удаляется расширенная хранимая процедура `xp_hello`.  
  
> [!NOTE]  
>  Присутствие данной расширенной хранимой процедуры обязательно, в противном случае пример вернет сообщение об ошибке.  
  
```  
USE master;  
GO  
EXEC sp_dropextendedproc 'xp_hello';  
```  
  
## <a name="see-also"></a>См. также  
 [sp_addextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql.md)   
 [sp_helpextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
