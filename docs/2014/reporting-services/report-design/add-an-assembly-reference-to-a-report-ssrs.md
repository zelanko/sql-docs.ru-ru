---
title: Добавление в отчет ссылку на сборку (службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- code [Reporting Services]
- custom assemblies [Reporting Services], referencing
- custom code [Reporting Services]
- adding assembly references
- assemblies [Reporting Services], references
ms.assetid: 0a03939e-48ce-4c30-b227-98533f2e0ccb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 23dda0c65589e55849f906c621e42ce70f0d7ab5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66106761"
---
# <a name="add-an-assembly-reference-to-a-report-ssrs"></a>Добавление в отчет ссылку на сборку (службы SSRS)
  При внедрении пользовательского кода, содержащего ссылки на [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] классы, отсутствующие в <xref:System.Math> или <xref:System.Convert>, необходимо предоставить ссылку на сборку для отчета, чтобы обработчик отчетов мог разрешить имена. Дополнительные сведения см. в разделе [Добавление кода в отчет (службы SSRS)](add-code-to-a-report-ssrs.md).  
  
### <a name="to-add-an-assembly-reference-to-a-report"></a>Добавление в отчет ссылки на сборку  
  
1.  В режиме **конструктора** щелкните правой кнопкой мыши в области конструктора за границей отчета и выберите команду **Свойства отчета**.  
  
2.  Нажмите кнопку **Ссылки**.  
  
3.  В окне **Добавить или удалить сборки**нажмите кнопку **Добавить** и затем нажмите кнопку с многоточием, чтобы найти сборку.  
  
4.  В окне **Добавить или удалить классы**нажмите кнопку **Добавить** , а затем введите имя класса и предоставьте имя экземпляра для использования в отчете.  
  
    > [!NOTE]  
    >  Укажите имя класса и имя экземпляра только для элементов, зависимых от экземпляров. Не задавайте статические элементы в списке **Классы** . Дополнительные сведения см. в разделе [Пользовательский код и ссылки на сборки в выражениях в конструкторе отчетов (службы SSRS)](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Использование пользовательских сборок с отчетами](../custom-assemblies/using-custom-assemblies-with-reports.md)   
 [Диалоговое окно «Свойства отчета» — «Ссылки»](../report-properties-dialog-box-references.md)  
  
  
