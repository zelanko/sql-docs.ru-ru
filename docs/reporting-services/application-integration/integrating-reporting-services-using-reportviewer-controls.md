---
title: Интеграция служб Reporting Services с помощью элементов управления ReportViewer | Документы Майкрософт
ms.date: 09/06/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: application-integration
ms.suite: pro-bi
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- ReportViewer controls
- integrating reports [Reporting Services]
ms.assetid: 3ba47fb4-73a9-4059-89fd-329adebe94a8
author: markingmyname
ms.author: maghan
ms.openlocfilehash: f121984a363a75ee22a25e515d486b4c99872983
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2018
ms.locfileid: "43265878"
---
# <a name="integrating-reporting-services-using-reportviewer-controls"></a>Интеграция служб Reporting Services с помощью элементов управления ReportViewer
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio 2015 предусматривает два элемента управления ReportViewer для внедрения функциональных средств просмотра отчетов в приложения. К ним относятся версия для приложений на базе Windows Forms, а также версия для приложений Web Forms. Эти элементы управления предоставляют одинаковые функциональные возможности, однако каждый из них разработан с учетом особенностей соответствующей среды. Оба элемента управления обрабатывают отчеты, развернутые на сервере отчетов (режим удаленной обработки) или скопированные на компьютер, где еще не установлены службы [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (режим локальной обработки).  
  
 Элемент управления ReportViewer не включает встроенную поддержку динамической адаптации к разным устройствам с разным разрешением экрана.  
  
## <a name="remote-processing-mode"></a>Удаленный режим обработки  
 Режим удаленной обработки является предпочтительным методом просмотра отчетов, развернутых на сервере отчетов. Режим удаленной обработки предоставляет следующие преимущества.  
  
-   Удаленная обработка является оптимальным решением для выполнения отчетов, поскольку отчеты обрабатываются сервером отчетов.  
  
-   Таким образом, всю обработку выполняет сервер отчетов, поэтому запрос отчета может обрабатываться несколькими серверами отчетов в варианте с масштабированием по горизонтали или многопроцессорным сервером в варианте с масштабированием по вертикали.  
  
 Кроме того, эксплуатация отчетов в удаленном режиме позволяет воспользоваться полным набором функциональных возможностей сервера отчетов, в том числе всеми модулями подготовки к просмотру и обработки данных.  
  
> [!NOTE]  
>  Список модулей, доступных для элемента управления ReportViewer при работе в режиме удаленной обработки, зависит от выпуска служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], установленного на сервере отчетов.  
  
## <a name="local-processing-mode"></a>Локальной режим обработки  
 В режиме локальной обработки предусмотрен альтернативный метод просмотра и подготовки отчетов на тот случай, если службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не установлены. В отличие от удаленной обработки, в данном режиме элементу управления доступно лишь подмножество функциональных возможностей, предоставляемых сервером отчетов. В режиме локальной обработки обработка данных не выполняется элементом управления, а реализуется приложением, в котором размещается отчет. Но обработка отчета выполняется самим элементом управления. В режиме локальной обработки доступны только модули подготовки отчетов в форматах PDF, Excel, Word и в формате изображений.  
  
## <a name="see-also"></a>См. также:  
 [Интеграция служб Reporting Services в приложения](../../reporting-services/application-integration/integrating-reporting-services-into-applications.md)   
 [Использование элемента управления WebForms ReportViewer](../../reporting-services/application-integration/using-the-webforms-reportviewer-control.md)   
 [Использование элемента управления WinForms ReportViewer](../../reporting-services/application-integration/using-the-winforms-reportviewer-control.md)  

  
  
