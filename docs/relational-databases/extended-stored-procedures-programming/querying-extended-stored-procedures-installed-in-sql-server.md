---
title: Запрос расширенных хранимых процедур
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
ms.custom: seo-dt-2019
ms.openlocfilehash: 875d4f252058d442c91915eb69784507c39b2e94
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "74095947"
---
# <a name="querying-extended-stored-procedures-installed-in-sql-server"></a>Запрос расширенных хранимых процедур, установленных в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Вместо этого используйте интеграцию со средой CLR.  
  
 Прошедший проверку подлинности пользователь может отобразить определенные в данный момент расширенные хранимые процедуры и имя библиотеки DLL, к которой они относятся, выполнив sp_helpextendedproc системной процедуры. **** [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Например, в следующем примере возвращается библиотека DLL, к которой принадлежит **xp_hello** :  
  
```  
sp_helpextendedproc 'xp_hello'  
```  
  
 Если **sp_helpextendedproc** выполняется без указания расширенной хранимой процедуры, отображаются все расширенные хранимые процедуры и их библиотеки DLL.  
  
> [!IMPORTANT]  
>  Сведения будут возвращены только для тех расширенных хранимых процедур, владельцем которых является вошедший в систему пользователь или на которые он имеет разрешение. Только члены предопределенной роли сервера **sysadmin** и **db_owner**, **db_securityadmin**и предопределенных ролей базы данных **db_ddladmin** могут просматривать сведения обо всех расширенных хранимых процедурах.  
  
## <a name="see-also"></a>См. также:  
 [sp_helpextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql.md)   
 [sp_addextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql.md)   
 [sp_dropextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)  
  
  
