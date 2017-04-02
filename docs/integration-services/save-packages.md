---
title: "Сохранение пакетов | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.savecopyas.f1"
helpviewer_keywords: 
  - "пакеты служб Integration Services, сохранение"
  - "пакеты [службы Integration Services], сохранение"
  - "сохранение пакетов"
  - "пакеты служб SSIS, сохранение"
  - "пакеты служб SQL Server Integration Services, сохранение"
ms.assetid: 17c1de2c-637f-45c2-a148-79294bae0af4
caps.latest.revision: 48
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 47
---
# Сохранение пакетов
  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] пакеты создаются с помощью конструктора служб [!INCLUDE[ssIS](../includes/ssis-md.md)] и сохраняются в файловой системе как XML-файлы (DTSX-файлы). Копии XML-файла пакета можно также сохранять в базе данных msdb в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] или в хранилище пакетов. Хранилище пакетов представляет собой папки в определенном месте файловой системы, управляемые службами [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
 При сохранении пакета в файловой системе можно в дальнейшем использовать службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , чтобы выполнить импорт пакета в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] или в хранилище пакетов. Дополнительные сведения см. в разделе [Импорт и экспорт пакетов (службы SSIS)](../integration-services/service/import-and-export-packages-ssis-service.md).  
  
 Можно также использовать программу командной строки **dtutil** для копирования пакета между файловой системой и базой данных msdb. Дополнительные сведения см. в статье [dtutil Utility](../integration-services/dtutil-utility.md).  
  
### Сохранение пакета  
  
-   [Сохранение пакета в файловой системе](../Topic/Save%20a%20Package%20to%20the%20File%20System.md)  
  
-   [Сохранение одной копии пакета](../Topic/Save%20a%20Copy%20of%20a%20Package.md)  
  
  