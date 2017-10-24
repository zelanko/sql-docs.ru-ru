---
title: "Клиентские протоколы — свойства именованных каналов (вкладка «Протокол») | Документы Microsoft"
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
- pipes [SQL Server], connecting to
- Named Pipes [SQL Server], default pipe
- client protocols [SQL Server]
ms.assetid: 30fbae62-2f2e-4d36-9c6e-3444fff68781
caps.latest.revision: 23
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 33d801033e2431f465e97502dcabf37f6a9c4847
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# Клиентские протоколы — свойства именованных каналов (вкладка «Протокол»)
  В диспетчере конфигурации [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используйте вкладку **Протокол** диалогового окна **Свойства именованных каналов** для просмотра или изменения описания канала по умолчанию. Для подключения к другому каналу введите название канала в поле **Канал по умолчанию** . Дополнительные сведения о строках соединения см. в разделе [Creating a Valid Connection String Using Named Pipes](http://msdn.microsoft.com/library/90930ff2-143b-4651-8ae3-297103600e4f).  
  
## Параметры  
 **Канал по умолчанию**  
 Задает канал по умолчанию, который будет использоваться сетевой библиотекой именованных каналов для попыток подключения к целевому экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] прослушивает:`\\.\pipe\sql\query`  
  
 Чтобы подключиться к каналу по умолчанию, введите `sql\query`  
  
 **Включено**  
 Возможные значения: **Да** и **Нет**.  
  
## См. также  
 [Выбор сетевого протокола](http://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)  
  
  

