---
title: Клиентские протоколы — свойства именованных каналов (вкладка «Протокол»)
description: Сведения о том, как просмотреть или изменить описание канала по умолчанию в диспетчере конфигурации SQL Server. Сведения о том, как подключиться к другому каналу.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- pipes [SQL Server], connecting to
- Named Pipes [SQL Server], default pipe
- client protocols [SQL Server]
ms.assetid: 30fbae62-2f2e-4d36-9c6e-3444fff68781
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016'
ms.openlocfilehash: 6e637bb0dd5979e5149ef70cba59ed8a4ac7f583
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97463886"
---
# <a name="client-protocols---named-pipes-properties-protocol-tab"></a>Клиентские протоколы — свойства именованных каналов (вкладка «Протокол»)
[!INCLUDE [SQL Server Windows Only - ASDBMI ](../../includes/applies-to-version/sql-windows-only-asdbmi.md)]
  В диспетчере конфигурации [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используйте вкладку **Протокол** в диалоговом окне **Named Pipes Properties** (Свойства именованных каналов) для просмотра или изменения описания канала по умолчанию. Для подключения к другому каналу введите название канала в поле **Канал по умолчанию** . Дополнительные сведения о строках соединения см. в разделе [Creating a Valid Connection String Using Named Pipes](/previous-versions/sql/sql-server-2016/ms189307(v=sql.130)).  
  
## <a name="options"></a>Параметры  
 **Канал по умолчанию**  
 Задает канал по умолчанию, который будет использоваться сетевой библиотекой именованных каналов для попыток подключения к целевому экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] прослушивает `\\.\pipe\sql\query`  
  
 Чтобы подключиться к каналу по умолчанию, введите `sql\query`  
  
 **Enabled**  
 Возможные значения: **Да** и **Нет**.  
  
## <a name="see-also"></a>См. также:  
 [Выбор сетевого протокола](/previous-versions/sql/sql-server-2016/ms187892(v=sql.130))  
  
