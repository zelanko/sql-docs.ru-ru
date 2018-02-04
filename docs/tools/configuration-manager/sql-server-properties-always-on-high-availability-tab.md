---
title: "Свойства SQL Server (всегда на вкладку высокий уровень доступности) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: configuration-manager
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d8630923-a600-4f1c-aca1-027453a3ec82
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c8ca29178e6465a162f6e19cabb307e6e742ae28
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sql-server-properties-always-on-high-availability-tab"></a>Свойства SQL Server (вкладка "Высокий уровень доступности AlwaysOn")
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
На вкладке **Высокий уровень доступности AlwaysOn** в диалоговом окне **Свойства SQL Server** в диспетчере конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно включить или отключить функцию "Группы доступности AlwaysOn" в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Включение функции "Группы доступности AlwaysOn" является предварительным требованием для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , чтобы группы доступности использовались в качестве решения высокого уровня доступности и аварийного восстановления.  
  
##  <a name="Prerequisites"></a> Предварительные требования  
 Для включения функции "Группы доступности AlwaysOn" экземпляр должен соответствовать следующим предварительным условиям.  
  
-   Экземпляр сервера должен находиться на узле отказоустойчивой кластеризации Windows Server (WSFC).  
  
-   Чтобы оказаться в одной и той же группе доступности, экземпляры должны входить в один и тот же кластер WSFC. Группа доступности не может пересекать границы кластера WSFC.  
  
-   Экземпляр сервера должен работать на выпуске [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который поддерживает [!INCLUDE[ssHADR](../../includes/sshadr-md.md)].  
  
-   Включайте функцию "Группы доступности AlwaysOn" только для одного экземпляра сервера в один момент времени. После включения функции "Группы доступности AlwaysOn" дождитесь, пока служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] перезапустится, и только после этого включайте следующий экземпляр.  
  
> [!NOTE]  
>  Сведения о поддержке компонентов и о других предварительных условиях, ограничениях и рекомендациях по [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]см. в электронной документации по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
## <a name="dialog-options"></a>Параметры диалогового окна  
 **Имя отказоустойчивого кластера Windows**  
 Отображает имя кластера WSFC, в котором локальный компьютер является узлом.  
  
 **Включение групп доступности AlwaysOn**  
 Этот флажок позволяет включить или выключить функцию "Группы доступности AlwaysOn" в данном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]следующим образом:  
  
-   Если этот флажок пуст, то функция "Группы доступности AlwaysOn" в настоящее время отключена. Чтобы включить "Группы доступности AlwaysOn", выберите флажок, нажмите кнопку **ОК**и вручную перезапустите службу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Если этот флажок уже выбран, то функция "Группы доступности AlwaysOn" в настоящее время включена. Чтобы отключить "Группы доступности AlwaysOn", снимите этот флажок и нажмите кнопку **ОК**. Экземпляр сервера будет перезапущен автоматически.  
  
    > [!TIP]  
    >  После отключения функции "Группы доступности AlwaysOn" необходимо удалить все локальные реплики доступности с экземпляра сервера. При удалении последней реплики для данной группы доступности будет также удалена и сама группа.  
  
## <a name="uielement-list"></a>Список элементов пользовательского интерфейса  
  
> [!NOTE]  
>  Дополнительные сведения о действиях после отключения функции "Группы доступности AlwaysOn" и о том, как создать и настроить группы доступности, см. в электронной документации по [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
  
