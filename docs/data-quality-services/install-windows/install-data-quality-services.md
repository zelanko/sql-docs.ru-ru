---
title: Установка служб Data Quality Services | Документы Майкрософт
ms.custom: ''
ms.date: 09/11/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 486e4216-a946-4c6e-828c-61bc905f7ec1
author: lrtoyou1223
ms.author: lle
manager: jroth
ms.openlocfilehash: f709a2a58b6dd6f18c992a79c94ad63bdd8f0ef6
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66776464"
---
# <a name="install-data-quality-services"></a>Установка служб Data Quality Services

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  [!INCLUDE[ssDQSnoversionLong](../../includes/ssdqsnoversionlong-md.md)] (DQS) содержит два компонента: **[!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]** и **[!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]** .  
  
|Компонент DQS|Описание|  
|-------------------|-----------------|  
|[!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]|[!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] устанавливается поверх компонента [!INCLUDE[ssNoversion](../../includes/ssNoVersion-md.md)] компонент Database Engine и включает три базы данных: DQS_MAIN, DQS_PROJECTS и DQS_STAGING_DATA. База данных DQS_MAIN содержит хранимые процедуры DQS, ядро DQS и опубликованные базы знаний. База данных DQS_PROJECTS содержит сведения о проекте служб DQS. DQS_STAGING_DATA представляет собой промежуточную область для копирования источника данных с целью выполнения операций DQS и последующего экспорта обработанных данных.|  
|[!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]|[!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)] — это автономное приложение, которое позволяет подключаться к [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]и имеет наглядный графический пользовательский интерфейс, используемый в операциях обеспечения качества данных и выполнения других административных задач служб DQS.|  
  
> [!IMPORTANT]  
>  Помимо этих двух компонентов DQS 2 также можно:  
>   
>  Используйте преобразование «Очистка DQS» из служб Integration Services, которое выполняет очистку данных в процессе обработки пакетов служб Integration Services. Этот компонент устанавливается автоматически при установке служб Integration Services. Сведения об установке служб Integration Services см. в статье [Установка служб Integration Services](../../integration-services/install-windows/install-integration-services.md).  
>   
>  Включите интеграцию служб DQS в службах Master Data Services, чтобы использовать функции сопоставления служб DQS в надстройке служб Master Data Services для Excel. Дополнительные сведения см. в разделе [Включение интеграции служб Data Quality Services со службами Master Data Services](../../master-data-services/install-windows/enable-data-quality-services-integration-with-master-data-services.md).  
  
 Установка DQS представляет собой процесс из трех частей.  
  
-   [Предварительная подготовка](#PreInstallationTasks). Проверьте системные требования перед установкой DQS.  
  
-   [Задачи по установке служб Data Quality Services](#DQSInstallation). Установите DQS с помощью программы установки SQL Server.  
  
-   [Действия после установки](#PostInstallationTasks). Выполните следующие задачи после окончания работы программы установки SQL Server для завершения установки DQS.  
  
> [!NOTE]  
>  Этот раздел не содержит инструкций по запуску программы установки из командной строки. Дополнительные сведения о параметрах командной строки для установки [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] и клиента см. в разделе [Параметры компонентов](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md#Feature) статьи [Установка SQL Server из командной строки](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).  
  
##  <a name="PreInstallationTasks"></a> Предварительная подготовка  
 Перед установкой DQS убедитесь, что компьютер соответствует минимальным требованиям к системе. В следующей таблице содержатся сведения о минимальных требованиях к системе для компонентов служб DQS.  
  
|Компонент DQS|Минимальные требования к системе|  
|-------------------|---------------------------------|  
|[!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]|Память (ОЗУ): Минимальные: 2 ГБ, рекомендуется 4 ГБ и более<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)] Компонент Database Engine. Дополнительные сведения см. в статье [Установка компонентов SQL Server Database Engine](../../database-engine/install-windows/install-sql-server-database-engine.md).|  
|[!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]|Платформа .NET Framework 4.0 (при ее отсутствии устанавливается во время установки клиента [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)] )<br /><br /> Internet Explorer 6.0 с пакетом обновления 1 (SP1) или более поздняя версия.|  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] и [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)] могут устанавливаться и работать на одном или на разных компьютерах. Оба компонента можно установить независимо друг от друга и в любой последовательности. Тем не менее для использования [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]необходимо установить [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] , с которым будет устанавливаться соединение.  
>   
>  Чтобы подключиться к [!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)] версии [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] или с помощью текущего или более раннюю версию [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)] и преобразование " очистка DQS ". Дополнительные сведения об обновлении существующей версии служб DQS в [!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)]см. в статье [Обновление служб Data Quality Services](../../database-engine/install-windows/upgrade-data-quality-services.md).  
>   
>  Хотя наличие Microsoft Excel не является предварительным требованием для установки клиента DQS, на компьютере клиента DQS необходимо установить Microsoft Excel 2003 или более позднюю версию для выполнения различных операций в клиентском приложении (например, импорт значения домена из файла Excel и сопоставление с исходными данными в файле Excel для обнаружения набора знаний, очистки или сопоставления).  
  
 Подробные сведения о минимальных требованиях к системе для установки [!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)] см. в статье [Требования к оборудованию и программному обеспечению для установки SQL Server](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).  
  
##  <a name="DQSInstallation"></a> Задачи по установке служб Data Quality Services  
 Для установки компонентов служб DQS необходимо использовать программу установки [!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)] . При запуске программы установки SQL Server необходимо пройти несколько страниц мастера установки, чтобы выбрать соответствующие параметры, исходя из своих требований. В следующей таблице перечислены лишь те страницы мастера установки, выбор параметров в которых повлияет на установку служб DQS.  
  
