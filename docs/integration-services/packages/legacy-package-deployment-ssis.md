---
title: "Устаревшее развертывание пакетов (службы SSIS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "пакеты служб Integration Services, развертывание"
  - "развертывание пакетов [службы Integration Services]"
  - "пакеты служб SQL Server Integration Services, развертывание"
  - "развертывание пакетов [службы Integration Services], о развертывании пакетов"
  - "пакеты [службы Integration Services], развертывание"
  - "пакеты служб SSIS, развертывание"
ms.assetid: 0f5fc7be-e37e-4ecd-ba99-697c8ae3436f
caps.latest.revision: 46
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 46
---
# Устаревшее развертывание пакетов (службы SSIS)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] включают в себя средства и мастера, которые упрощают развертывание пакетов с компьютера разработчика на рабочий сервер или другие компьютеры.  
  
 Процесс развертывания пакетов состоит из четырех шагов.  
  
1.  Первый шаг является необязательным и заключается в создании конфигураций пакетов, обновляющих свойства элементов пакетов во время выполнения. Настройки будут автоматически включены при развертывании пакета.  
  
2.  Второй шаг — построение проекта служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] для создания программы развертывания пакетов. Программа развертывания для проекта содержит пакеты, которые необходимо развернуть.  
  
3.  Третий шаг — копирование папки развертывания, созданной в ходе построения проекта служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , на целевой компьютер.  
  
4.  Четвертый шаг заключается в запуске на целевом компьютере мастера установки пакета, который позволяет установить пакеты в файловую систему или на экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## Связанные задачи  
 Дополнительные сведения о создании программы развертывания см. в разделе [Создание программы развертывания](../../integration-services/packages/create-a-deployment-utility.md).  
  
 Дополнительные сведения о развертывании пакетов с помощью программы развертывания см. в разделе [Развертывание пакетов с помощью программы развертывания](../../integration-services/packages/deploy-packages-by-using-the-deployment-utility.md).  
  
 Дополнительные сведения о создании конфигурации пакетов см. в разделе [Создание конфигурации пакетов](../../integration-services/packages/create-package-configurations.md).  
  
  