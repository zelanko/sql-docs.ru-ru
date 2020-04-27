---
title: Удаление экземпляра отказоустойчивого кластера SQL Server (программа установки) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: 07b57b7ebea8a2bf5eaf381c09d7eb29dd6a4cd4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63017032"
---
# <a name="remove-a-sql-server-failover-cluster-instance-setup"></a>Удаление экземпляра отказоустойчивого кластера SQL Server (программа установки)
  Выполните следующую процедуру для удаления экземпляра кластера отработки отказа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
> [!IMPORTANT]  
>  Чтобы обновить или удалить экземпляр отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , необходимо иметь разрешения локального администратора для входа в систему в качестве службы на все узлы отказоустойчивого кластера.  
  
 **Before you begin**  
  
 Учтите следующие важные моменты перед удалением отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
-   Если собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] случайно удален, не смогут запуститься ресурсы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Чтобы переустановить собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , запустите программу установки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и установите предварительно необходимые компоненты [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
-   При удалении отказоустойчивого кластера, обладающего более чем одним кластерным ресурсом SQL IP, необходимо удалить дополнительные ресурсы SQL IP при помощи администратора кластера.  
  
 Дополнительные сведения о синтаксисе командной строки см. [в разделе Install SQL Server 2014 из командной строки](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).  
  
### <a name="to-uninstall-a-ssnoversion-failover-cluster"></a>Удаление отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  
  
1.  Для удаления отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] используется функция удаления узла, предоставляемая программой установки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , которая удаляет каждый узел по отдельности. Дополнительные сведения см. на странице [Добавление и удаление узлов в отказоустойчивом кластере SQL Server (настройка)](add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).  
  
## <a name="see-also"></a>См. также:  
 [Просмотр и чтение файлов журналов программы установки SQL Server](../../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
  
