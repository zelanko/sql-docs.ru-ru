---
title: Интеграция служб Reporting Services с помощью элементов управления средства просмотра отчетов | Документы Майкрософт
ms.date: 09/18/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: application-integration
ms.topic: reference
helpviewer_keywords:
- Report Viewer controls
- integrating reports [Reporting Services]
ms.assetid: 3ba47fb4-73a9-4059-89fd-329adebe94a8
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 8ffaeb12bc961256959571d18808e2869a1d7485
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62741887"
---
# <a name="integrating-reporting-services-using-report-viewer-controls"></a>Интеграция служб Reporting Services с помощью элементов управления средства просмотра отчетов
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio 2015 предусматривает два элемента управления средства просмотра отчетов для внедрения функциональных средств просмотра отчетов в приложения. К ним относятся версия для приложений на базе Windows Forms, а также версия для приложений Web Forms. Эти элементы управления предоставляют одинаковые функциональные возможности, однако каждый из них разработан с учетом особенностей соответствующей среды. Оба элемента управления обрабатывают отчеты, развернутые на сервере отчетов (режим удаленной обработки) или скопированные на компьютер, где еще не установлены службы [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (режим локальной обработки).  
  
 Элемент управления средства просмотра отчетов не включает встроенную поддержку динамической адаптации к разным устройствам с разным разрешением экрана.  
  
## <a name="remote-processing-mode"></a>Удаленный режим обработки  
 Режим удаленной обработки является предпочтительным методом просмотра отчетов, развернутых на сервере отчетов. Режим удаленной обработки предоставляет следующие преимущества.  
  
-   Удаленная обработка является оптимальным решением для выполнения отчетов, поскольку отчеты обрабатываются сервером отчетов.  
  
-   Таким образом, всю обработку выполняет сервер отчетов, поэтому запрос отчета может обрабатываться несколькими серверами отчетов в варианте с масштабированием по горизонтали или многопроцессорным сервером в варианте с масштабированием по вертикали.  
  
 Кроме того, эксплуатация отчетов в удаленном режиме позволяет воспользоваться полным набором функциональных возможностей сервера отчетов, в том числе всеми модулями подготовки к просмотру и обработки данных.  
  
> [!NOTE]  
>  Список модулей, доступных для элемента управления средства просмотра отчетов при работе в режиме удаленной обработки, зависит от выпуска служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], установленного на сервере отчетов.  
  
## <a name="local-processing-mode"></a>Локальной режим обработки  
 В режиме локальной обработки предусмотрен альтернативный метод просмотра и подготовки отчетов на тот случай, если службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не установлены. В отличие от удаленной обработки, в данном режиме элементу управления доступно лишь подмножество функциональных возможностей, предоставляемых сервером отчетов. В режиме локальной обработки обработка данных не выполняется элементом управления, а реализуется приложением, в котором размещается отчет. Но обработка отчета выполняется самим элементом управления. В режиме локальной обработки доступны только модули подготовки отчетов в форматах PDF, Excel, Word и в формате изображений.  
  
## <a name="see-also"></a>См. также:  
 [Интеграция служб Reporting Services в приложения](../../reporting-services/application-integration/integrating-reporting-services-into-applications.md)   
 [Using the WebForms ReportViewer Control](../../reporting-services/application-integration/using-the-webforms-reportviewer-control.md)  (Использование элемента управления средства просмотра отчетов WebForms)  
 [Using the WebForms ReportViewer Control](../../reporting-services/application-integration/using-the-winforms-reportviewer-control.md) (Использование элемента управления средства просмотра отчетов WinForms)  

  
  
