---
title: "Настройка брандмауэра для доступа к серверу отчетов | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 09/14/2015
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- firewall systems [Reporting Services]
- configuring servers [Reporting Services]
ms.assetid: 04dae07a-a3a4-424c-9bcb-a8000e20dc93
caps.latest.revision: 13
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 4ea69363565456fda2c1adc7d48d60c6a0bef8f7
ms.contentlocale: ru-ru
ms.lasthandoff: 06/13/2017

---
# <a name="configure-a-firewall-for-report-server-access"></a>настроить брандмауэр для доступа к серверу отчетов
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и опубликованным отчетам производится по URL-адресам, которые состоят из IP-адреса, номера порта и имени виртуального каталога. Если включен брандмауэр Windows, то порт, на который настроен сервер отчетов, скорее всего, закрыт. Обычно это выражается в том, что при обращении с удаленного клиентского компьютера к **диспетчеру отчетов** выдается пустая страница либо при запросе отчета открывается пустая веб-страница.  
  
 Открыть порт можно при помощи брандмауэра Windows на компьютере сервера отчетов. Службы Reporting Services не открывают порты автоматически, этот шаг необходимо выполнить вручную.  
  
 По умолчанию сервер отчетов слушает HTTP-запросы для порта 80. Следующие пошаговые инструкции позволяют настроить порт. Если URL-адреса сервера отчетов настроены на другой порт, при выполнении описанных ниже инструкций необходимо указывать его номер.  
  
 При обращении к реляционным базам данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на внешних компьютерах или в случае, если база данных сервера отчетов находится на внешнем экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , необходимо открыть порт 1433 и 1434 на внешнем компьютере. Дополнительные сведения о брандмауэре Windows см. в статье [Настройка брандмауэра Windows для доступа к компоненту Database Engine](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) в электронной документации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения о настройках брандмауэра Windows по умолчанию и описание портов TCP, влияющих на компоненты [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]и [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], см. в разделе [Настройка брандмауэра Windows для разрешения доступа к SQL Server](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md) электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="prerequisites"></a>Предварительные требования  
 Выполнение следующих инструкций предполагает, что создана база данных сервера отчетов, настроена учетная запись службы и URL-адреса диспетчера отчетов и веб-службы сервера отчетов. Дополнительные сведения см. в разделе [Управление сервером отчетов служб Reporting Services в собственном режиме](../../reporting-services/report-server/manage-a-reporting-services-native-mode-report-server.md).  
  
 Кроме этого, необходимо проверить доступность экземпляра сервера отчетов из веб-браузера через локальное соединение. Этот шаг необходим для проверки работоспособности установки. Прежде чем приступать к открытию портов, необходимо проверить правильность настройки установки. Чтобы выполнить этот шаг в Windows Server, потребуется также добавить сервер отчетов к доверенным сайтам. Дополнительные сведения см. в статье [Настройка сервера отчетов, работающего в собственном режиме, для локального администрирования (SSRS)](../../reporting-services/report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
## <a name="opening-ports-in-windows-firewall"></a>Открытие портов в брандмауэре Windows  
  
#### <a name="to-open-port-80"></a>Открытие порта 80  
  
1.  В меню **Пуск** выберите **Панель управления**, **Система и безопасность**и **Брандмауэр Windows**. Если на панели управления не включено представление по категориям, сразу выберите **Брандмауэр Windows**.  
  
2.  Выберите **Дополнительные настройки**.  
  
3.  Выберите **Правила для входящих подключений.**  
  
4.  Выберите **Создать правило** в окне **Действия****.**  
  
5.  Выберите **Тип правила** в разделе **Порт**.  
  
6.  Нажмите кнопку **Далее**.  
  
7.  На странице **Протокол и порты** выберите **TCP**.  
  
8.  Выберите **Указанные локальные порты** и введите значение **80**.  
  
9. Нажмите кнопку **Далее**.  
  
10. На странице **Действие** выберите **Разрешить соединение**.  
  
11. Нажмите кнопку **Далее**.  
  
12. На странице **Профиль** выберите необходимые параметры для среды.  
  
13. Нажмите кнопку **Далее**.  
  
14. На странице **Имя** введите имя**ReportServer (TCP через порт 80)**.  
  
15. Нажмите кнопку **Готово**.  
  
16. Перезагрузите компьютер.  
  
## <a name="next-steps"></a>Следующие шаги  
 После открытия порта, прежде чем удаленные пользователи смогут производить доступ к серверу отчетов, им необходимо предоставить доступ к корневой папке и на уровне сайта. Даже если порт правильно открыт, пользователи не смогут соединяться с сервером отчетов, если им не предоставлены необходимые разрешения. Дополнительные сведения см. в разделе [Предоставление пользователям доступа к серверу отчетов (диспетчер отчетов)](../../reporting-services/security/grant-user-access-to-a-report-server-report-manager.md) электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Правильность открытия порта можно также проверить, открыв диспетчер отчетов с другого компьютера. Дополнительные сведения см. в разделе [Диспетчер отчетов (службы SSRS в собственном режиме)](http://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896) электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Настройка учетной записи службы сервера отчетов (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Настройка URL-адресов сервера отчетов (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)   
 [Создание базы данных сервера отчетов (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/ssrs-report-server-create-a-report-server-database.md)   
 [Настройка учетной записи службы сервера отчетов (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Управление сервером отчетов служб Reporting Services в собственном режиме](../../reporting-services/report-server/manage-a-reporting-services-native-mode-report-server.md)  
  
  

