---
title: Доступ к веб-службы сервера отчетов, с помощью Visual Basic или Visual C# (учебник по службам SSRS) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- walkthroughs [Reporting Services]
- Reporting Services, Web service
- Web service [Reporting Services], tutorials
ms.assetid: cf688163-4ac0-475b-b6dd-6f2f05b553c6
caps.latest.revision: 45
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 7fc7e1ab0e855bd9ddd208b295cf3a10d44dfce7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36094689"
---
# <a name="accessing-the-report-server-web-service-using-visual-basic-or-visual-c-ssrs-tutorial"></a>Доступ к веб-службе сервера отчетов на языке Visual Basic или Visual C# (учебник по службам SSAS)
  В руководстве ниже показано, как получить доступ к серверу веб-службы отчетов из приложения, созданного с [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] или [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[csprcs](../includes/csprcs-md.md)].  
  
## <a name="what-you-will-learn"></a>Обзор учебника  
 В ходе работы с этим учебником предстоит выполнить следующие действия:  
  
-   Создайте клиентское приложение, использующее [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] шаблон проекта консольного приложения.  
  
-   Добавить веб-ссылку на веб-службу сервера отчетов.  
  
-   Написать код для доступа к этой веб-службе.  
  
-   Выполнить созданное приложение командной строки в режиме отладки.  
  
## <a name="requirements"></a>Требования  
 Для работы с учебником необходимо наличие следующих компонентов.  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] или аналогичное [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-средство разработки, совместимое.  
  
-   Необходимые разрешения для доступа к веб-службе сервера отчетов [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] на компьютере, на котором размещен сервер отчетов.  
  
-   Отчет, установленный на сервере отчетов. Этот учебник основывается на образце отчета Company Sales. Дополнительные сведения об образцах отчетов см. в разделе [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
> [!NOTE]  
>  Образцы не устанавливаются автоматически в процессе установки, но их можно установить в любое время. Сведения об образцах см. в разделе [SQL Server Product Samples](http://go.microsoft.com/fwlink/?LinkId=182887).  
  
 **Предполагаемое время для выполнения заданий учебника:** 60 минут  
  
## <a name="tasks"></a>Задания  
 [Урок 1. Создание клиентского проекта веб-службы](../../2014/tutorials/lesson-1-creating-the-web-service-client-project.md)  
  
 [Урок 2. Добавление веб-ссылки](../../2014/tutorials/lesson-2-adding-a-web-reference.md)  
  
 [Урок 3. Доступ к веб-службе](../../2014/tutorials/lesson-3-accessing-the-web-service.md)  
  
 [Урок 4: Запуск приложения &#40;VB VC&#35;&#41;](../../2014/tutorials/lesson-4-running-the-application-vb-vcsharp.md)  
  
  