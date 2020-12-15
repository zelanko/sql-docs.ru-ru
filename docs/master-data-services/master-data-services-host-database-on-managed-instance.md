---
title: Размещение базы данных на управляемом экземпляре
description: Узнайте, как создать и настроить базу данных Master Data Services (MDS) и разместить ее на Управляемый экземпляр SQL Azure.
ms.custom: ''
ms.date: 07/01/2019
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 19519697-c219-44a8-9339-ee1b02545445
author: v-redu
ms.author: lle
monikerRange: '>=sql-server-ver15'
ms.openlocfilehash: ef24acb23a346b59b747d876d60d9a58374188bd
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97469975"
---
# <a name="host-an-mds-database-on-a-managed-instance"></a>Размещение базы данных MDS на управляемом экземпляре

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  В этой статье описано, как настроить базу данных Master Data Services (MDS) на управляемом экземпляре.
  
## <a name="preparation"></a>Подготовка

Для подготовки необходимо создать и настроить Управляемый экземпляр Azure SQL, а также настроить компьютер веб-приложения.

### <a name="create-and-configure-the-database"></a>Создание и настройка базы данных

1. Создание управляемого экземпляра с виртуальной сетью. Дополнительные сведения см. [в разделе Краткое руководство. создание управляемый экземпляр SQL](/azure/sql-database/sql-database-managed-instance-get-started) .

1. Настройте подключение типа "точка — сеть". Инструкции см. в статье [Настройка подключения типа "точка — сеть" к виртуальной сети с помощью собственной проверки подлинности Azure Certificate: портал Azure](/azure/vpn-gateway/vpn-gateway-howto-point-to-site-resource-manager-portal) .

1. Настройка проверки подлинности Azure Active Directory с помощью Управляемый экземпляр SQL. Дополнительные сведения см. [в разделе Настройка проверки подлинности Azure Active Directory и управление ею с помощью SQL](/azure/sql-database/sql-database-aad-authentication-configure) .

### <a name="configure-web-application-machine"></a>Настройка компьютера веб-приложения

1. Установите сертификат подключения типа "точка — сеть" и VPN, чтобы убедиться, что компьютер может получить доступ к управляемому экземпляру. Дополнительные сведения см. в разделе [Настройка подключения типа "точка — сеть" к виртуальной сети с помощью собственной проверки подлинности сертификата Azure: портал Azure](/azure/vpn-gateway/vpn-gateway-howto-point-to-site-resource-manager-portal) .

1. Установите следующие роли и компоненты:
   - Роли:
     - Службы IIS
     - Средства управления веб-сайтом
     - Консоль управления (IIS)
     - Веб-службы Интернета
     - Разработка приложений
     - Расширяемость .NET 3.5
     - Расширяемость .NET 4.5
     - ASP.NET 3.5
     - ASP.NET 4.5
     - Расширения ISAPI
     - Фильтры ISAPI
     - Общие функции HTTP
     - Документ по умолчанию
     - Просмотр каталогов
     - Ошибки HTTP
     - Статическое содержимое
     - Исправность и диагностика
     - Ведение журнала HTTP
     - Монитор запросов
     - Производительность
     - Сжатие статического содержимого
     - Безопасность
     - Фильтрация запросов
     - Проверка подлинности Windows
       > [!NOTE]
       > Не устанавливать публикацию WebDAV

   - Возможности
     - .NET Framework 3.5 (включая .NET 2.0 и 3.0)
     - Дополнительные службы .NET Framework 4.5 Advanced Services
     - ASP.NET 4.5
     - Службы WCF
     - Активация HTTP (требуется)
     - Совместное использование TCP-порта
     - Служба активации процессов Windows
     - Модель процесса
     - Среда .NET
     - API-интерфейсы конфигурации
     - Функция сжатия динамического содержимого

## <a name="install-and-configure-an-mds-web-application"></a>Установка и Настройка веб-приложения MDS

Затем установите и настройте [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] .

### <a name="install-sql-server-2019"></a>Установка SQL Server 2019

Используйте мастер установки SQL Server установки или командную строку для установки [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] .

1. Откройте `Setup.exe` и выполните действия, описанные в мастере установки.

2. На странице [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] Выбор компонентов **в разделе** Общие компоненты **выберите**.
Это действие устанавливает:
   - [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]
   - Сборки
   - Оснастка Windows PowerShell
   - Папки и файлы для веб-приложений и служб.

   ![Снимок экрана со страницей выбора компонентов.](../master-data-services/media/mds-sqlserver2019-config-mi-sqlfeatureselection.png "MDS-SQLServer2019-config-MI_SQLFeatureSelection")  

### <a name="set-up-the-database-and-website"></a>Настройка базы данных и веб-сайта

1. Подключите виртуальную сеть Azure, чтобы убедиться, что вы можете подключиться к управляемому экземпляру.

   ![Снимок экрана с VPN-подключением Test MI к виртуальной сети Azure.](../master-data-services/media/mds-sqlserver2019-config-mi-p2svpnconnect.png "MDS-SQLServer2019-config-MI_P2SVPNConnect")

