---
title: Удаление расширенной хранимой процедуры из SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: bcb58ac180861641803147d1dfea621bd52df9a6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62512029"
---
# <a name="removing-an-extended-stored-procedure-from-sql-server"></a>Удаление расширенной хранимой процедуры из SQL Server
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Вместо этого используйте интеграцию со средой CLR.  
  
 Чтобы удалить каждую функцию расширенной хранимой процедуры в определяемой пользователем библиотеке DLL расширенной хранимой процедуры, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] системный администратор должен запустить **sp_dropextendedproc** системную хранимую процедуру, указав имя функции и имя библиотеки DLL, в которой находится эта функция. Например, эта команда удаляет функцию **xp_hello**, расположенную в библиотеке DLL с именем xp_hello. dll, из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
```  
sp_dropextendedproc 'xp_hello'  
```  
  
 Начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], **sp_dropextendedproc** не удаляет Системные расширенные хранимые процедуры. Вместо этого системный администратор должен отклонить разрешение EXECUTE на расширенную хранимую процедуру для роли **Public** .  
  
## <a name="see-also"></a>См. также:  
 [sp_dropextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql)  
  
  
