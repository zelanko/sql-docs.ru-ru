---
title: "Привязка отчета или модели к общему источнику данных (SSRS) | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shared data sources [Reporting Services]
- data sources [Reporting Services], shared
ms.assetid: 23cc15f2-2883-48e2-bc6c-fa0ab61a2e21
caps.latest.revision: 11
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 50893ee7140f33086d432fdc00f660f6371fe282
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="bind-a-report-or-model-to-a-shared-data-source-ssrs"></a>Привязка отчета или модели к общему источнику данных (SSRS)
  В некоторых ситуациях, например при переносе отчета или модели с тестового сервера на рабочий, бывает необходимо сохранить файл на локальном компьютере, а затем передать его на другой сервер отчетов. При передаче отчета или модели на новый сервер необходимо повторно привязать его к общему источнику данных, находящемуся на новом сервере отчетов. Если повторную привязку отчета или модели не выполнить, они не будут работоспособны при обращении к ним с нового сервера отчетов.  
  
> [!IMPORTANT]  
>  Перед повторной привязкой отчета или модели к общему источнику данных этот источник должен уже существовать на сервере отчетов или в библиотеке SharePoint. Дополнительные сведения об источниках данных см. в статье [Создание, изменение и удаление общих источников данных (службы SSRS)](../../reporting-services/report-data/create-modify-and-delete-shared-data-sources-ssrs.md).  
  
### <a name="to-bind-a-report-or-model-to-a-shared-data-source-on-a-report-server-running-in-native-mode"></a>Привязка отчета или модели к общему источнику данных на сервере отчетов, работающем в собственном режиме  
  
1.  Щелкните имя отчета или модели, передаваемых на сервер, в **диспетчере отчетов**.  
  
     Откроется вкладка «Свойства».  
  
2.  Щелкните **Источники данных**.  
  
3.  Нажмите кнопку **Обзор**и перейдите к источнику данных, с которым необходимо связать отчет или модель.  
  
4.  Выберите источник данных и нажмите кнопку **ОК**.  
  
5.  Нажмите кнопку **Применить**.  
  
     Теперь отчет или модель привязаны к выбранному источнику данных.  
  
### <a name="to-bind-a-report-or-model-to-a-shared-data-source-on-a-report-server-running-in-sharepoint-integrated-mode"></a>Привязка отчета или модели к общему источнику данных на сервере отчетов, работающем в режиме интеграции с SharePoint  
  
1.  Если библиотека еще не открыта, щелкните ее имя на панели «Быстрый запуск». Если имя библиотеки не отображается, щелкните **Просмотреть содержимое всего сайта**и выберите имя библиотеки.  
  
2.  Укажите отчет или модель и щелкните стрелку вниз.  
  
3.  Щелкните **Управление источниками данных**.  
  
4.  Щелкните **источник_данных_1**.  
  
5.  Убедитесь, что в области **Тип соединения** выбран вариант **Общий источник данных** .  
  
6.  В области **Связь с источником данных** нажмите кнопку с многоточием (...).  
  
7.  Найдите источник данных, который необходимо использовать.  
  
8.  Выберите источник данных и нажмите кнопку **ОК**.  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
10. Щелкните **Закрыть**.  
  
## <a name="see-also"></a>См. также раздел  
 [Передача файла или отчета (диспетчер отчетов)](../../reporting-services/reports/upload-a-file-or-report-report-manager.md)   
 [Загрузка документов в библиотеку SharePoint (службы Reporting Services в режиме SharePoint)](../../reporting-services/report-server-sharepoint/upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode.md)   
 [Создание общих источников данных и управление ими (службы Reporting Services в режиме интеграции с SharePoint)](http://msdn.microsoft.com/library/2d3428e4-a810-4e66-a287-ff18e57fad76)   
 [Создание, удаление или изменение общего источника данных (диспетчер отчетов)](http://msdn.microsoft.com/library/cd7bace3-f8ec-4ee3-8a9f-2f217cdca9f2)   
 [Подключения к данным, источники данных и строки подключения (построитель отчетов и службы SSRS)](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)   
 [Источники данных, поддерживаемые службами Reporting Services (SSRS)](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md)  
  
  
