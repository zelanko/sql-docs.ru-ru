---
title: "Требования к реализации пользовательских отчетов элементов | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- custom report items
ms.assetid: cfacd816-00d6-4a3d-be72-1bba6f7f6886
caps.latest.revision: 22
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 43770b0b167e2a40874d1b8f31b3b146e62ec2b5
ms.contentlocale: ru-ru
ms.lasthandoff: 08/12/2017

---
# <a name="custom-report-item-implementation-requirements"></a>Требования к реализации пользовательских элементов отчета
  В этом разделе обсуждаются предварительные условия, которые необходимо выполнить перед разработкой и развертыванием пользовательских элементов отчета.  
  
## <a name="development-and-deployment-requirements"></a>Требования разработки и развертывания  
 Для разработки пользовательского элемента отчета для служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] необходимо следующее:  
  
-   административный доступ к серверу, работающему под управлением [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] со службами [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и средой [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)];  
  
-   [!INCLUDE[vsprvsext](../../includes/vsprvsext-md.md)]или более поздней версии с [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] средств разработки программного обеспечения (SDK) установлен.  
  
-   доступ к документации по пакету [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK;  
  
-   опыт разработки компонентов и работы с пространствами имен модели компонентов в среде [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Дополнительные сведения см. в разделах «Component Authoring» и «Component Model Namespaces in Visual Studio» на веб-сайте msdn.microsoft.com (на английском языке).  
  
## <a name="language-and-namespace-requirements"></a>Требования к языку и пространствам имен  
 Пользовательские элементы отчета [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] полностью поддерживают платформу [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Пользовательские элементы отчета можно разрабатывать на любом языке, соответствующем платформе .NET.  
  
 Среда [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] предлагает разработчику множество средств и функций, упрощающих и ускоряющих итерационные циклы создания кода, отладки и тестирования, чтобы облегчить процесс развертывания. В пакет [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK входят компиляторы [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] и C#, а также связанные средства.  
  
-   Пользовательские элементы отчета используют **Microsoft.ReportDesigner** и <xref:Microsoft.ReportingServices.Interfaces> пространства имен. Они хранятся в сборках Microsoft.ReportingServices.Designer.DLL и Microsoft.ReportingServices.Interfaces.DLL, которые устанавливаются в составе служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
-   В компонентах времени разработки пользовательских элементов отчета необходимо реализовать интерфейсы из пространства имен <xref:System.ComponentModel> в платформе [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Пространство имен <xref:System.ComponentModel> описывается в документации по пакету [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK.  
  
> [!IMPORTANT]  
>  По умолчанию с [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] устанавливается платформа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], но не устанавливается пакет SDK для платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] . Если пакет SDK не установлен на компьютере, а в коллекцию электронной документации не входит документация по пакету SDK, ссылки на содержимое пакета SDK в этом разделе работать не будут. После установки [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK, можно добавить в документации SDK в коллекцию электронной документации и в оглавление, следуя инструкциям в разделе [Добавление или удаление документации по продукту SQL Server](http://msdn.microsoft.com/library/ef798cc8-87cf-4d60-a7bf-9e061bdd0052).  
  
## <a name="see-also"></a>См. также:  
 [Создание компонента пользовательского элемента отчета времени выполнения](../../reporting-services/custom-report-items/creating-a-custom-report-item-run-time-component.md)   
 [Создание компонента пользовательского элемента отчета времени разработки](../../reporting-services/custom-report-items/creating-a-custom-report-item-design-time-component.md)   
 [Как: развертывание пользовательского элемента отчета](../../reporting-services/custom-report-items/how-to-deploy-a-custom-report-item.md)   
 [Библиотеки классов элемента пользовательского отчета](../../reporting-services/custom-report-items/custom-report-item-class-libraries.md)  
  
  

