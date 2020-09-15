---
description: Добавление дополнительного клиентского веб-интерфейса служб Reporting Services в ферме
title: Добавление дополнительного клиентского веб-интерфейса служб Reporting Services в ферму | Документы Майкрософт
ms.date: 05/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint
ms.topic: conceptual
ms.assetid: d7a11bda-ae26-49ac-b071-37d83cae5afe
author: maggiesMSFT
ms.author: maggies
monikerRange: '>=sql-server-2016 <=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: dc2b1eaee352b34333be5a166168161194e1f03d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88418630"
---
# <a name="add-an-additional-reporting-services-web-front-end-to-a-farm"></a>Добавление дополнительного клиентского веб-интерфейса служб Reporting Services в ферме
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме совместимости с SharePoint включают компоненты, необходимые для работы серверов приложений и клиентского веб-интерфейса. Этот раздел посвящен установке компонентов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , необходимых для сервера WFE, включая страницы приложений, используемых такими компонентами служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , как подписки, предупреждения и [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]. Первичная установка [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] необходима WFE для установки надстройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для продуктов SharePoint 2016.  
  
## <a name="prerequisites"></a>Предварительные условия  
  
-   Для запуска программы установки SQL Server необходимо быть локальным администратором.  
  
-   Компьютер должен быть присоединен к домену.  
  
-   Необходимо знать имя существующего сервера базы данных, на котором размещены базы данных конфигурации и содержимого SharePoint.  
  
-   Сервер базы данных должен быть настроен для установления удаленных соединений с базой данных.  В противном случае будет невозможно подключить новый сервер к ферме, так как он не сможет соединиться с базами данных конфигурации SharePoint.  
  
-   На новом сервере должна быть установлена та же версия SharePoint, что и на текущих работающих серверах фермы. Например, если в ферме уже установлен SharePoint 2013 с пакетом обновления 1 (SP1), то на новом сервере также нужно установить пакет обновления 1 (SP1), прежде чем можно будет присоединить его к ферме.  
  
## <a name="steps"></a>Шаги  
 Шаги, приведенные в этом разделе, предполагают, что установкой и настройкой сервера занимается администратор фермы SharePoint. На схеме показана типичная трехуровневая среда. Пронумерованные элементы описаны ниже.  
  
-   (1) Несколько серверов клиентского веб-интерфейса (WFE). Для серверов WFE требуется надстройка служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для SharePoint 2010. Чтобы добавить второй сервер приложений на этот уровень, выполните следующие шаги.  
  
-   (2) Два сервера приложений, на которых запущены службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и веб-сайты, например центр администрирования.  
  
-   (3) Два сервера базы данных SQL Server.  
  
-   (4) Представляет программное или решение для оборудования по распределению сетевой нагрузки (NLB)  
  
 ![Добавление служб SSRS в новый внешний веб-интерфейс SharePoint](../../reporting-services/install-windows/media/rs-sharepointscale-wfe.gif "Добавление служб SSRS в новый внешний веб-интерфейс SharePoint")  
  
 Следующие шаги предполагают, что установкой и настройкой сервера занимается администратор.  
  
|Шаг|Описание и ссылка|  
|----------|--------------------------|  
|Добавление сервера SharePoint в ферму.|Для развертывания еще одного приложения служб Reporting Services потребуется установить SharePoint.<br/><br/>Инструкции для SharePoint 2013 см. в разделе [Добавление сервера SharePoint в ферму в SharePoint Server 2013](https://technet.microsoft.com/library/cc261752(v=office.15).aspx).<br/><br/>Инструкции для SharePoint 2016 см. в разделе [Добавление сервера SharePoint в ферму в SharePoint Server 2016](https://technet.microsoft.com/library/cc261752(v=office.16).aspx).|  
|Установите надстройку служб Microsoft SQL Server Reporting Services для продуктов SharePoint 2016.|Существуют специальные методы установки надстройки. Следующие шаги предусматривают использование мастера установки SQL Server. Дополнительные сведения об установке надстройки см. в разделе [Установка или удаление надстройки служб Reporting Services для SharePoint](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).<br /><br /> 1) Запустите установку SQL Server.<br /><br /> 2) На странице **Роль установки** выберите **Установка компонентов SQL Server**.<br /><br /> 3) На странице **Выбор компонентов** выберите **Надстройка служб Reporting Services для продуктов SharePoint**.<br /><br /> 4) Нажмите кнопку **Далее** на нескольких следующих страницах, чтобы завершить выбор параметров установки.<br /><br/>Дополнительные сведения об установке [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] см. в руководстве по [установке сервера отчетов в режиме интеграции с SharePoint](install-the-first-report-server-in-sharepoint-mode.md).|  
|Убедитесь, что новый сервер находится в рабочем состоянии.|1) В центре администрирования SharePoint выберите пункт **Управление серверами на ферме** в группе **Параметры системы** .<br /><br /> 2) Убедитесь, что новый сервер присутствует в списке.|  
|Обновите решение NLB.|В случае необходимости обновите программную или аппаратную среду распределения сетевой нагрузки, включив в нее новый сервер.|  

## <a name="next-steps"></a>Дальнейшие действия

[Добавление сервера SharePoint в ферму в SharePoint Server 2016](https://technet.microsoft.com/library/cc261752(v=office.16).aspx)  
[Добавление сервера SharePoint в ферму в SharePoint Server 2013](https://technet.microsoft.com/library/cc261752(v=office.15).aspx)

Остались вопросы? [Посетите форум служб Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
