---
title: Предварительные условия для использования учебников (построитель отчетов) | Документы Майкрософт
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b8346a6-f4f4-4ad3-bc98-8f2be342ef2d
caps.latest.revision: 8
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 5326d5e91521e90f7596e3dd0647cb273078fd82
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194196"
---
# <a name="prerequisites-for-tutorials-report-builder"></a>Предварительные условия для использования учебников (построитель отчетов)
  При использовании учебников по построителю отчетов предполагается возможность просмотра и сохранения отчетов на сервере отчетов или сайте SharePoint, интегрированном с сервером отчетов. Во всех учебниках для данных используются запросы, которые необходимо обработать с помощью экземпляра [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
 Если нет доступа к серверу отчетов, сайту или источнику данных, изучить работу с построителем отчетов можно путем построения отчета вне сети. См. раздел [Учебник. Создание стандартного отчета с диаграммой в режиме "вне сети" (построитель отчетов)](report-builder/tutorial-create-a-quick-chart-report-offline-report-builder.md).  
  
## <a name="requirements"></a>Требования  
 Чтобы завершить учебники по построителю отчетов, должны быть выполнены следующие условия.  
  
-   Доступ к построителю отчетов [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] . Построитель отчетов можно запустить с помощью изолированной версии построителя отчетов или версии ClickOnce, которая доступна из диспетчера отчетов или с сайта SharePoint. Для версии ClickOnce отличается только первый шаг — открытие построителя отчетов.  
  
     Чтобы использовать диспетчер отчетов, откройте диспетчер отчетов и нажмите кнопку **построитель**. По умолчанию для диспетчера отчетов URL-адрес — http://\<*servername*> / reports.  
  
     Чтобы начать работу с сайтом SharePoint, перейдите на сайт, щелкните вкладку «Документы», выберите «Создать документ» и в раскрывающемся списке выберите «Отчет построителя отчетов», Например, http://\<имя_сервера >/узлы/mySite/reports. Администратор сайта SharePoint должен включить функцию «Отчет построителя отчетов» для всех библиотек документов.  
  
-   URL-адрес [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] сервера или сайта SharePoint, интегрированном с [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] сервера отчетов. Необходимы следующие разрешения: на сохранение и просмотр отчетов, общих источников данных, общих наборов данных, элементов отчетов и моделей. По умолчанию для сервера отчетов, URL-адрес — http://\<имя_сервера > / reportserver. По умолчанию URL-адрес сайта SharePoint является http://\<имя_узла > или http://\<сервера > / site.  
  
-   Имя [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] экземпляра и учетные данные, необходимые для доступа только для чтения к любой базе данных. Запросы набора данных в учебниках используют статические данные, но все запросы должны обрабатываться экземпляром [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] для возвращения метаданных, необходимых для набора данных отчета. Например, следующая строка подключения определяет только сервер: `data source=<servername>`. У вас должны быть права на доступ к базе данных по умолчанию, назначенной вам системным администратором, который предоставляет разрешения на доступ к серверу. Также можно указать базу данных, как показано в следующей строке подключения: `data source=<servername>;initial catalog=<database>`.  
  
-   Для работы с учебником, включающим карту, сервер отчетов необходимо настроить для поддержки мозаичного фона Bing Map. Дополнительные сведения см. в разделе [план поддержки отчетов карты](plan-for-map-report-support.md) в [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] документации в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [электронной документации по](http://go.microsoft.com/fwlink/?LinkId=154888) на сайте msdn.microsoft.com.  
  
-   Учебник, [учебник: создание детализированных и Main отчетов &#40;построитель&#41;](tutorial-creating-drillthrough-and-main-reports-report-builder.md), используется демонстрационный набор данных Contoso business intelligence. Этот набор включает хранилище данных ContosoDW и базу данных оперативной аналитической обработки (OLAP) Contoso_Retail. Создаваемые в данном учебнике отчеты извлекают данные из куба Contoso Sales. Базу данных OLAP Contoso_Retail можно скачать в [Центре загрузки Майкрософт](http://go.microsoft.com/fwlink/?LinkID=191575). Необходимо скачать только файл ContosoBIdemoABF.exe. Он содержит базу данных OLAP.  
  
     Второй файл, ContosoBIdemoBAK.exe, относится к хранилищу данных ContosoDW, которое не используется в данном учебнике.  
  
     На веб-сайте приведены инструкции по извлечению и восстановлению файла резервной копии ContosoRetail.abf в базу данных Contoso_Retail OLAP.  
  
     Необходимо иметь доступ к экземпляру служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], где будет установлена база данных OLAP.  
  
 Администратор сервера отчетов может предоставить необходимые разрешения на сервере отчетов, настроить [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] расположения папок и настроить параметры по умолчанию для построителя отчетов. Дополнительные сведения см. в разделе [установка, удаление и поддержка построителя отчетов](install-uninstall-and-report-builder-support.md).  
  
## <a name="see-also"></a>См. также  
 [Учебники по &#40;построитель отчетов&#41;](report-builder-tutorials.md)  
  
  