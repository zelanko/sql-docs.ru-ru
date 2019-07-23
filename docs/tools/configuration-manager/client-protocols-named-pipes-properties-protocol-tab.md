---
title: Клиентские протоколы — свойства именованных каналов (вкладка "Протокол") | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- pipes [SQL Server], connecting to
- Named Pipes [SQL Server], default pipe
- client protocols [SQL Server]
ms.assetid: 30fbae62-2f2e-4d36-9c6e-3444fff68781
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: b971f59abd9238c74a3c26d6cc019f7c55908326
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68010255"
---
# <a name="client-protocols---named-pipes-properties-protocol-tab"></a>Клиентские протоколы — свойства именованных каналов (вкладка «Протокол»)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  В диспетчере конфигурации [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используйте вкладку **Протокол** диалогового окна **Свойства именованных каналов** для просмотра или изменения описания канала по умолчанию. Для подключения к другому каналу введите название канала в поле **Канал по умолчанию** . Дополнительные сведения о строках соединения см. в разделе [Creating a Valid Connection String Using Named Pipes](https://msdn.microsoft.com/library/90930ff2-143b-4651-8ae3-297103600e4f).  
  
## <a name="options"></a>Параметры  
 **Канал по умолчанию**  
 Задает канал по умолчанию, который будет использоваться сетевой библиотекой именованных каналов для попыток подключения к целевому экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] прослушивает `\\.\pipe\sql\query`  
  
 Чтобы подключиться к каналу по умолчанию, введите `sql\query`  
  
 **Включено**  
 Возможные значения: **Да** и **Нет**.  
  
## <a name="see-also"></a>См. также:  
 [Выбор сетевого протокола](https://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)  
  
  
