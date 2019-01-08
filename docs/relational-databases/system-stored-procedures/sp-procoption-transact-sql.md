---
title: sp_procoption (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_procoption
- sp_procoption_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_procoption
ms.assetid: 6f0221bd-70b4-4b04-b15d-722235aceb3c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fcde4fd9439862dd88bdb1ff8c9eb40ff85ce0d4
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/18/2018
ms.locfileid: "53590428"
---
# <a name="spprocoption-transact-sql"></a>sp_procoption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Задает или отменяет хранимую процедуру для автоматического запуска. Хранимая процедура настроена на выполнение при каждом запуске экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_procoption [ @ProcName = ] 'procedure'   
    , [ @OptionName = ] 'option'   
    , [ @OptionValue = ] 'value'   
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@ProcName =** ] **"**_процедуры_**"**  
 — Имя процедуры, для которого требуется задать параметр. *процедура* — **nvarchar(776)**, не имеет значения по умолчанию.  
  
 [  **@OptionName =** ] **"**_параметр_**"**  
 Имя устанавливаемого параметра. Единственное значение для *параметр* — **запуска**.  
  
 [  **@OptionValue =** ] **"**_значение_**"**  
 Указывает, следует ли данный аргумент (**true** или **на**) или выключается (**false** или **off**). *значение* — **varchar(12)**, не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или номер ошибки (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Процедуры автозапуска должны находиться в **master** базы данных и не может содержать параметры ввода или ВЫВОДА. Выполнение хранимых процедур начинается после восстановления всех баз данных и регистрации сообщения «Восстановление завершено» во время начального запуска.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере назначается процедура для автоматического выполнения.  
  
```  
EXEC sp_procoption @ProcName = '<procedure name>'   
    , @OptionName = ] 'startup'   
    , @OptionValue = 'on';   
```  
  
 В следующем примере останавливается автоматическое выполнение процедуры.  
  
```  
EXEC sp_procoption @ProcName = '<procedure name>'   
    , @OptionValue = 'off';   
```  
  
## <a name="see-also"></a>См. также  
 [Выполнение хранимой процедуры](../../relational-databases/stored-procedures/execute-a-stored-procedure.md)  
  
  
