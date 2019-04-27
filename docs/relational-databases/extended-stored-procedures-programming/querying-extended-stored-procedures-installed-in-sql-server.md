---
title: Запрос расширенных хранимых процедур, установленных в SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], querying
ms.assetid: e02348e6-dba6-438a-98b6-684244bb034d
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: f2d5584d70b32764fd9c7e11a53131626e9df444
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62742230"
---
# <a name="querying-extended-stored-procedures-installed-in-sql-server"></a>Запрос расширенных хранимых процедур, установленных в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Используйте вместо этого интеграцию со средой CLR.  
  
 Объект [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] прошедшего проверку подлинности пользователь может отобразить в настоящее время определены расширенные хранимые процедуры и имя библиотеки DLL, которым принадлежит, выполнив **sp_helpextendedproc** системной процедуры. Например, в следующем примере возвращается библиотеки DLL, к которому **xp_hello** принадлежит:  
  
```  
sp_helpextendedproc 'xp_hello'  
```  
  
 Если **sp_helpextendedproc** выполняется без указания расширенной хранимой процедуры, расширенные хранимые процедуры и их DLL-библиотеки.  
  
> [!IMPORTANT]  
>  Сведения будут возвращены только для тех расширенных хранимых процедур, владельцем которых является вошедший в систему пользователь или на которые он имеет разрешение. Только члены **sysadmin** предопределенной роли сервера и **db_owner**, **db_securityadmin**и **db_ddladmin** базы данных роли можно просмотреть сведения для всех расширенных хранимых процедур.  
  
## <a name="see-also"></a>См. также  
 [sp_helpextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql.md)   
 [sp_addextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql.md)   
 [sp_dropextendedproc (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)  
  
  
