---
title: sp_helpextendedproc (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_helpextendedproc
- sp_helpextendedproc_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpextendedproc
ms.assetid: 7e1f017e-c898-4225-b375-6a73ef9aac7b
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: a7e9cc50f543232dea6b5ce39153eee2292284ac
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38052252"
---
# <a name="sphelpextendedproc-transact-sql"></a>sp_helpextendedproc (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Сообщает сведения о расширенных хранимых процедурах, определенных в настоящий момент, и имя динамически подключаемой библиотеки (DLL), которой принадлежит эта процедура (функция).  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Используйте вместо этого [интеграцию со средой CLR](../../relational-databases/clr-integration/common-language-runtime-integration-overview.md) .  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpextendedproc [ [@funcname = ] 'procedure' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@funcname =**] **"***процедуры***"**  
 Имя расширенной хранимой процедуры, сведения о которой сообщаются. *процедура* — **sysname**, значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя расширенной хранимой процедуры.|  
|**библиотеки DLL**|**nvarchar(255)**|Имя DLL.|  
  
## <a name="remarks"></a>Примечания  
 Когда *процедуры* указано, **sp_helpextendedproc** сообщает сведения об указанной расширенной хранимой процедуры. Если этот параметр не задан, **sp_helpextendedproc** принадлежит возвращает все расширенные хранимые процедуры, имена и имена библиотек DLL, в котором каждый расширенной хранимой процедуры.  
  
## <a name="permissions"></a>Разрешения  
 Разрешение на выполнение **sp_helpextendedproc** предоставляется **открытый**.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-reporting-help-on-all-extended-stored-procedures"></a>A. Справочные сведения обо всех расширенных хранимых процедурах  
 В следующем примере сообщается обо всех расширенных хранимых процедурах.  
  
```  
USE master;  
GO  
EXEC sp_helpextendedproc;  
GO  
```  
  
### <a name="b-reporting-help-on-a-single-extended-stored-procedure"></a>Б. Справочные сведения об одной расширенной хранимой процедуре  
 В следующем примере сообщается о `xp_cmdshell` расширенной хранимой процедуры.  
  
```  
USE master;  
GO  
EXEC sp_helpextendedproc xp_cmdshell;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_addextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql.md)   
 [sp_dropextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
