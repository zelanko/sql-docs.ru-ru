---
description: sp_procoption (Transact-SQL)
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 155600ed4a41d4ad8ee7f404426bf5eed0d77ba8
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89535053"
---
# <a name="sp_procoption-transact-sql"></a>sp_procoption (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Задает или отменяет хранимую процедуру для автоматического запуска. Хранимая процедура настроена на выполнение при каждом запуске экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_procoption [ @ProcName = ] 'procedure'   
    , [ @OptionName = ] 'option'   
    , [ @OptionValue = ] 'value'   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @ProcName = ] 'procedure'` Имя процедуры, для которой задается параметр. *процедура* имеет тип **nvarchar (776)** и не имеет значения по умолчанию.  
  
`[ @OptionName = ] 'option'` Имя устанавливаемого параметра. Единственное значение *параметра* — **Startup**.  
  
`[ @OptionValue = ] 'value'` Указывает, следует ли устанавливать параметр ON (**true** или **On**) или OFF (**false** или **Off**). *значение* имеет тип **varchar (12)** и не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или номер ошибки (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Процедуры запуска должны быть в базе данных **master** и не могут содержать входные или выходные параметры. Выполнение хранимых процедур начинается после восстановления всех баз данных и регистрации сообщения «Восстановление завершено» во время начального запуска.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере назначается процедура для автоматического выполнения.  
  
```  
EXEC sp_procoption @ProcName = N'<procedure name>'   
    , @OptionName = 'startup'   
    , @OptionValue = 'on';   
```  
  
 В следующем примере останавливается автоматическое выполнение процедуры.  
  
```  
EXEC sp_procoption @ProcName = N'<procedure name>'      
    , @OptionName = 'startup'
    , @OptionValue = 'off';   
```  
  
## <a name="see-also"></a>См. также  
 [Выполнение хранимой процедуры](../../relational-databases/stored-procedures/execute-a-stored-procedure.md)  
  
  
