---
title: sp_bindsession (Transact-SQL) | Документация Майкрософт
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
- sp_bindsession
- sp_bindsession_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_bindsession
ms.assetid: 1436fe21-ad00-4a98-aca1-1451a5e571d2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 86c735cece67642ab6cd42c5e8164df7f7400d8e
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43036997"
---
# <a name="spbindsession-transact-sql"></a>sp_bindsession (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Привязывает или развязывает сеанс к другим сеансам в одном экземпляре компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Привязывание сеансов позволяет двум и более сеансам участвовать в одной транзакции и общих блокировках, пока выполняется ROLLBACK TRANSACTION или COMMIT TRANSACTION.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Используйте режим MARS или распределенные транзакции. Дополнительные сведения см. в статье [Использование множественных активных результирующих наборов &#40;MARS&#41;](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_bindsession { 'bind_token' | NULL }  
```  
  
## <a name="arguments"></a>Аргументы  
 **"** *bind_token* **"**  
 Токен, идентифицирующий транзакцию, первоначально полученную с помощью **sp_getbindtoken** или открытых служб данных **srv_getbindtoken** функции. *bind_token*— **varchar(255)**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Два объединенных сеанса совместно используют только транзакции и блокировки. Каждый сеанс сохраняет свой собственный уровень изоляции, и установка нового уровня изоляции на одном сеансе не затронет уровень изоляции другого сеанса. Каждый сеанс идентифицируется по его учетной записи безопасности и может обращаться только к тем ресурсам базы данных, на которые учетной записи предоставлены разрешения.  
  
 **sp_bindsession** использует токен привязки для привязки двух или более существующих сеансов клиента. Эти сеансы клиента должны быть на одном экземпляре компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)], от которого был получен токен связывания. Сеанс — это клиент, выполняющий команду. Привязанные сеансы баз данных совместно используют пространство транзакций и блокировок.  
  
 Токен связывания, полученный от одного экземпляра компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)], не может использоваться для сеанса клиента, подключенного к другому экземпляру, даже для транзакций DTC. Токен связывания допустим только локально внутри каждого экземпляра и не может совместно использоваться множеством экземпляров. Для привязки сеансов клиента на другом экземпляре [!INCLUDE[ssDE](../../includes/ssde-md.md)], необходимо получить другой токен связывания, выполнив **sp_getbindtoken**.  
  
 **sp_bindsession** будет завершаться ошибкой, если она использует маркер, который не активен.  
  
 Отменить привязку из сеанса с помощью **sp_bindsession** без указания *bind_token* или путем передачи значения NULL в *bind_token*.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере указанный токен привязки привязывается к текущему сеансу.  
  
> [!NOTE]  
>  Токен привязки, показанный в примере был получен путем выполнения **sp_getbindtoken** перед выполнением **sp_bindsession**.  
  
```  
USE master;  
GO  
EXEC sp_bindsession 'BP9---5---->KB?-V'<>1E:H-7U-]ANZ';  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_getbindtoken (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-getbindtoken-transact-sql.md)   
 [srv_getbindtoken &#40;API расширенных хранимых процедур&#41;](../../relational-databases/extended-stored-procedures-reference/srv-getbindtoken-extended-stored-procedure-api.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
