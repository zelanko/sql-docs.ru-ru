---
title: sp_adddistributor (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_adddistributor
- sp_adddistributor_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_adddistributor
ms.assetid: 35415502-68d0-40f6-993c-180e50004f1e
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: db37da85e4b707970436b926f6e772bd74402311
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52774436"
---
# <a name="spadddistributor-transact-sql"></a>sp_adddistributor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает запись в [sys.sysservers](../../relational-databases/system-compatibility-views/sys-sysservers-transact-sql.md) таблицы (если еще не существует), отмечает запись сервера как распространитель и сохраняет сведения о свойстве. Данная хранимая процедура выполняется на распространителе в базе данных master, чтобы зарегистрировать и пометить сервер как распространитель. В случае с удаленным распространителем хранимая процедура выполняется также и на издателе от базы данных master, чтобы зарегистрировать удаленный распространитель.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_adddistributor [ @distributor= ] 'distributor'   
    [ , [ @heartbeat_interval= ] heartbeat_interval ]   
    [ , [ @password= ] 'password' ]   
    [ , [ @from_scripting= ] from_scripting ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@distributor=**] **"***распространителя***"**  
 Имя сервера распространителя. *распространитель* — **sysname**, не имеет значения по умолчанию. Этот аргумент используется только при настройке удаленного распространителя. Он добавляет записи к свойствам распространителя в **msdb.. MSdistributor** таблицы.  
  
 [  **@heartbeat_interval=**] *heartbeat_interval*  
 Максимальное количество минут, в течение которых агент может выполняться без ведения журнала сообщений о ходе работы. *heartbeat_interval* — **int**, значение по умолчанию 10 минут. Для проверки состояния запущенных агентов репликации создается задание агента SQL Server, выполняемое с заданным интервалом.  
  
 [  **@password=**] **"***пароль***"**]  
 — Это пароль **distributor_admin** имени входа. *пароль* — **sysname**, значение по умолчанию NULL. Если аргумент имеет значение NULL или для него используется пустая строка, то для пароля выбирается случайное значение. Пароль должен быть настроен при добавлении первого удаленного распространителя. **distributor_admin** входа и *пароль* хранятся для записи связанного сервера, используемого для *распространителя* RPC-подключения, включая локальные соединения. Если *распространителя* является локальным, пароль для **distributor_admin** присваивается новое значение. Для издателей с удаленным распространителем, то же значение для *пароль* должен быть указан при выполнении **sp_adddistributor** на издателе и распространителе. [sp_changedistributor_password](../../relational-databases/system-stored-procedures/sp-changedistributor-password-transact-sql.md) можно использовать для изменения пароля распространителя.  
  
> [!IMPORTANT]  
>  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
 [  **@from_scripting=** ] *from_scripting*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_adddistributor** используется в репликации моментальных снимков, репликации транзакций и репликации слиянием.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#AddDistPub](../../relational-databases/replication/codesnippet/tsql/sp-adddistributor-transa_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять процедуру **sp_adddistributor**.  
  
## <a name="see-also"></a>См. также  
 [Настройка публикации и распространения](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [sp_changedistributor_property &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changedistributor-property-transact-sql.md)   
 [sp_dropdistributor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql.md)   
 [sp_helpdistributor (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Настройка распространения](../../relational-databases/replication/configure-distribution.md)  
  
  
