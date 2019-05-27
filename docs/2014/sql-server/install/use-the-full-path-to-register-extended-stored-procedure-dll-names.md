---
title: Используйте полный путь, чтобы зарегистрировать расширенную хранимую процедуру имена библиотек DLL | Документация Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- registering DLL names
- extended stored procedures [SQL Server], registering
- DLL names [SQL Server]
- full path DLL name registration [SQL Server]
ms.assetid: f648d57c-af32-4c71-9882-47b6766f3c2b
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e560ec0fd617d4da46235803da8cbd69ef4f80d5
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66091292"
---
# <a name="use-the-full-path-to-register-extended-stored-procedure-dll-names"></a>Используйте полный путь для регистрации имен DLL-библиотек расширенных хранимых процедур
  Расширенные хранимые процедуры, ранее зарегистрированные без указания полного пути к DLL, могут не работать в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Описание  
 Расширенные хранимые процедуры, ранее зарегистрированные без указания полного пути к DLL-библиотеке, могут не работать после обновления. Это происходит, потому что прежний каталог BINN в процессе обновления не добавляется к новому пути. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может не найти расширенные хранимые процедуры.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Перед обновлением выполните следующие шаги для каждой расширенной хранимой процедуры, не зарегистрированной с использованием полного пути.  
  
1.  Чтобы удалить расширенную хранимую процедуру, выполните хранимую процедуру sp_dropextendedproc.  
  
2.  Чтобы зарегистрировать расширенную хранимую процедуру с указанием полного пути, выполните хранимую процедуру sp_addextendedproc.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
