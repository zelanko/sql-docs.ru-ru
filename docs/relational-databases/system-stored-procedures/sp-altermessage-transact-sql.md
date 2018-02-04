---
title: "sp_altermessage (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_altermessage_TSQL
- sp_altermessage
dev_langs:
- TSQL
helpviewer_keywords:
- sp_altermessage
ms.assetid: 1b28f280-8ef9-48e9-bd99-ec14d79abaca
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0922bc2c5365b31c1f4b385e43b10302f6465c52
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="spaltermessage-transact-sql"></a>sp_altermessage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет состояние определяемых пользователем или системных сообщений в экземпляре [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Пользовательские сообщения можно просмотреть с помощью **sys.messages** представления каталога.  

  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_altermessage [ @message_id = ] message_number   ,[ @parameter = ]'write_to_log'  
   ,[ @parameter_value = ]'value'   
```  
  
## <a name="arguments"></a>Аргументы  
 [**@message_id =** ] *message_number*  
 Номер ошибки сообщения из **sys.messages**. *Аргумент message_number* — **int** без значения по умолчанию.  
  
 [ **@parameter =** ] **'***write_to_log*'  
 Используется с  **@parameter_value**  указывает, что сообщение для записи [!INCLUDE[msCoName](../../includes/msconame-md.md)] в журнале приложений Windows. *write_to_log* — **sysname** без значения по умолчанию. *write_to_log* необходимо присвоить значение WITH_LOG или значение NULL. Если *write_to_log* равен WITH_LOG или значение NULL и значение для  **@parameter_value**  — **true**, сообщение записывается в журнал приложений Windows. Если *write_to_log* равен WITH_LOG или значение NULL, а значение для  **@parameter_value**  — **false**, сообщение не всегда записывается в журнал приложений Windows, но может быть запись в зависимости от того, как была вызвана ошибка. Если *write_to_log* указано, значение для  **@parameter_value**  также должен быть указан.  
  
> [!NOTE]  
>  Если сообщение заносится в журнал приложений Windows, оно также заносится и в журнал ошибок компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 [ **@parameter_value =** ]**'***value*'  
 Используется с  **@parameter**  для указания, что ошибка записывается на [!INCLUDE[msCoName](../../includes/msconame-md.md)] в журнале приложений Windows. *значение* — **varchar(5)**, и не имеет значения по умолчанию. Если **true**, ошибка всегда записывается в журнал приложений Windows. Если **false**, ошибка не всегда записывается в журнал приложений Windows, но может записываться в зависимости от того, как была вызвана ошибка. Если *значение* указано, *write_to_log* для  **@parameter**  также должен быть указан.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="remarks"></a>Remarks  
 Влияние **sp_altermessage** с WITH_LOG похоже на параметра инструкции RAISERROR WITH LOG, за исключением того, что **sp_altermessage** изменяет поведение в журнале существующего сообщения. Если сообщение изменено с параметром WITH_LOG, это сообщение всегда записывается в журнал приложений Windows, независимо от того, как была вызвана ошибка. Даже если инструкция RAISERROR выполняется без параметра WITH_LOG, ошибка записывается в журнал приложений Windows.  
  
 Системные сообщения может быть изменена с помощью **sp_altermessage**.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в **serveradmin** предопределенной роли сервера.  
  
## <a name="examples"></a>Примеры  
 В следующем примере существующее сообщение `55001` записывается в журнал приложений Windows.  
  
```  
EXECUTE sp_altermessage 55001, 'WITH_LOG', 'true';  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [RAISERROR (Transact-SQL)](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [sp_addmessage &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addmessage-transact-sql.md)   
 [sp_dropmessage &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dropmessage-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
