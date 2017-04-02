---
title: "Добавление в отчет ссылку на сборку (службы SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "код [службы Reporting Services]"
  - "пользовательские сборки [службы Reporting Services], ссылки"
  - "пользовательский код [службы Reporting Services]"
  - "добавление ссылок на сборку"
  - "сборки [службы Reporting Services], ссылки"
ms.assetid: 0a03939e-48ce-4c30-b227-98533f2e0ccb
caps.latest.revision: 43
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 43
---
# Добавление в отчет ссылку на сборку (службы SSRS)
  При внедрении пользовательского кода, содержащего ссылки на классы платформы [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], не входящие в <xref:System.Math> или <xref:System.Convert>, необходимо предоставить в отчете ссылку на сборку, чтобы обработчик отчетов мог разрешать имена этих классов. Дополнительные сведения см. в разделе [Добавление кода в отчет (службы SSRS)](../../reporting-services/report-design/add-code-to-a-report-ssrs.md).  
  
### Добавление в отчет ссылки на сборку  
  
1.  В режиме **конструктора** щелкните правой кнопкой мыши в области конструктора за границей отчета и выберите команду **Свойства отчета**.  
  
2.  Нажмите кнопку **Ссылки**.  
  
3.  В окне **Добавить или удалить сборки**нажмите кнопку **Добавить** и затем нажмите кнопку с многоточием, чтобы найти сборку.  
  
4.  В окне **Добавить или удалить классы**нажмите кнопку **Добавить** , а затем введите имя класса и предоставьте имя экземпляра для использования в отчете.  
  
    > [!NOTE]  
    >  Укажите имя класса и имя экземпляра только для элементов, зависимых от экземпляров. Не задавайте статические элементы в списке **Классы** . Дополнительные сведения см. в разделе [Пользовательский код и ссылки на сборки в выражениях в конструкторе отчетов (службы SSRS)](../../reporting-services/report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## См. также  
 [Использование пользовательских сборок с отчетами](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)   
 [Диалоговое окно «Свойства отчета» — «Ссылки»](../Topic/Report%20Properties%20Dialog%20Box,%20References.md)  
  
  