---
title: Пакет развертывания (службы SSIS) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, deploying
- deploying packages [Integration Services]
- SQL Server Integration Services packages, deploying
- deploying packages [Integration Services], about deploying packages
- packages [Integration Services], deploying
- SSIS packages, deploying
ms.assetid: 0f5fc7be-e37e-4ecd-ba99-697c8ae3436f
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: c912d4417842bc332262549cc604b97eaa50a44d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62767096"
---
# <a name="package-deployment-ssis"></a>Развертывание пакетов (службы SSIS)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] включают в себя средства и мастера, которые упрощают развертывание пакетов с компьютера разработчика на рабочий сервер или другие компьютеры.  
  
 Процесс развертывания пакетов состоит из четырех шагов.  
  
1.  Первый шаг является необязательным и заключается в создании конфигураций пакетов, обновляющих свойства элементов пакетов во время выполнения. Настройки будут автоматически включены при развертывании пакета.  
  
2.  Второй шаг — построение проекта служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] для создания программы развертывания пакетов. Программа развертывания для проекта содержит пакеты, которые необходимо развернуть.  
  
3.  Третий шаг — копирование папки развертывания, созданной в ходе построения проекта служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , на целевой компьютер.  
  
4.  Четвертый шаг заключается в запуске на целевом компьютере мастера установки пакета, который позволяет установить пакеты в файловую систему или на экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="related-tasks"></a>Связанные задачи  
 Дополнительные сведения о создании программы развертывания см. в разделе [Создание программы развертывания](../create-a-deployment-utility.md).  
  
 Дополнительные сведения о развертывании пакетов с помощью программы развертывания см. в разделе [Развертывание пакетов с помощью программы развертывания](../deploy-packages-by-using-the-deployment-utility.md).  
  
 Дополнительные сведения о создании конфигурации пакетов см. в разделе [Создание конфигурации пакетов](../create-package-configurations.md).  
  
  