1. Откройте, [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] а затем выберите **Конфигурация базы данных** в левой области.

1. Выберите **создать базу данных** , чтобы открыть **Мастер создания базы данных**. Выберите **Далее**.

1. На странице **сервер базы данных** укажите поле **экземпляра SQL Server** , а затем выберите **тип проверки подлинности**. Выберите **проверить подключение** , чтобы подтвердить возможность использования учетных данных для подключения к базе данных с помощью выбранного типа проверки подлинности. Выберите **Далее**.

   > [!NOTE]
   > - Экземпляр SQL Server выглядит следующим образом `xxxxxxx.xxxxxxx.database.windows.net` .
   > - Для управляемого экземпляра выберите тип проверки подлинности **"SQL Server учетная запись"** и **"текущий пользователь — Active Directory встроенные"** .
   > - Если выбран параметр **текущий пользователь — Active Directory, интегрированный** в качестве типа проверки подлинности, поле **имя пользователя** доступно только для чтения и отображает учетную запись пользователя Windows, выполнившего вход в систему. Если вы используете SQL Server 2019 [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] на виртуальной машине Azure, в поле **имя пользователя** отображается имя виртуальной машины и имя пользователя для учетной записи локального администратора на виртуальной машине.

   Проверка подлинности должна содержать правило **"sysadmin"** для управляемых экземпляров.

   ![Снимок экрана: страница "сервер базы данных" мастера создания базы данных.](../master-data-services/media/mds-sqlserver2019-config-mi-createdbconnect.png "MDS-SQLServer2019-config-MI_CreateDBConnect")  

1. Введите имя в поле **Имя базы данных** . Кроме того, чтобы выбрать параметры сортировки Windows, снимите флажок **SQL Server параметры сортировки по умолчанию** и выберите один или несколько доступных параметров. Например, **с учетом регистра**. Выберите **Далее**.

   ![Снимок экрана: страница "база данных" мастера создания базы данных.](../master-data-services/media/mds-sqlserver2019-config-mi-createddbname.png "MDS-SQLServer2019-config-MI_CreatedDBName")

1. В поле **имя пользователя** укажите учетную запись Windows суперпользователя по умолчанию для [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] . Супер-пользователь имеет доступ ко всем функциональным областям и может добавлять, удалять и обновлять все модели.

   ![Снимок экрана со страницей учетной записи администратора мастера создания базы данных.](../master-data-services/media/mds-sqlserver2019-config-mi-createdbusername.png "MDS-SQLServer2019-config-MI_createDBUserName")

1. Нажмите кнопку **Далее** , чтобы просмотреть сводку параметров для [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] базы данных. Нажмите кнопку  **Далее** еще раз, чтобы создать базу данных. Вы увидите страницу **ход выполнения и завершение** .

