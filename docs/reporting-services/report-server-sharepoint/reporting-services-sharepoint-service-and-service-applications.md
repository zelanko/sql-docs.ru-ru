---
title: Служба и приложения службы Reporting Services в SharePoint | Документы Майкрософт
ms.custom: ''
ms.date: 09/25/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: report-server-sharepoint
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: d1db1758c979ae3582d562c47690e12af72171cc
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="reporting-services-sharepoint-service-and-service-applications"></a>Служба и приложения службы Reporting Services в SharePoint

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

  Службы Reporting Services в режиме интеграции с SharePoint спроектированы на основе архитектуры службы SharePoint и используют службу SharePoint, а также одно или несколько приложений службы. Создание приложения службы открывает доступ к службе и формирует базу данных приложения службы. Можно создать несколько приложений службы Reporting Services, однако для большинства сценариев развертывания достаточно одного приложения службы.  

> [!NOTE]
> Интеграция служб Reporting Services с SharePoint больше не доступна после выхода SQL Server 2016.
  
## <a name="creating-a-reporting-services-service-application"></a>Создание приложения службы Reporting Services

 Для создания приложений служб Reporting Services можно использовать центр администрирования SharePoint или скрипты PowerShell. Дополнительные сведения об использовании центра администрирования SharePoint см. в разделе "Создание приложения службы Reporting Services" статьи [Установка служб Reporting Services в режиме интеграции с SharePoint для SharePoint 2010](http://msdn.microsoft.com/47efa72e-1735-4387-8485-f8994fb08c8c). В подразделе PowerShell этого раздела приведен пример скрипта PowerShell для создания приложений службы.  
  
## <a name="modify-the-associations-of-the-service-application-with-a-proxy-group"></a>Изменение взаимосвязей приложения службы с использованием группы прокси

 Новая страница для создания приложения служб содержит раздел **Связь с веб-приложением**. Данный раздел позволяет связать приложение службы во время его создания. Для изменения взаимосвязи и установки пользовательской конфигурации в приложении службы выполните следующие шаги. Можно использовать тот же общий процесс, но вместо изменения взаимосвязи приложения службы с пользовательской группой добавить учетную запись-посредник в группу по умолчанию.  
  
1.  В центре администрирования SharePoint в разделе «Управление приложениями» выберите пункт **Настройка связей приложения службы**.  
  
2.  На странице «Связи между приложениями служб» измените представление для **Приложения служб**.  
  
3.  Найдите и щелкните имя нового приложения службы Reporting Services. Можно щелкнуть группу прокси-серверов приложения **по умолчанию** для добавления прокси-сервера в группу по умолчанию.  
  
4.  В списке **Изменить следующую группу соединений** выберите **Пользовательская**.  
  
5.  Установите флажок для учетной записи-посредника и нажмите кнопку **ОК**.  
  
## <a name="edit-service-application-properties"></a>Изменение свойств приложения службы

 Для изменения свойств можно повторно открыть страницу свойств приложения службы.  
  
1.  В центре администрирования SharePoint, в разделе «Управление приложениями», выберите **Управление приложениями служб**.  
  
2.  Выберите приложение службы, щелкнув столбец типа, чтобы выделить всю строку. Если щелкнуть имя приложения, откроется страница «Параметры управления» для службы, а не свойства приложения службы.  
  
3.  На ленте «Приложения службы» нажмите кнопку **Свойства**.  
  
## <a name="create-a-reporting-services-service-application-using-powershell"></a>Создание приложения службы Reporting Services с помощью PowerShell

 Создать приложение службы и прокси-сервер можно с помощью PowerShell. В следующем примере предполагается, что пул приложения, который необходимо настроить для использования приложения службы, известен вам.  
  
1.  Добавьте объект пула приложений, соответствующий имени пула приложений, в переменную, передаваемую в новое действие.  
  
    ```  
    $appPoolName = get-spserviceapplicationpool “<application pool name>”  
    ```  
  
2.  Создайте приложение службы с указанным именем и именем пула приложений.  
  
    ```  
    New-SPRSServiceApplication –Name ‘MyServiceApplication’ –ApplicationPool $appPoolName –DatabaseName ‘MyServiceApplicationDatabase’ –DatabaseServer ‘<Server Name>’  
    ```  
  
3.  Получите новый объект приложения службы и передайте объект в канал командлета создания новой учетной записи-посредника.  
  
    ```  
    Get-SPRSServiceApplication –name MyServiceApplication | New-SPRSServiceApplicationProxy “MyServiceApplicationProxy”  
    ```  
  
## <a name="related-tasks"></a>Связанные задачи
  
|Задача|Ссылка|  
|----------|----------|  
|Управление параметрами приложения службы.|[Управление приложением службы SharePoint — Reporting Services](../../reporting-services/report-server-sharepoint/manage-a-reporting-services-sharepoint-service-application.md)|  
|Резервное копирование и восстановление приложения службы и связанных компонентов, таких как ключи шифрования и прокси-серверы.|[Резервное копирование и восстановление приложения службы SharePoint — Reporting Services](../../reporting-services/report-server-sharepoint/backup-and-restore-reporting-services-sharepoint-service-applications.md)|  

Остались вопросы? [Посетите форум служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231).
