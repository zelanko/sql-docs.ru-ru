---
title: Учетные записи домена, необходимые для фермы SharePoint (советник по переходу) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 90cd6d3e-a271-4cb8-81f2-fc555b2d3cab
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: c4079ea4213d7ecbec0165c32c82b3449bbb5aee
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952507"
---
# <a name="domain-accounts-required-for-sharepoint-farm-upgrade-advisor"></a>Для фермы SharePoint требуются учетные записи домена (советник по переходу)
  Продукты SharePoint, которые настроены для среды ферм, требуют использования учетных записей домена.  
  
||  
|-|  
|режим **[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint.|  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssRS](../../includes/ssrs.md)]  
  
### <a name="description"></a>Описание  
 Продукты SharePoint, настроенные для среды ферм, требуют использования учетных записей домена для служб и подключений к базе данных. Это касается учетной записи, заданной в качестве учетной записи службы Reporting Services.  
  
 Страницы центра администрирования SharePoint 2010 — единственное место, где можно увидеть ошибки, если для службы Reporting Services не используется учетная запись пользователя домена. При попытке настройки интеграции служб Reporting Services будет выдано сообщение об ошибке следующего содержания:  
  
 «Сервер отчетов запущен от имени встроенной учетной записи NT AUTHORITY\NETWORK SERVICE, которая не поддерживается установкой фермы SharePoint. Необходимо повторно настроить службу сервера отчетов для запуска от имени учетной записи пользователя домена».  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Для [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и предыдущих версий используйте диспетчер конфигурации служб Reporting Services, чтобы изменить учетную запись, назначенную в качестве учетной записи службы сервера отчетов.  
  
#### <a name="to-change-the-service-account-from-configuration-manager"></a>Изменение учетной записи службы, используйте диспетчер конфигурации  
  
1.  В меню **Пуск** выберите **все программы**, а затем щелкните **Microsoft SQL Server 2008 R2**.  
  
2.  Выберите **средства настройки**и щелкните **Диспетчер конфигурации служб Reporting Services**.  
  
3.  В Configuration Manager выберите вкладку **учетная запись службы** .  
  
4.  Выберите **использовать другую учетную запись** и введите учетные данные для учетной записи домена.  
  
5.  Нажмите кнопку **Применить**.  
  
## <a name="see-also"></a>См. также  
 [Настройка учетной записи службы сервера отчетов (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)  
  
  
