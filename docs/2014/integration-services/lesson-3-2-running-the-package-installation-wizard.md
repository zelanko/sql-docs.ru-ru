---
title: Шаг 2. Запуск мастера установки пакета | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f91fbb89-4626-4c47-b96d-56052dc45861
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 0fe0862438943fec36728a3c4e6c796061c86593
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62891582"
---
# <a name="step-2-running-the-package-installation-wizard"></a>Шаг 2. Запуск мастера установки пакета
  В этой задаче мастер установки пакета используется для развертывания пакетов из проекта Deployment Tutorial в экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. В таблицу sysssispackages базы данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] msdb можно установить только пакеты; файлы поддержки, включенные в пакет развертывания, будут развернуты в файловой системе.  
  
 Мастер установки пакета проводит пользователя через последовательность шагов по установке и настройке пакетов. Пакеты будут устанавливаться в экземпляр [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] на компьютере назначения (куда скопирован пакет развертывания). Будет также создана папка «C:\DeploymentTutorialInstall», в которую мастер установит файлы, не относящиеся к пакету.  
  
 На предыдущем занятии были изменены пакеты в учебнике, чтобы сконфигурировать их. С помощью мастера установки пакета будут изменены эти настройки, чтобы пакеты могли успешно выполняться в той среде, куда они установлены.  
  
### <a name="to-install-the-packages"></a>Установка пакетов  
  
1.  Найдите на компьютере назначения пакет развертывания.  
  
     Если в качестве размещения программы развертывания использовалось значение по умолчанию (bin\Deployment), пакет развертывания будет находиться в папке Deployment в проекте Deployment Tutorial.  
  
2.  В папке Deployment дважды щелкните файл манифеста, Deployment Tutorial.SSISDeploymentManifest.  
  
3.  На странице приветствия мастера установки пакетов нажмите кнопку **Далее**.  
  
4.  На странице "Развертывание пакетов служб SSIS" выберите параметр **Установить на SQL Server** , установите флажок **Проверить пакеты после установки** и нажмите кнопку **Далее**.  
  
5.  На странице "Выбор целевого сервера SQL Server" укажите **(локальный)** в поле **Имя сервера** .  
  
6.  Если экземпляр SQL Server поддерживает проверку подлинности Windows, выберите **Использовать проверку подлинности Windows**; в противном случае выберите **Использовать проверку подлинности SQL Server** и задайте имя пользователя и пароль.  
  
7.  Убедитесь в том, что снят флажок **Шифрование обеспечивается хранением на сервере** .  
  
8.  Нажмите кнопку **Далее**.  
  
9. На странице "Выбор папки для установки" нажмите кнопку **Обзор**.  
  
10. В диалоговом окне **Выбор папки** разверните **Мой компьютер** и щелкните **Локальный диск (C:)**.  
  
11. Щелкните **Создать папку** и замените имя по умолчанию для новой папки ( **Новая папка**) на **DeploymentTutorialInstall**.  
  
    > [!IMPORTANT]  
    >  На это имя ссылается одна из переменных среды конфигурации. Имя папки и ссылка должны соответствовать друг другу, иначе пакет не сможет выполняться.  
  
12. Нажмите кнопку **ОК**.  
  
13. Убедитесь в том, что на странице "Выбор папки установки" в поле "Папка" содержится **C:\DeploymentTutorialInstall** и нажмите кнопку **Далее**.  
  
14. На странице "Подтверждение установки" нажмите кнопку **Далее**.  
  
     Мастер устанавливает пакеты. После завершения установки открывается страница «Настройка пакетов».  
  
15. Убедитесь в том, что на странице "Настройка пакетов" в списке **Файл конфигурации** содержатся файлы datatransferconfig.dtsconfig и loadxmldataconfig.dtsconfig.  
  
16. В списке **Файл конфигурации** щелкните **datatransferconfig.dtsconfig**, разверните "Свойство" в столбце **Путь** поля **Конфигурации** и обновите столбец **Значение** указанными ниже значениями.  
  
    |Свойство|Значение|Обновленное значение|  
    |--------------|-----------|-------------------|  
    |\Package.Connections[Deployment Tutorial Log].Properties[ConnectionString]|C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Completed Packages\Deployment Tutorial Log|C:\DeploymentTutorialInstall\Deployment Tutorial Log|  
    |\Package.Connections[NewCustomers].Properties[ConnectionString]|C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Sample Data\NewCustomers.txt|C:\DeploymentTutorialInstall\NewCustomers.txt|  
  
17. В списке **Файл конфигурации** щелкните loadxmldataconfig.dtsconfig, разверните "Свойство" в столбце **Путь** поля **Конфигурации** и обновите столбец **Значение** указанными ниже значениями.  
  
    |Свойство|Значение|Обновленное значение|  
    |--------------|-----------|-------------------|  
    |\Package.LoadXMLData.Properties[[XML Source].[XMLData]]|C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Sample Data\orders.xml|C:\DeploymentTutorialInstall\orders.xml|  
    |\Package.LoadXMLData.Properties[[XML Source].[XMLSchemaDefinition]]|C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Sample Data\orders.xsd|C:\DeploymentTutorialInstall\orders.xsd|  
  
18. На странице "Проверка пакета" просмотрите результаты проверки каждого установленного пакета и нажмите кнопку **Далее**.  
  
     Поскольку значения переменных среды на целевом компьютере отличаются от значений переменных среды на компьютере разработчика, на странице проверки пакетов отображается несколько предупреждений. Следует ожидать следующих предупреждений.  
  
    -   Файл конфигурации: «C:\DeploymentTutorial\DataTransferConfig.dtsConfig» является недопустимым. Проверьте имя файла конфигурации.  
  
    -   Не удалось загрузить по крайней мере одну запись конфигурации в пакете. Проверьте записи конфигурации и предыдущие предупреждения, чтобы увидеть, какая из них ошибочна.  
  
    -   Файл конфигурации: «C:\DeploymentTutorial\LoadXMLDataConfig.dtsConfig недопустим. Проверьте имя файла конфигурации.  
  
    -   Не удалось загрузить по крайней мере одну запись конфигурации в пакете. Проверьте записи конфигурации и предыдущие предупреждения, чтобы увидеть, какая из них ошибочна.  
  
     Эти предупреждения не влияют на установку пакета.  
  
     Если не установлен флажок **Проверить пакеты после установки** на странице "Развертывание пакетов служб SSIS", то страницы "Проверка пакетов" не открываются и мастер не выводит сведения о проверке.  
  
19. На странице "Завершение работы мастера установки пакета" прочитайте сводку результатов установки и нажмите кнопку **Готово**.  
  
    > [!NOTE]  
    >  Для проверки пакетов создается временный файл журнала. Этот файл не используется при выполнении пакета.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Шаг 3. Тестирование развернутых пакетов.](../integration-services/lesson-3-3-testing-the-deployed-packages.md)  
  
![Значок служб Integration Services (маленький)](media/dts-16.gif "значок служб Integration Services (маленький)")**оставаться до даты со службами Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетите страницу служб Integration Services на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также  
 [Службы Integration Services (службы SSIS)](service/integration-services-service-ssis-service.md)   
 [Управление службой Integration Services](../../2014/integration-services/manage-the-integration-services-service.md)  
  
  
