---
title: "Свойства именованных каналов | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipes [SQL Server]
- listening [SQL Server], pipes
- pipes [SQL Server], listening on pipes
- Named Pipes [SQL Server], listening on pipes
ms.assetid: a5fd5b8e-f889-485b-89e3-d4010ec4c6ec
caps.latest.revision: 32
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a5e2f9b67c74a5eea97209bb812ee2e385c9c41a
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="named-pipes-properties"></a>Свойства именованных каналов
  Используйте страницу **Протокол**в диалоговом окне **Свойства именованных каналов** , чтобы просмотреть или изменить именованный канал, который прослушивается [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , во время использования протокола именованных каналов.  
  
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
  
  

