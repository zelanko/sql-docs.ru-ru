---
title: sp_changesubscriptiondtsinfo (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changesubscriptiondtsinfo
- sp_changesubscriptiondtsinfo_TSQL
helpviewer_keywords:
- sp_changesubscriptiondtsinfo
ms.assetid: 64fc085f-f81b-493b-b59a-ee6192d9736d
author: stevestein
ms.author: sstein
ms.openlocfilehash: a091df0cbbeb2883ff9905d7c5b3718d50efa86b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68762551"
---
# <a name="sp_changesubscriptiondtsinfo-transact-sql"></a>sp_changesubscriptiondtsinfo (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Изменяет свойства пакета служб DTS для подписки. Эта хранимая процедура выполняется на подписчике в базе данных подписки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_changesubscriptiondtsinfo [ [ @job_id = ] job_id ]  
    [ , [ @dts_package_name= ] 'dts_package_name' ]  
    [ , [ @dts_package_password= ] 'dts_package_password' ]  
    [ , [ @dts_package_location= ] 'dts_package_location' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @job_id = ] job_id`Идентификатор задания агент распространения принудительной подписки. *job_id* имеет тип **varbinary (16)** и не имеет значения по умолчанию. Чтобы найти идентификатор задания распространения, выполните **sp_helpsubscription** или **sp_helppullsubscription**.  
  
`[ @dts_package_name = ] 'dts_package_name'`Указывает имя пакета служб DTS. *dts_package_name* имеет тип **sysname**и значение по умолчанию NULL. Например, чтобы указать пакет с именем **DTSPub_Package**, необходимо указать `@dts_package_name = N'DTSPub_Package'`.  
  
`[ @dts_package_password = ] 'dts_package_password'`Указывает пароль для пакета. Аргумент *dts_package_password* имеет тип **sysname** и значение по умолчанию NULL, которое указывает, что свойство Password должно остаться без изменений.  
  
> [!NOTE]  
>  У пакета служб DTS должен быть пароль.  
  
`[ @dts_package_location = ] 'dts_package_location'`Указывает расположение пакета. *dts_package_location* имеет тип **nvarchar (12)** и значение по умолчанию NULL, которое указывает, что расположение пакета должно остаться без изменений. Расположение пакета можно изменить на **распространитель** или на **подписчик**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_changesubscriptiondtsinfo** используется для репликации моментальных снимков и репликации транзакций, которые являются принудительными подписками.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** , **db_owner** предопределенной роли базы данных или создатель подписки могут выполнять **sp_changesubscriptiondtsinfo**.  
  
## <a name="see-also"></a>См. также:  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
