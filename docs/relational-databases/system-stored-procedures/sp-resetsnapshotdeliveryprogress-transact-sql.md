---
title: sp_resetsnapshotdeliveryprogress (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_resetsnapshotdeliveryprogress
- sp_resetsnapshotdeliveryprogress_TSQL
helpviewer_keywords:
- sp_resetsnapshotdeliveryprogress
ms.assetid: 5df7d86b-d343-4d9b-88b1-74429ed092e6
author: stevestein
ms.author: sstein
ms.openlocfilehash: cc6205eb5487b89db55488bcdf36fbb036595d57
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68129651"
---
# <a name="sp_resetsnapshotdeliveryprogress-transact-sql"></a>sp_resetsnapshotdeliveryprogress (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает в исходное состояние процесс доставки моментального снимка для подписки по запросу, чтобы доставку моментального снимка можно было начать заново. Выполняется на подписчике в базе данных подписки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_resetsnapshotdeliveryprogress [ [ @verbose_level = ] verbose_level ]  
    [ , [ @drop_table = ] 'drop_table' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @verbose_level = ] verbose_level`Указывает объем возвращаемых сведений. *verbose_level*имеет **тип int**и значение по умолчанию **1**. Значение **1** означает, что если необходимые блокировки не удается получить в таблице **MSsnapshotdeliveryprogress** , то возвращается ошибка, а **0** означает, что ошибка не возвращается.  
  
`[ @drop_table = ] 'drop_table'`Указывает, следует ли удалить или усечь таблицу, содержащую сведения о ходе выполнения моментального снимка. *DROP_TABLE* имеет тип **nvarchar (5)** и значение по умолчанию **false**. FALSE означает, что таблица усекается, а TRUE означает, что таблица удаляется.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_resetsnapshotdeliveryprogress** удаляются все строки в таблице **MSsnapshotdeliveryprogress** . Благодаря этому удаляются все метаданные, оставленные в базе данных подписки предыдущим процессом в ходе доставки моментального снимка.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_resetsnapshotdeliveryprogress**.  
  
## <a name="see-also"></a>См. также:  
 [Хранимые процедуры репликации &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
