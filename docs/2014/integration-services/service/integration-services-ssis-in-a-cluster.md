---
title: Службы Integration Services (SSIS) в кластере | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 0216266d-d866-4ea2-bbeb-955965f4d7c2
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b70dbab14424335fe210f5a9b1ddbdbda4f90deb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62889317"
---
# <a name="integration-services-ssis-in-a-cluster"></a>Службы Integration Services (SSIS) в кластере
  Кластеризация служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] не рекомендуется, так как службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] не являются кластеризованными, не ориентируются на использование кластеров и не поддерживают отработку отказа между узлами кластера. Следовательно, в кластерной среде службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] должны быть установлены и запущены в качестве изолированной службы на каждом узле кластера.  
  
 Хотя служба [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и не является службой, поддерживающей работу в кластере, ее можно вручную настроить на работу в качестве ресурса кластера после того, как служба [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] будет отдельно установлена на каждом узле кластера.  
  
 Однако если целью постройки кластеризованной аппаратной среды является достижение высокого уровня доступности, то этой цели можно добиться и без настройки службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] в качестве ресурса кластера.  Чтобы управлять пакетами, находящимися на любом узле кластера, с любого другого узла кластера, измените файл конфигурации для службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на каждом узле кластера. Необходимо так изменить эти файлы конфигурации, чтобы они указывали на все доступные экземпляры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , на которых хранятся пакеты. Такое решение предоставляет высокий уровень доступности, необходимый для большинства клиентов, а также избегает потенциальных проблем, с которыми можно столкнуться при настройке службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] в качестве ресурса кластера. Дополнительные сведения об изменении этого файла конфигурации см. в статье [Настройка служб Integration Services (SSIS)](integration-services-service-ssis-service.md).  
  
 Понимание роли службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] крайне важно для принятия компетентного решения относительно настройки службы в кластерной среде. Дополнительные сведения см. в разделе [Службы Integration Services (SSIS)](integration-services-service-ssis-service.md).  
  
## <a name="understanding-the-disadvantages-of-configuring-integration-services-as-a-cluster-resource"></a>Основные сведения о недостатках настройки службы Integration Services в качестве ресурса кластера  
 Далее приводятся потенциальные недостатки настройки службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] в качестве ресурса кластера.  
  
-   При отработке отказа не происходит повторного запуска выполняющихся пакетов. Восстановление после ошибок пакетов можно произвести, перезапустив пакеты с контрольных точек. Перезапуск с контрольных точек можно производить и без настройки службы в качестве ресурса кластера. Дополнительные сведения см. в разделе [Restart Packages by Using Checkpoints](../packages/restart-packages-by-using-checkpoints.md).  
  
-   Если служба [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] была настроена в группе ресурсов, отличной от группы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то будет невозможно использовать среду [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] на клиентских компьютерах для управления пакетами, хранящимися в базе данных msdb. В этом двухшаговом сценарии служба [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] не может делегировать учетные данные.  
  
-   Если существует несколько групп ресурсов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которые включают службу [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] в кластер, то при отработке отказа могут возникнуть непредвиденные результаты. Рассмотрим следующий сценарий. Группа1, в которую входят служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и служба [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , выполняется на узле А. Группа2, в которую также входят служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и служба [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , выполняется на узле Б. Происходит переход Группы2 на узел А. Попытка запуска другого экземпляра службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на узле А завершается с ошибкой, поскольку допускается существование только одного экземпляра службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Завершится ли с ошибкой служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при попытке перехода на узел А, зависит от конфигурации службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] в Группе2. Если служба [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] была настроена для влияния на другие службы в группе ресурсов, то служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при попытке перехода завершится с ошибкой, потому что служба [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] завершилась с ошибкой. Если служба была настроена не влиять на другие службы в группе ресурсов, то служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сможет совершить переход на узел А. Если служба [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] в Группе2 не была настроена не затрагивать другие службы в группе ресурсов, то завершение с ошибкой переходящей службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] может вызвать завершение с ошибкой переходящей службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="related-tasks"></a>Связанные задачи  
 Пошаговые инструкции по настройке службы Integration Services в кластере см. в разделе [Настройка служб Integration Services на работу в качестве ресурса кластера](../configure-the-integration-services-service-as-a-cluster-resource.md).  
  
  
