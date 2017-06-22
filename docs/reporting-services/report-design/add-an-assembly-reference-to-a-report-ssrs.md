---
title: "Добавьте ссылку на сборку в отчет (SSRS) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code [Reporting Services]
- custom assemblies [Reporting Services], referencing
- custom code [Reporting Services]
- adding assembly references
- assemblies [Reporting Services], references
ms.assetid: 0a03939e-48ce-4c30-b227-98533f2e0ccb
caps.latest.revision: 43
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1bf8106435899a97572c5972721bdf3190d031a6
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="add-an-assembly-reference-to-a-report-ssrs"></a>Добавление в отчет ссылку на сборку (службы SSRS)
  При внедрении пользовательского кода, который содержит ссылки на [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] классы, которые не находятся в <xref:System.Math> или <xref:System.Convert>, необходимо указать ссылку на сборку в отчет, чтобы обработчик отчетов может разрешать имена. Дополнительные сведения см. в разделе [Добавление кода в отчет (службы SSRS)](../../reporting-services/report-design/add-code-to-a-report-ssrs.md).  
  
### <a name="to-add-an-assembly-reference-to-a-report"></a>Добавление в отчет ссылки на сборку  
  
1.  В режиме **конструктора** щелкните правой кнопкой мыши в области конструктора за границей отчета и выберите команду **Свойства отчета**.  
  
2.  Нажмите кнопку **Ссылки**.  
  
3.  В окне **Добавить или удалить сборки**нажмите кнопку **Добавить** и затем нажмите кнопку с многоточием, чтобы найти сборку.  
  
4.  В окне **Добавить или удалить классы**нажмите кнопку **Добавить** , а затем введите имя класса и предоставьте имя экземпляра для использования в отчете.  
  
    > [!NOTE]  
    >  Укажите имя класса и имя экземпляра только для элементов, зависимых от экземпляров. Не задавайте статические элементы в списке **Классы** . Дополнительные сведения см. в разделе [Пользовательский код и ссылки на сборки в выражениях в конструкторе отчетов (службы SSRS)](../../reporting-services/report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Использование пользовательских сборок с отчетами](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)   
 [Диалоговое окно «Свойства отчета» — «Ссылки»](http://msdn.microsoft.com/library/4639d368-9918-4bb1-9953-7a724ca78dea)  
  
  
