---
title: Привязка отчета или модели к общему источнику данных (службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- shared data sources [Reporting Services]
- data sources [Reporting Services], shared
ms.assetid: 23cc15f2-2883-48e2-bc6c-fa0ab61a2e21
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 83edc5eb7d0a79e6af7bb88253cc501cc30d0f60
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "59957790"
---
# <a name="bind-a-report-or-model-to-a-shared-data-source-ssrs"></a>Привязка отчета или модели к общему источнику данных (SSRS)
  В некоторых ситуациях, например при переносе отчета или модели с тестового сервера на рабочий, бывает необходимо сохранить файл на локальном компьютере, а затем передать его на другой сервер отчетов. При передаче отчета или модели на новый сервер необходимо повторно привязать его к общему источнику данных, находящемуся на новом сервере отчетов. Если повторную привязку отчета или модели не выполнить, они не будут работоспособны при обращении к ним с нового сервера отчетов.  
  
> [!IMPORTANT]  
>  Перед повторной привязкой отчета или модели к общему источнику данных этот источник должен уже существовать на сервере отчетов или в библиотеке SharePoint. Дополнительные сведения об источниках данных см. в статье [Создание, изменение и удаление общих источников данных (службы SSRS)](create-modify-and-delete-shared-data-sources-ssrs.md).  
  
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
  
## <a name="see-also"></a>См. также  
 [Передача файла или отчета (диспетчер отчетов)](../reports/upload-a-file-or-report-report-manager.md)   
 [Загрузка документов в библиотеку SharePoint (службы Reporting Services в режиме SharePoint)](../upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode.md)   
 [Создание общих источников данных и управление ими (службы Reporting Services в режиме интеграции с SharePoint)](../create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md)   
 [Создание, удаление или изменение общего источника данных (диспетчер отчетов)](../create-delete-or-modify-a-shared-data-source-report-manager.md)   
 [Подключения к данным, источники данных и строки подключения в службах Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [Источники данных, поддерживаемые службами Reporting Services (SSRS)](../create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
  
