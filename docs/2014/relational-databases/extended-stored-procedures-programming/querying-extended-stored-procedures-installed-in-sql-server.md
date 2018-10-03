---
title: Запрос расширенных хранимых процедур, установленных в SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], querying
ms.assetid: e02348e6-dba6-438a-98b6-684244bb034d
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: f8f8616fe8b5a6c06a8492fc713e4e93004d0dad
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48057274"
---
# <a name="querying-extended-stored-procedures-installed-in-sql-server"></a>Запрос расширенных хранимых процедур, установленных в SQL Server
    
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
 [sp_helpextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql)   
 [sp_addextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql)   
 [sp_dropextendedproc (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql)  
  
  
