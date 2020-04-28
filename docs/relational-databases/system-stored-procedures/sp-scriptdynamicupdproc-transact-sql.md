---
title: sp_scriptdynamicupdproc (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_scriptdynamicupdproc_TSQL
- sp_scriptdynamicupdproc
helpviewer_keywords:
- sp_scriptdynamicupdproc
ms.assetid: b4c18863-ed92-4aa2-a04f-7ed832fc9e07
author: stevestein
ms.author: sstein
ms.openlocfilehash: 67ba388871720ff804063f27a378b838d300baf0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68126392"
---
# <a name="sp_scriptdynamicupdproc-transact-sql"></a>sp_scriptdynamicupdproc (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Формирует инструкцию CREATE PROCEDURE, создающую хранимую процедуру динамического обновления. Инструкция UPDATE создается в пользовательской хранимой процедуре динамически на основе синтаксиса MCALL, при котором указываются изменяемые столбцы. Следует использовать эту хранимую процедуру, если число индексов в таблице подписки увеличивается, а число изменяемых столбцов невелико. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_scriptdynamicupdproc [ @artid =] artid  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @artid = ] artid`Идентификатор статьи. *artid* имеет **тип int**и не имеет значения по умолчанию.  
  
## <a name="result-sets"></a>Результирующие наборы  
 Возвращает результирующий набор, состоящий из одного столбца **nvarchar (4000)** . Результирующий набор формирует полную инструкцию CREATE PROCEDURE, служащую для создания пользовательской хранимой процедуры.  
  
## <a name="remarks"></a>Remarks  
 **sp_scriptdynamicupdproc** используется в репликации транзакций. По умолчанию, при синтаксисе MCALL в сценарий включаются все столбцы, входящие в инструкцию UPDATE, а для определения измененных столбцов используется битовая карта. Если столбец не изменился, ему присваиваются его же значения, что обычно не приводит ни к каким проблемам. Если столбец является индексированным, выполняются дополнительные операции. При таком динамическом подходе принимаются во внимание только измененные столбцы, в результате чего формируется оптимальная инструкция UPDATE. Однако составление динамической инструкции UPDATE требует дополнительной обработки в период выполнения. Рекомендуется протестировать динамический и статический подходы и выбрать оптимальное решение.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_scriptdynamicupdproc**.  
  
## <a name="examples"></a>Примеры  
 В этом примере создается статья (с параметром *artid* , равным **1**) в таблице **authors** в базе данных **pubs** и указывается, что инструкция UPDATE является настраиваемой процедурой для выполнения:  
  
```  
'MCALL sp_mupd_authors'  
```  
  
 Для формирования пользовательской хранимой процедуры, которая будет выполняться агентом распространителя на подписчике, на издателе необходимо выполнить следующую хранимую процедуру:  
  
```  
EXEC sp_scriptdynamicupdproc @artid = '1'  
  
The statement returns:  
  
CREATE PROCEDURE [sp_mupd_authors]   
  @c1 varchar(11),@c2 varchar(40),@c3 varchar(20),@c4 char(12),@c5 varchar(40),@c6 varchar(20),  
  @c7 char(2),@c8 char(5),@c9 bit,@pkc1 varchar(11),@bitmap binary(2)  
as  
  
declare @stmt nvarchar(4000), @spacer nvarchar(1)  
SELECT @spacer =N''  
SELECT @stmt = N'UPDATE [authors] SET '  
  
if substring(@bitmap,1,1) & 2 = 2  
begin  
  select @stmt = @stmt + @spacer + N'[au_lname]' + N'=@2'  
  select @spacer = N','  
end  
if substring(@bitmap,1,1) & 4 = 4  
begin  
  select @stmt = @stmt + @spacer + N'[au_fname]' + N'=@3'  
  select @spacer = N','  
end  
if substring(@bitmap,1,1) & 8 = 8  
begin  
  select @stmt = @stmt + @spacer + N'[phone]' + N'=@4'  
  select @spacer = N','  
end  
if substring(@bitmap,1,1) & 16 = 16  
begin  
  select @stmt = @stmt + @spacer + N'[address]' + N'=@5'  
  select @spacer = N','  
end  
if substring(@bitmap,1,1) & 32 = 32  
begin  
  select @stmt = @stmt + @spacer + N'[city]' + N'=@6'  
  select @spacer = N','  
end  
if substring(@bitmap,1,1) & 64 = 64  
begin  
  select @stmt = @stmt + @spacer + N'[state]' + N'=@7'  
  select @spacer = N','  
end  
if substring(@bitmap,1,1) & 128 = 128  
begin  
  select @stmt = @stmt + @spacer + N'[zip]' + N'=@8'  
  select @spacer = N','  
end  
if substring(@bitmap,2,1) & 1 = 1  
begin  
  select @stmt = @stmt + @spacer + N'[contract]' + N'=@9'  
  select @spacer = N','  
end  
select @stmt = @stmt + N' where [au_id] = @1'  
exec sp_executesql @stmt, N' @1 varchar(11),@2 varchar(40),@3 varchar(20),@4 char(12),@5 varchar(40),  
                             @6 varchar(20),@7 char(2),@8 char(5),@9 bit',@pkc1,@c2,@c3,@c4,@c5,@c6,@c7,@c8,@c9  
  
if @@rowcount = 0  
   if @@microsoftversion>0x07320000  
      exec sp_MSreplraiserror 20598  
```  
  
 После выполнения этой хранимой процедуры можно использовать получившийся в итоге скрипт для создания хранимой процедуры вручную на подписчиках.  
  
## <a name="see-also"></a>См. также:  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
