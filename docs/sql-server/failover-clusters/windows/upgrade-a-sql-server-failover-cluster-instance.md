---
title: Обновление экземпляра отказоустойчивого кластера SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 10/01/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- upgrading failover clusters
- clusters [SQL Server], upgrading
- failover clustering [SQL Server], upgrading
ms.assetid: daac41fe-7d0b-4f14-84c2-62952ad8cbfa
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 54863db300d7a63404161e438bede2ecc2ec8928
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47783732"
---
# <a name="upgrade-a-sql-server-failover-cluster-instance"></a>Обновление экземпляра отказоустойчивого кластера SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает обновление отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] при установке новой версии [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], нового пакета обновления [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]или накопительного пакета обновления, а также при установке нового пакета обновлений Windows или накопительного пакета обновлений Windows отдельно на все отказоустойчивые кластеры. Это позволяет сократить время простоя до одной операции перехода на другой ресурс вручную (или двух таких операций, если нужно перейти на исходную первичную реплику).  
  
 Обновление операционной системы Windows, в которой размещен отказоустойчивый кластер, не поддерживается для операционных систем, предшествующих [!INCLUDE[winblue-server-2-md](../../../includes/winblue-server-2-md.md)]. Сведения об обновлении узла кластера под управлением [!INCLUDE[winblue-server-2-md](../../../includes/winblue-server-2-md.md)] или более поздней версии см. в разделе [Выполнение последовательного обновления](#perform-a-rolling-upgrade-or-update).  
  
 Далее приведены сведения о поддержке:  
  
-   Обновление [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] можно выполнить как через пользовательский интерфейс, так и с помощью командной строки. Обновление можно запустить из командной строки на каждом узле отказоустойчивого кластера. Можно также обновить каждый узел кластера при помощи пользовательского интерфейса программы установки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  Дополнительные сведения см. в статьях [Обновление экземпляра отказоустойчивого кластера SQL Server (программа установки)](../../../sql-server/failover-clusters/windows/upgrade-a-sql-server-failover-cluster-instance-setup.md) и [Установка SQL Server из командной строки](../../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md).  
  
-   В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не поддерживаются следующие сценарии в рамках обновления:  
  
    -   Невозможно обновить изолированный экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] до кластера отработки отказа.  
  
    -   Невозможно добавить компоненты в кластер отработки отказа. Например, невозможно добавить компонент [!INCLUDE[ssDE](../../../includes/ssde-md.md)] в существующий отказоустойчивый кластер, имеющий только службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
    -   Невозможно понизить узел отказоустойчивого кластера до изолированного экземпляра.  
  
    -   Изменение выпуска отказоустойчивого кластера ограничено определенными сценариями. Дополнительные сведения см. в статье [Supported Version and Edition Upgrades](../../../database-engine/install-windows/supported-version-and-edition-upgrades.md).  
  
-   При обновлении отказоустойчивого кластера время простоя ограничивается временем отработки отказа и временем, необходимым для обновления запускаемых скриптов. При соблюдении процесса последовательного обновления, описанного ниже, и выполнении всех предварительных условий для всех узлов до начала процедуры обновления время простоя сводится к минимуму. Обновление [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] при использовании оптимизированных для памяти таблиц займет немного больше времени. Дополнительные сведения см. в разделе [Составление и тестирование плана обновления ядра СУБД](../../../database-engine/install-windows/plan-and-test-the-database-engine-upgrade-plan.md).  
  
## <a name="prerequisites"></a>предварительные требования  
 Перед установкой ознакомьтесь со следующими важными сведениями.  
  
-   [Обновления поддерживаемых версий и выпусков](../../../database-engine/install-windows/supported-version-and-edition-upgrades.md). Убедитесь, что текущая версия операционной системы Windows позволяет обновить текущую версию [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] до версии [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Например, невозможно напрямую обновить экземпляр отказоустойчивого кластера SQL Server 2005 до версии [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] или обновить отказоустойчивый кластер, запущенный в [!INCLUDE[winxpsvr-md](../../../includes/winxpsvr-md.md)].  
  
-   [Choose a Database Engine Upgrade Method](../../../database-engine/install-windows/choose-a-database-engine-upgrade-method.md). Выберите подходящий метод обновления с учетом сведений о поддерживаемых версиях и обновлениях выпуска, а также компонентах, установленных в среде и требующих обновления (это нужно, чтобы обеспечить правильный порядок обновления этих компонентов).  
  
-   [Составление и тестирование плана обновления Database Engine](../../../database-engine/install-windows/plan-and-test-the-database-engine-upgrade-plan.md). Просмотрите заметки о выпуске и известные проблемы, связанные с обновлением, изучите контрольный список предварительных требований, а затем разработайте и протестируйте план обновления.  
  
-   [Требования к оборудованию и программному обеспечению для установки SQL Server](../../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md). Ознакомьтесь с требованиями к оборудованию и ПО для установки [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Если требуется дополнительное программное обеспечение, установите его на каждом узле перед запуском обновления, чтобы минимизировать время простоя.  
  
## <a name="perform-a-rolling-upgrade-or-update"></a>Выполнение последовательного обновления  
 Чтобы обновить отказоустойчивый кластер [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] до версии [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], необходимо поочередно запустить программу установки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] на каждом узле отказоустойчивого кластера, начиная с пассивных. В процессе обновления каждого узла связи последнего с возможными владельцами соответствующего отказоустойчивого кластера прерываются. В случае непредвиденной отработки отказа обновленные узлы не участвуют в этом процессе до тех пор, пока программа установки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не передаст группу ресурсов кластера во владение одному из обновленных узлов.  
  
 По умолчанию программа установки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] автоматически определяет момент перехода на обновленный узел. Этот момент определяется в зависимости от общего числа узлов в экземпляре отказоустойчивого кластера и от количества уже обновленных узлов. Если обновлена половина или большее число узлов, при выполнении обновления следующего узла программа установки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] осуществляет отработку отказа с переходом на один из обновленных узлов. После отработки отказа с переходом на обновленный узел кластерная группа перемещается на обновленный узел. Все обновленные узлы помещаются в список возможных владельцев, а все еще не обновленные узлы удаляются из списка возможных владельцев. При обновлении каждого из оставшихся узлов этот узел добавляется к возможным владельцам соответствующего отказоустойчивого кластера.  
  
 В результате этого процесса время простоя ограничивается временем отработки отказа и временем выполнения скрипта обновления базы данных в течение всей операции обновления отказоустойчивого кластера.  
  
 Чтобы управлять отработкой отказа узлов кластера во время обновления, запустите операцию обновления из командной строки с параметром /FAILOVERCLUSTERROLLOWNERSHIP. Дополнительные сведения см. в разделе [Установка SQL Server из командной строки](../../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md).  
  
## <a name="next-steps"></a>Следующие шаги  
 [Обновление SQL Server с помощью мастера установки &#40;программа установки&#41;](../../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)   
 [Установка SQL Server из командной строки](../../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)   
 [Обновление экземпляра отказоустойчивого кластера SQL Server (программа установки)](../../../sql-server/failover-clusters/windows/upgrade-a-sql-server-failover-cluster-instance-setup.md)  
  
  
