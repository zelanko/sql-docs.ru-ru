---
title: "Свойства именованных каналов | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: configuration-manager
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipes [SQL Server]
- listening [SQL Server], pipes
- pipes [SQL Server], listening on pipes
- Named Pipes [SQL Server], listening on pipes
ms.assetid: a5fd5b8e-f889-485b-89e3-d4010ec4c6ec
caps.latest.revision: "32"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 72fecdede46024eae399d9a762b0f8cdf7bb3a6b
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2018
---
# <a name="named-pipes-properties"></a>Свойства именованных каналов
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Используйте **протокола**на странице **свойства именованных каналов** диалоговое окно «», чтобы просмотреть или изменить именованный канал, который [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ожидает передачи данных, при использовании протокола именованных каналов.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]должен быть перезапущен, чтобы включить или отключить протокол или изменить именованный канал.  
  
## <a name="options"></a>Параметры  
 **Enabled**  
 Возможные значения: **Да** и **Нет**.  
  
 **Имя канала**  
 Указывает именованный канал, который прослушивается [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] прослушивает `\\.\pipe\sql\query` для экземпляра по умолчанию и `\\.\pipe\MSSQL$<instancename>\sql\query` для именованного экземпляра. Длина этого поля ограничена 2047 символами.  
  
## <a name="creating-an-alternate-named-pipe"></a>Создание альтернативного именованного канала  
 Чтобы изменить именованный канал, введите новое имя канала в поле **Имя канала** , а затем остановите и перезапустите [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Так как **sql\query** хорошо известен в качестве именованного канала, используемого [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], изменение канала может помочь сократить риск проведения атак вредоносными программами.  
  
### <a name="example"></a>Пример  
 Введите **\\\\.\pipe\unit\app** , чтобы прослушивать канал **unit\app** .  
  
 Введите **\\\\.\pipe\acct** , чтобы прослушивать канал **acct** .  
  
## <a name="see-also"></a>См. также  
 [Включение или отключение сетевого протокола сервера](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)   
 [Выбор сетевого протокола](http://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)   
 [Создание допустимой строки соединения с использованием именованных каналов](http://msdn.microsoft.com/library/90930ff2-143b-4651-8ae3-297103600e4f)  
  
  
