---
title: Клиентские протоколы — свойства именованных каналов (вкладка "Протокол") | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- pipes [SQL Server], connecting to
- Named Pipes [SQL Server], default pipe
- client protocols [SQL Server]
ms.assetid: 30fbae62-2f2e-4d36-9c6e-3444fff68781
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3fe7bb05afc8e0814ddb3d872a810759aae2a678
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63253550"
---
# <a name="client-protocols---named-pipes-properties-protocol-tab"></a>Клиентские протоколы — свойства именованных каналов (вкладка «Протокол»)
  В диспетчере конфигурации [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используйте вкладку **Протокол** диалогового окна **Свойства именованных каналов** для просмотра или изменения описания канала по умолчанию. Для подключения к другому каналу введите название канала в поле **Канал по умолчанию** . Дополнительные сведения о строках подключения см. в разделе [Создание допустимое подключение String Using Named Pipes](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md).  
  
## <a name="options"></a>Параметры  
 **Канал по умолчанию**  
 Задает канал по умолчанию, который будет использоваться сетевой библиотекой именованных каналов для попыток подключения к целевому экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] прослушивает `\\.\pipe\sql\query`  
  
 Чтобы подключиться к каналу по умолчанию, введите `sql\query`  
  
 **Включено**  
 Возможные значения: **Да** и **Нет**.  
  
## <a name="see-also"></a>См. также  
 [Выбор сетевого протокола](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  
