---
title: sp_altermessage (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_altermessage_TSQL
- sp_altermessage
dev_langs:
- TSQL
helpviewer_keywords:
- sp_altermessage
ms.assetid: 1b28f280-8ef9-48e9-bd99-ec14d79abaca
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4949307cdaf2cc712e56525e872381c2af8256fd
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "72304793"
---
# <a name="sp_altermessage-transact-sql"></a>sp_altermessage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет состояние определяемых пользователем или системных сообщений в экземпляре [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Определяемые пользователем сообщения можно просматривать с помощью представления каталога **sys. messages** .  

  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_altermessage [ @message_id = ] message_number   ,[ @parameter = ]'write_to_log'  
   ,[ @parameter_value = ]'value'   
```  
  
## <a name="arguments"></a>Аргументы  
 [**@message_id =** ] *message_number*  
 Номер ошибки сообщения, которое необходимо изменить из **sys. messages**. *message_number* имеет **тип int** и не имеет значения по умолчанию.  
  
`[ @parameter = ] 'write\_to\_log_'`Используется с ** \@parameter_value** , чтобы указать, что сообщение должно быть записано в журнал [!INCLUDE[msCoName](../../includes/msconame-md.md)] приложений Windows. *write_to_log* имеет тип **sysname** и не имеет значения по умолчанию. для *write_to_log* должно быть задано значение WITH_LOG или null. Если параметру *write_to_log* присвоено значение WITH_LOG или null, а для ** \@parameter_value** — **true**, сообщение записывается в журнал приложений Windows. Если параметру *write_to_log* присвоено значение WITH_LOG или null, а для ** \@parameter_value** — **false**, сообщение не всегда записывается в журнал приложений Windows, но может быть записано в зависимости от того, как возникла ошибка. Если указано *write_to_log* , необходимо также указать значение для ** \@parameter_value** .  
  
> [!NOTE]  
>  Если сообщение заносится в журнал приложений Windows, оно также заносится и в журнал ошибок компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
`[ @parameter_value = ]'value_'`Используется с ** \@параметром** , чтобы указать, что ошибка должна быть записана в [!INCLUDE[msCoName](../../includes/msconame-md.md)] журнал приложений Windows. *значение* имеет тип **varchar (5)** и не имеет значения по умолчанию. Если **значение — true**, ошибка всегда записывается в журнал приложений Windows. Если **значение равно false**, то ошибка не всегда записывается в журнал приложений Windows, но может быть записана в зависимости от того, как возникла ошибка. Если указано *значение* , необходимо также указать *write_to_log* для ** \@параметра** .  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 Результат **sp_altermessage** с параметром WITH_LOG аналогичен параметру RAISERROR with log, за исключением того, что **sp_altermessage** изменяет поведение ведения журнала существующего сообщения. Если сообщение изменено с параметром WITH_LOG, это сообщение всегда записывается в журнал приложений Windows, независимо от того, как была вызвана ошибка. Даже если инструкция RAISERROR выполняется без параметра WITH_LOG, ошибка записывается в журнал приложений Windows.  
  
 Системные сообщения можно изменять с помощью **sp_altermessage**.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в предопределенной роли сервера **serveradmin** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере существующее сообщение `55001` записывается в журнал приложений Windows.  
  
```  
EXECUTE sp_altermessage 55001, 'WITH_LOG', 'true';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [RAISERROR (Transact-SQL)](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [sp_addmessage (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addmessage-transact-sql.md)   
 [sp_dropmessage (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dropmessage-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
