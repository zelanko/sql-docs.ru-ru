---
title: "Копирование пакета с помощью SQL Server Data Tools | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "пакеты [службы Integration Services], копирование"
  - "копирование пакетов"
  - "повторное создание идентификатора GUID пакета"
  - "обновление свойств пакета"
ms.assetid: 03edc659-e76d-48c0-a749-5f1899b6b507
caps.latest.revision: 18
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 18
---
# Копирование пакета с помощью SQL Server Data Tools
  В этом разделе описывается, как создать новый пакет служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] копированием существующего пакета и как обновить свойства **Name** и **GUID** нового пакета.  
  
### Копирование пакета  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , содержащий пакет, который нужно скопировать.  
  
2.  Дважды щелкните пакет в обозревателе решений.  
  
3.  Убедитесь, что копируемый пакет выбран в обозревателе решений либо в конструкторе служб SSIS выбрана вкладка, содержащая пакет  
  
4.  В меню **Файл** выберите команду **Сохранить \<имя пакета> как**.  
  
    > [!NOTE]  
    >  Чтобы команда **Сохранить как** появилась в меню **Файл**, пакет нужно открыть в конструкторе служб SSIS.  
  
5.  При необходимости перейдите в другую папку.  
  
6.  Обновите имя файла пакета. Убедитесь, что файл сохраняется с расширением DTSX.  
  
7.  Нажмите кнопку **Сохранить**.  
  
8.  Выберите, обновлять ли имя объекта пакета, чтобы оно соответствовало имени файла. Если нажать кнопку **Да**, то свойство пакета **Name** обновится. Новый пакет будет добавлен к проекту служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] и открыт в конструкторе служб [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
9. При необходимости перейдите на вкладку **Поток управления** и выберите **Свойства**.  
  
10. В окне "Свойства" щелкните значение свойства идентификатора (ID), а затем выберите **\<Сформировать новый идентификатор>** в раскрывающемся списке.  
  
11. В меню **Файл** выберите команду **Сохранить выбранные элементы** , чтобы сохранить новый пакет.  
  
## См. также  
 [Сохранение одной копии пакета](../Topic/Save%20a%20Copy%20of%20a%20Package.md)   
 [Создание пакетов в SQL Server Data Tools](../integration-services/create-packages-in-sql-server-data-tools.md)   
 [Пакеты служб Integration Services (SSIS)](../integration-services/integration-services-ssis-packages.md)  
  
  