---
title: Пакет развертывания (службы SSIS) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, deploying
- deploying packages [Integration Services]
- SQL Server Integration Services packages, deploying
- deploying packages [Integration Services], about deploying packages
- packages [Integration Services], deploying
- SSIS packages, deploying
ms.assetid: 0f5fc7be-e37e-4ecd-ba99-697c8ae3436f
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 63d2d0019c725122c091a228dd50a5c97f384211
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48209244"
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
  
  
