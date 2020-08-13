---
title: Удаление экземпляра отказоустойчивого кластера
description: Эта процедура используется для удаления экземпляра отказоустойчивого кластера SQL Server. В этой статье приводятся важные рекомендации, которые необходимо выполнить, прежде чем продолжать.
ms.custom: seo-lt-2019
ms.date: 12/13/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- clusters [SQL Server], removing failover clustered instance
- failover clustering [SQL Server], removing failover clustered instance
- uninstalling failover clustered instances
- removing failover clustered instances
ms.assetid: bf63353b-69cf-4c5c-98ea-7b151e36537f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dba18abbd7eb5938b7f2fa4d0c3caff8d5d6f567
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85897674"
---
# <a name="remove-a-sql-server-failover-cluster-instance-setup"></a>Удаление экземпляра отказоустойчивого кластера SQL Server (программа установки)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
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
  
  
