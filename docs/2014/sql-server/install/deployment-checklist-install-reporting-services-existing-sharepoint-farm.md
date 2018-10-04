---
title: 'Контрольный список развертывания: Установка служб Reporting Services в существующей ферме SharePoint | Документация Майкрософт'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 436b4c3d-3f2f-464a-be7e-5c051d9ffb8f
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 6bf76bca14e7ae1dbf96cfd9c0123bad42e31a94
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48220524"
---
# <a name="deployment-checklist-install-reporting-services-into-an-existing-sharepoint-farm"></a>Контрольный список развертывания: установка служб Reporting Services в существующей ферме SharePoint
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Серверы отчетов SharePoint можно установить в новую ферму SharePoint или в существующую ферму SharePoint. В этом разделе описаны возможные сценарии и рекомендации по установке [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в новой и существующей ферме SharePoint.  
  
## <a name="prerequisites"></a>предварительные требования  
 Прежде чем запустить программу установки, ознакомьтесь со следующими моментами.  
  
|Шаг|Ссылка|  
|----------|----------|  
|Создайте или определите учетные записи, используемые при развертывании сервера отчетов. Необходима учетная запись службы сервера отчетов, а также учетные данные для соединения с базой данных сервера отчетов||  
|Выберите экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для размещения базы данных сервера отчетов. Можно использовать локальный или удаленный экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Необходимо выбрать экземпляр на том компьютере, который имеет достаточный объем памяти для размещения отчетов.||  
|(Необязательно.) Выясните название SMTP-сервера или шлюза, предоставляющего услуги электронной почты для организации, если в подписках планируется использование электронной почты сервера отчетов|[Настройка сервера отчетов для доставки электронной почты &#40;диспетчер конфигурации служб SSRS&#41;](../../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)|  
|Примечание: Если вы обновляете компьютер из предыдущего выпуска CTP [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и вы пользовательскими изменениями в файлах конфигурации, необходимо будет внесения изменений в файлах конфигурации после обновления до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Затрагиваются файлы **web.config** и **client.config**.||  
  
## <a name="installation-scenarios"></a>Сценарии установки  
 В следующей таблице описаны возможные сценарии, при установке [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в новой и существующей ферме SharePoint. Локальный режим позволяет подготавливать локально из библиотеки документов SharePoint без интеграции с отчеты [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] сервера отчетов. Надстройка служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для продуктов SharePoint является обязательной в отличие от сервера отчетов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Дополнительные сведения о локальном режиме см. в разделе [Отчеты, созданные в локальном Подключенном режиме в средстве просмотра отчетов &#40;служб Reporting Services в режиме интеграции с SharePoint&#41; ](../../../2014/reporting-services/local-vs-connected-mode-report-viewer-reporting-services-sharepoint-mode.md) и [где найти надстройку служб Reporting Services для продуктов SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).  
  
|Начальная конфигурация|Рабочий процесс|Конечная конфигурация|Комментарии|  
|----------------------------|--------------|--------------------------|--------------|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] в локальном режиме|Установка|Подключенный режим [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].||  
|Подключенный режим [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] или [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|Обновление на месте|Подключенный режим [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].||  
|Подключенный режим [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] или [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|Миграция|Подключенный режим [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].||  
  
## <a name="installation-and-in-place-upgrade-checklist"></a>Контрольный список действий при установке и обновлении на месте  
 В следующей таблице приведено краткое описание шагов, средств и сведений, которые необходимо изучить и использовать при установке.  
  
|Шаг|Ссылка|  
|----------|----------|  
|**Установкой и первоначальной конфигурацией**||  
|Установите надстройку SharePoint на всех компьютерах клиентского веб-интерфейса.|[Добавление дополнительного клиентского веб-интерфейса служб Reporting Services в ферме](../../reporting-services/install-windows/add-an-additional-reporting-services-web-front-end-to-a-farm.md)|  
|Установка служб SQL Server [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Reporting Services и компонента Database Engine.|[Установка служб Reporting Services в режиме SharePoint для SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)|  
|Создайте по крайней мере одно приложение службы SSRS и настройте взаимосвязь с приложением службы.|См. в разделе «Приложение службы» в [установить службы Reporting Services в режиме SharePoint для SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)|  
|**Дополнительная настройка**||  
|Добавьте типы содержимого служб SSRS в библиотеку документов.|[Добавление типов содержимого сервера отчетов в библиотеку &#40;режим интеграции служб Reporting Services в SharePoint&#41;](../../../2014/reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md)|  
|Подготовьте к работе агент SQL Server|[Подготовка подписок и предупреждений для приложений служб SSRS](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md)|  
|Настройте параметры электронной почты для приложения службы|[Настройка электронной почты для приложения служб Reporting Services &#40;SharePoint 2010 и SharePoint 2013&#41;](../../reporting-services/install-windows/configure-e-mail-for-a-reporting-services-service-application.md)|  
|Настройте службу Claims to Windows Token Service (c2WTS)|[Служба claims to Windows Token Service &#40;C2WTS&#41; и службы Reporting Services](../../../2014/sql-server/install/claims-to-windows-token-service-c2wts-and-reporting-services.md)|  
  
## <a name="migration-checklist"></a>Контрольный список действий по миграции  
 Далее приведен список основных шагов по миграции из существующей установки в новую установку.  
  
|Шаг|Ссылка|  
|----------|----------|  
|Установите и настройте новый сервер. Это включает следующие действия.<br /><br /> Средство подготовки продуктов SharePoint<br /><br /> Продукт SharePoint 2010<br /><br /> SharePoint 2010 с пакетом обновления 1 (SP1)<br /><br /> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint<br /><br /> Надстройка служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для продуктов SharePoint 2010|[Установка служб Reporting Services в режиме SharePoint для SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)|  
|Создайте по крайней мере одно приложение службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]||  
|Резервное копирование [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] баз данных||  
|Резервное копирование [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ключей шифрования||  
|Восстановите базу данных и ключи шифрования служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]||  
|Сопоставьте все веб-приложения в новое [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]приложений служб|Новая установка **теперь функциональна**|  
|Удалите URL-адрес интеграции на старом сервере.|В центре администрирования SharePoint на странице **Общие параметры приложения** выберите **Интеграция служб Reporting Services**.|  
|При желании удалите службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] из старой установки.||  
  
## <a name="next-steps"></a>Следующие шаги  
  
## <a name="see-also"></a>См. также  
 [Установку в режиме интеграции с SharePoint служб Reporting Services &#40;SharePoint 2010 и SharePoint 2013&#41;](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md)   
 [Руководство по использованию компонентов бизнес-Аналитики SQL Server в ферме SharePoint 2010](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)   
 [Поддерживаемые сочетания SharePoint и компонентов служб Reporting Services и надстройки &#40;SQL Server 2014&#41;](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md)  
  
  
