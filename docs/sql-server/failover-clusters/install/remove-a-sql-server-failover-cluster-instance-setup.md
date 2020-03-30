---
title: Удаление экземпляра отказоустойчивого кластера
ms.custom: seo-lt-2019
ms.date: 12/13/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- clusters [SQL Server], removing failover clustered instance
- failover clustering [SQL Server], removing failover clustered instance
- uninstalling failover clustered instances
- removing failover clustered instances
ms.assetid: bf63353b-69cf-4c5c-98ea-7b151e36537f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 97573a3a8a7d08f9eb615443dd7b0d42d6fd1b23
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "75230725"
---
# <a name="remove-a-sql-server-failover-cluster-instance-setup"></a>Удаление экземпляра отказоустойчивого кластера SQL Server (программа установки)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Выполните следующую процедуру для удаления экземпляра кластера отработки отказа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
> [!IMPORTANT]  
>  Чтобы обновить или удалить экземпляр отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , необходимо иметь разрешения локального администратора для входа в систему в качестве службы на все узлы отказоустойчивого кластера.  
  
 **Before you begin**  
  
 Учтите следующие важные моменты перед удалением отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
-   Если собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] случайно удален, не смогут запуститься ресурсы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Чтобы переустановить собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , запустите программу установки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и установите предварительно необходимые компоненты [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
-   При удалении отказоустойчивого кластера, обладающего более чем одним кластерным ресурсом SQL IP, необходимо удалить дополнительные ресурсы SQL IP при помощи администратора кластера.  
  
 Сведения о синтаксисе командной строки см. в разделе [Установка SQL Server 2016 из командной строки](../../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md).  
  
### <a name="to-uninstall-a-ssnoversion-failover-cluster"></a>Удаление отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  
  
1.  Для удаления отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] используется функция удаления узла, предоставляемая программой установки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , которая удаляет каждый узел по отдельности. Дополнительные сведения см. на странице [Добавление и удаление узлов в отказоустойчивом кластере SQL Server (настройка)](../../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).  
  
## <a name="see-also"></a>См. также:  
 [Просмотр и чтение файлов журналов программы установки SQL Server](../../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
  
