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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 94a5983701bdb7370c389f970d0c75af11a7779c
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82815379"
---
# <a name="sp_procoption-transact-sql"></a>sp_procoption (Transact-SQL)
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
`[ @ProcName = ] 'procedure'`Имя процедуры, для которой задается параметр. *процедура* имеет тип **nvarchar (776)** и не имеет значения по умолчанию.  
  
`[ @OptionName = ] 'option'`Имя устанавливаемого параметра. Единственное значение *параметра* — **Startup**.  
  
`[ @OptionValue = ] 'value'`Указывает, следует ли устанавливать параметр ON (**true** или **On**) или OFF (**false** или **Off**). *значение* имеет тип **varchar (12)** и не имеет значения по умолчанию.  
  
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
  
  
