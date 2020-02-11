---
title: Удаление расширенной хранимой процедуры
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- deleting extended stored procedures
- removing extended stored procedures
- extended stored procedures [SQL Server], removing
- dropping extended stored procedures
ms.assetid: 7827e574-3f59-4279-9a9b-532582e041cb
author: rothja
ms.author: jroth
ms.custom: seo-dt-2019
ms.openlocfilehash: ec61cf630d606977689d3fb3763cce8bd8b705c8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "74095437"
---
# <a name="removing-an-extended-stored-procedure-from-sql-server"></a>Удаление расширенной хранимой процедуры из SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Вместо этого используйте интеграцию со средой CLR.  
  
 Чтобы удалить каждую функцию расширенной хранимой процедуры в определяемой пользователем библиотеке DLL расширенной хранимой процедуры, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] системный администратор должен запустить **sp_dropextendedproc** системную хранимую процедуру, указав имя функции и имя библиотеки DLL, в которой находится эта функция. Например, эта команда удаляет функцию **xp_hello**, расположенную в библиотеке DLL с именем xp_hello. dll, из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
```  
sp_dropextendedproc 'xp_hello'  
```  
  
 Начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], **sp_dropextendedproc** не удаляет Системные расширенные хранимые процедуры. Вместо этого системный администратор должен отклонить разрешение EXECUTE на расширенную хранимую процедуру для роли **Public** .  
  
## <a name="see-also"></a>См. также:  
 [sp_dropextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)  
  
  