|Страница|Действие|  
|----------|------------|  
|Выбор компонентов|Выберите<br /><br /> **Службы Data Quality Services** на странице **Службы компонента Database Engine** , чтобы установить сервер служб [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]. <br />Если вы установите флажок **Службы Data Quality Services** , программа установки SQL Server скопирует файл установщика DQSInstaller.exe в каталог экземпляра SQL Server на данном компьютере. Его необходимо запустить после окончания работы программы установки SQL Server, чтобы *завершить* установку [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] . Кроме того, перед использованием [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] необходимо будет выполнить некоторые дополнительные действия по его настройке. Дополнительные сведения см. в разделе [Действия после установки](#PostInstallationTasks).<br /><br /> **Data Quality Client** , чтобы установить клиент [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)].<br /><br /> (Рекомендовано) **Средства управления — полный набор** на странице **Основные средства управления**, чтобы установить среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Она предоставляет графический пользовательский интерфейс для управления экземпляром SQL Server и позволяет выполнять дополнительные задачи после установки, перечисленные в следующем разделе.|  
|Конфигурация компонента Database Engine|Нажмите кнопку **Добавить текущего пользователя** , чтобы добавить свою учетную запись пользователя в предопределенную роль сервера sysadmin. Это необходимо, чтобы можно было позже запустить файл DQSInstaller.exe и завершить установку [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] .|  
  
##  <a name="PostInstallationTasks"></a> Действия после установки  
 После завершения работы мастера установки SQL Server необходимо выполнить дополнительные шаги, описанные в этом разделе, чтобы завершить установку [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] , выполнить его настройку и начать его использование.  
  
1.  Чтобы завершить установку [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] , запустите файл DQSInstaller.exe. После запуска файла DQSInstaller.exe:  
  
    -   Создаются базы данных DQS_MAIN, DQS_PROJECTS и DQS_STAGING_DATA.  
  
    -   Создаются имена входа ##MS_dqs_db_owner_login## и ##MS_dqs_service_login##.  
  
    -   Создаются роли dqs_administrator, dqs_kb_editor и dqs_kb_operator в базе данных DQS_MAIN.  
  
    -   В базе данных master создается хранимая процедура DQInitDQS_MAIN.  
  
    -   Файл журнала DQS_install.log обычно создается в папке C:\Program Files\Microsoft SQL Server\MSSQL13. *(имя_экземпляра)* \MSSQL\Log. Этот файл содержит сведения о действиях, выполненных после запуска файла DQSInstaller.exe.  
  
    -   Если база данных служб Master Data Services находится на том же экземпляре SQL Server, что и [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)], создается пользователь, сопоставленный с именем входа служб Master Data Services, которому предоставляется роль dqs_administrator в базе данных DQS_MAIN.  
  
     После этого установка [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] будет завершена.  
  
     Дополнительные сведения см. в разделе [Запуск файла DQSInstaller.exe для завершения установки сервера служб DQS](../../data-quality-services/install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).  
  
2.  Предоставление ролей DQS пользователям.  
  
     Чтобы войти на сервер [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] с помощью клиента [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)], пользователь должен обладать любой из следующих трех ролей в базе данных DQS_MAIN:  
  
    -   **dqs_administrator**  
  
    -   **dqs_kb_editor**  
  
    -   **dqs_kb_editor**  
  
     По умолчанию, если учетная запись пользователя является членом предопределенной роли сервера sysadmin, этот пользователь может выполнять вход на [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] с помощью клиента [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)] , даже если его учетной записи не назначена ни одна из ролей служб DQS. Дополнительные сведения о трех ролях служб DQS см. в разделе [DQS Security](../../data-quality-services/dqs-security.md).  
  
     Дополнительные сведения см. в статье [Предоставление ролей DQS пользователям](../../data-quality-services/install-windows/grant-dqs-roles-to-users.md).  
  
    > [!NOTE]  
    >  Эти три роли DQS недоступны для баз данных DQS_PROJECTS и DQS_STAGING_DATA.  
  
3.  Сделайте ваши данные доступными для операций DQS. Убедитесь, что исходные данные доступны для операций DQS и возможен экспорт обработанных данных в таблицу в базе данных.  
  
     Дополнительные сведения см. в разделе  
                    [Предоставление доступа к данным для операций со службами DQS](../../data-quality-services/install-windows/access-data-for-the-dqs-operations.md).  
  
## <a name="see-also"></a>См. также  
 [Видео: Install and Configure DQS (Установка и настройка служб DQS)](https://go.microsoft.com/fwlink/?LinkId=238241)   
 [Обновление сборок SQLCLR после обновления .NET Framework](../../data-quality-services/install-windows/upgrade-sqlclr-assemblies-after-net-framework-update.md)   
 [Экспорт и импорт баз знаний DQS с помощью DQSInstaller.exe](../../data-quality-services/install-windows/export-and-import-dqs-knowledge-bases-using-dqsinstaller-exe.md)   
 [Обновление служб Data Quality Services](../../database-engine/install-windows/upgrade-data-quality-services.md)   
 [Удаление объектов сервера служб Data Quality](../../sql-server/install/remove-data-quality-server-objects.md)   
 [Установка компонентов бизнес-аналитики SQL Server](../../sql-server/install/install-sql-server-business-intelligence-features.md)   
 [Удаление SQL Server](../../sql-server/install/uninstall-sql-server.md)   
 [Службы Data Quality Services](../../data-quality-services/data-quality-services.md)   
 [Устранение неполадок во время установки и настройки DQS](https://social.technet.microsoft.com/wiki/contents/articles/3776.aspx)  
  
  
