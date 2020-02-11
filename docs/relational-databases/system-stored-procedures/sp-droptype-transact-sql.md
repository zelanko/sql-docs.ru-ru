---
title: sp_droptype (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_droptype_TSQL
- sp_droptype
dev_langs:
- TSQL
helpviewer_keywords:
- sp_droptype
ms.assetid: e78464ac-2370-4c4e-9cc0-06aebc07cec5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 13ef625d778fe20aa5d33b2958c90aa8cd5a2a8e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68088479"
---
# <a name="sp_droptype-transact-sql"></a>sp_droptype (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Удаляет псевдоним типа данных из **systypes**.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_droptype [ @typename = ] 'type'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @typename = ] 'type'`Имя псевдонима типа данных, которому вы владеете. Аргумент *Type имеет тип* **sysname**и не имеет значения по умолчанию.  
  
## <a name="return-code-type"></a>Тип кода возврата  
 0 (успех) или 1 (сбой).  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 Тип данных псевдонима **типа** не может быть удален, если на него ссылаются таблицы или другие объекты базы данных.  
  
> [!NOTE]  
>  Псевдоним типа данных нельзя удалить, если он используется в определении таблицы или с ним связано правило или значение по умолчанию.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в предопределенной роли базы данных **db_owner** или **db_ddladmin** предопределенной роли базы данных.  
  
## <a name="examples"></a>Примеры  
 В следующем примере удаляется псевдоним типа данных `birthday`.  
  
> [!NOTE]  
>  Такой псевдоним типа данных должен существовать, иначе будет возвращено сообщение об ошибке.  
  
```  
USE master;  
GO  
EXEC sp_droptype 'birthday';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Ядро СУБД хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_addtype &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addtype-transact-sql.md)   
 [sp_rename &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
