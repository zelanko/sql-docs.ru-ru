---
title: "Запрос расширенных хранимых процедур, установленных в SQL Server | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: extended-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: extended stored procedures [SQL Server], querying
ms.assetid: e02348e6-dba6-438a-98b6-684244bb034d
caps.latest.revision: "31"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a91d959f1c9ba80202745910b66ad67ae3aa06d1
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="querying-extended-stored-procedures-installed-in-sql-server"></a>Запрос расширенных хранимых процедур, установленных в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Используйте вместо этого интеграцию со средой CLR.  
  
 Объект [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] прошедший проверку пользователь может отображать определенные в данный момент расширенные хранимые процедуры и имя библиотеки DLL, для которых они принадлежит, выполнив **sp_helpextendedproc** системной процедуры. Например, следующий пример возвращает DLL, для которого **xp_hello** принадлежит:  
  
```  
sp_helpextendedproc 'xp_hello'  
```  
  
 Если **sp_helpextendedproc** выполняется без указания отображаются расширенные хранимые процедуры, расширенные хранимые процедуры и их DLL-библиотеки.  
  
> [!IMPORTANT]  
>  Сведения будут возвращены только для тех расширенных хранимых процедур, владельцем которых является вошедший в систему пользователь или на которые он имеет разрешение. Только члены **sysadmin** предопределенной роли сервера и **db_owner**, **db_securityadmin**и **db_ddladmin** базы данных роли можно просмотреть сведения для всех расширенных хранимых процедур.  
  
## <a name="see-also"></a>См. также:  
 [sp_helpextendedproc &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql.md)   
 [sp_addextendedproc &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql.md)   
 [sp_dropextendedproc &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)  
  
  