1. После создания и настройки базы данных нажмите кнопку **Готово**.

   Дополнительные сведения о параметрах **мастера создания базы данных** см. в разделе [Мастер создания базы данных &#40;[!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] Configuration Manager&#41;](../master-data-services/create-database-wizard-master-data-services-configuration-manager.md).

1. На странице **Конфигурация базы данных** в выберите [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] **выбрать базу данных**.

1. Выберите **подключить**, выберите [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] базу данных и нажмите кнопку **ОК**.

   ![Снимок экрана: диалоговое окно "подключение к базе данных".](../master-data-services/media/mds-sqlserver2019-config-mi-connectdbname.png "MDS-SQLServer2019-config-MI_connectDBName")

1. В [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] выберите **веб-конфигурация** в левой области.

1. В списке веб **-сайт** выберите **веб-сайт по умолчанию**, а затем щелкните **создать** , чтобы создать веб-приложение.

   ![Снимок экрана: диалоговое окно "диспетчер конфигурации Master Data Services".](../master-data-services/media/mds-sqlserver2019-config-mi-webconfiguration.png "MDS-SQLServer2019-config-MI_WebConfiguration")

   > [!NOTE]
   > При выборе **веб-сайта по умолчанию** необходимо отдельно создать веб-приложение. Если в списке выбран вариант **создать новый веб-сайт** , приложение будет создано автоматически.

1. В разделе **пул приложений** введите другое имя пользователя, введите пароль и нажмите кнопку **ОК**.

   ![Снимок экрана: диалоговое окно "Управление приложением".](../master-data-services/media/mds-sqlserver2019-config-mi-createwebapplication.png "MDS-SQLServer2019-config-MI_CreateWebApplication")

   > [!NOTE]
   > Убедитесь, что пользователь имеет доступ к базе данных с помощью встроенной проверки подлинности Active Directory, которую вы недавно создали. Кроме того, вы можете изменить подключение в `web.config` дальнейшем.

   Дополнительные сведения о диалоговом окне " **Создание веб-приложения** " см. в разделе [&#40;[!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] Configuration Manager&#41;диалогового окна "Создание веб-приложения"](../master-data-services/create-web-application-dialog-box-master-data-services-configuration-manager.md).

1. В области **веб-конфигурация** в окне **веб-приложение** выберите созданное приложение и нажмите кнопку **выбрать** в разделе **связать приложение с базой данных** .

1. Выберите **подключить** и выберите [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] базу данных, которую необходимо связать с веб-приложением. Выберите **ОК**.

   Настройка веб-сайта завершена. Теперь на странице **веб-конфигурация** отображается выбранный веб-сайт, созданное веб-приложение и [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] база данных, связанная с приложением.

   ![Снимок экрана: раздел веб-конфигурации.](../master-data-services/media/mds-sqlserver2019-config-mi-webconfigselectdb.png "MDS-SQLServer2019-config-MI_WebConfigSelectDB")

1. Нажмите кнопку **Применить**. Появится сообщение **Завершение настройки** . Нажмите кнопку **ОК** в окне сообщения, чтобы запустить веб-приложение. Адрес веб-сайта — `http://server name/web application/` .

## <a name="configure-authentication"></a>Настройка аутентификации

Чтобы подключить базу данных управляемого экземпляра к веб-приложению, необходимо изменить другой тип проверки подлинности.

Найдите `web.config` файл в разделе `C:\Program Files\Microsoft SQL Server\150\Master Data Services\WebApplication` . Измените строку connectionString, чтобы изменить другой тип проверки подлинности для подключения к базе данных управляемого экземпляра.

По умолчанию используется тип проверки подлинности, `Active Directory Integrated` как показано в следующем образце строки подключения:

   ```xml
   <add name="MDS1" connectionString="Data Source=*****.*****.database.windows.net;Initial Catalog=MasterDataServices;Integrated Security=False;Connect Timeout=60;Authentication=&quot;Active Directory Integrated&quot;" />
   ```

MDS также поддерживает проверку подлинности с помощью пароля Active Directory и проверку подлинности SQL Server, как показано в следующих примерах строк подключения:

- Проверка пароля Active Directory

   ```xml
   <add name="MDS1" connectionString="Data Source=*****.*****.database.windows.net;Initial Catalog=MasterDataServices;Integrated Security=False;Connect Timeout=60;Authentication=&quot;Active Directory Password&quot; ; UID=bob@contoso.onmicrosoft.com; PWD=MyPassWord!" />
   ```

- Учетные записи проверки

   ```xml
   <add name="MDS1" connectionString="Data Source=*****.*****.database.windows.net;Initial Catalog=MasterDataServices;Integrated Security=False;Connect Timeout=60;User ID=UserName;Password=MyPassword!;" />
   ```

## <a name="upgrade-ssmdsshort_md-and-sql-database-version"></a>Обновление [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] и версия базы данных SQL

### <a name="upgrade-ssmdsshort_md"></a>Обновления [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]

Установите **накопительное обновление SQL Server 2019**. [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] будет обновлен автоматически.

### <a name="upgrade-sql-server"></a>Обновление SQL Server

При `The client version is incompatible with the database version` установке **накопительного пакета обновления SQL Server 2019** может появиться сообщение об ошибке.
![Снимок экрана Master Data Services ошибки.](../master-data-services/media/mds-sqlserver2019-config-mi-upgradedbpage.png "MDS-SQLServer2019-config-MI_UpgradeDBPage")

Чтобы устранить эту проблему, необходимо обновить версию базы данных:

1. Откройте [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] , а затем выберите  **Конфигурация базы данных** в левой области.

1. На странице **Конфигурация базы данных** в выберите [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] **выбрать базу данных**.

1. Выберите [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] базу данных, связанную с веб-приложением. Выберите **подключить**, а затем нажмите кнопку **ОК**.

   ![Снимок экрана: диалоговое окно "подключение к базе данных службы основных данных".](../master-data-services/media/mds-sqlserver2019-config-mi-connectdbname.png "MDS-SQLServer2019-config-MI_ConnectDBName")

1. Выберите **обновить базу данных...** .

   ![Снимок экрана с параметром обновления базы данных.](../master-data-services/media/mds-sqlserver2019-config-mi-selectupgradedb.png "MDS-SQLServer2019-config-MI_SelectUpgradeDB")

1. В мастере обновления базы данных нажмите кнопку **Далее** на странице **Приветствие** и на странице  **Проверка обновления** .

   ![Снимок экрана страницы "Проверка обновления" мастера обновления базы данных.](../master-data-services/media/mds-sqlserver2019-config-mi-upgradedbwizard.png "MDS-SQLServer2019-config-MI_UpgradeDBWizard")

1. По завершении всех задач нажмите кнопку **Готово** .

## <a name="see-also"></a>См. также раздел

- [База данных служб Master Data Services](../master-data-services/master-data-services-database.md)
- [Веб-приложение диспетчера основных данных](../master-data-services/master-data-manager-web-application.md)
- [Страница "Конфигурация базы данных" (диспетчер конфигурации служб Master Data Services)](../master-data-services/database-configuration-page-master-data-services-configuration-manager.md)
- [Новые возможности Master Data Services (MDS)](../master-data-services/what-s-new-in-master-data-services-mds.md)