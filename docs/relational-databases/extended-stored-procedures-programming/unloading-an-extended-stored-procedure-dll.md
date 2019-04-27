---
title: Выгрузка расширенной хранимой процедуры DLL | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], unloading
- unloading extended stored procedures
ms.assetid: 4c75ab14-af54-4965-b376-8d75d385c941
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: d7f05ad92e5e5264801302f2f1e64c76478141d9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62742109"
---
# <a name="unloading-an-extended-stored-procedure-dll"></a>Выгрузка DLL-библиотеки расширенной хранимой процедуры
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Пользуйтесь вместо этого интеграцией со средой CLR.  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] загружает библиотеку DLL расширенной хранимой процедуры, как только выполняется вызов одной из функций библиотеки DLL. DLL-библиотека остается загруженной до тех пор, пока не выключается сервер или системный администратор не выгружает ее с помощью инструкции DBCC. Например, следующая команда выгружает **xp_hello.dll**, позволяя системному администратору, чтобы скопировать новую версию этого файла в каталог без завершения работы сервера:  
  
```  
DBCC xp_hello(FREE)  
```  
  
## <a name="see-also"></a>См. также  
 [DBCC dllname &#40;бесплатный&#41; &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-dllname-free-transact-sql.md)  
  
  
