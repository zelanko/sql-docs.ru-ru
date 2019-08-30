---
title: Размещение базы данных на управляемом экземпляре | Документация Майкрософт
description: Описывает настройку базы данных MDS на управляемом экземпляре.
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
manager: craigg
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 0081ea193452e4e92938051bc7b4a40bc8631eaa
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70155381"
---
# <a name="host-database-on-managed-instance"></a>База данных узла на управляемом экземпляре

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В этой статье описывается настройка базы данных MDS на управляемом экземпляре.
  
## <a name="preparation"></a>Подготовка

В процессе подготовки необходимо выполнить следующие действия.
- Завершение создания и настройки управляемого экземпляра. Включите виртуальную сеть и VPN-подключение типа "точка — сеть".
- Завершите настройку компьютера веб-приложения.
  - Включить установку VPN типа "точка — сеть".
  - Установите роли и компоненты.

**Сторона базы данных:**

1. Создание управляемого экземпляра базы данных SQL Azure включает в себя виртуальную сеть. [Краткое руководство Создание управляемого экземпляра базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-get-started)
2. Настройте подключение типа "точка — сеть". [Настройка подключения типа "точка — сеть" к виртуальной сети с помощью собственной проверки подлинности на основе сертификата Azure. портал Azure](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-howto-point-to-site-resource-manager-portal)
3. Настройка проверки подлинности Azure Active Directory с помощью управляемого экземпляра базы данных SQL. [Настройка проверки подлинности Azure Active Directory и управление ею с помощью SQL](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication-configure)

**Сторона компьютера веб-приложения:**

1. Установите сертификат подключения типа "точка — сеть" и VPN, чтобы убедиться, что компьютер может получить доступ к управляемому экземпляру базы данных SQL. [Настройка подключения типа "точка — сеть" к виртуальной сети с помощью собственной проверки подлинности на основе сертификата Azure. портал Azure](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-howto-point-to-site-resource-manager-portal)
2. Установите роли и компоненты. Следующие функции являются обязательными.

- Роли

      Internet Information Services
      Web Management Tools
      IIS Management Console
      World Wide Web Services
      Application Development
      .NET Extensibility 3.5
      .NET Extensibility 4.5
      ASP.NET 3.5
      ASP.NET 4.5
      ISAPI Extensions
      ISAPI Filters
      Common HTTP Features
      Default Document
      Directory Browsing
      HTTP Errors
      Static Content
      [Note: Do not install WebDAV Publishing]
      Health and Diagnostics
      HTTP Logging
      Request Monitor
      Performance
      Static Content Compression
      Security
      Request Filtering
      Windows Authentication

- Функции:

      .NET Framework 3.5 (includes .NET 2.0 and 3.0)
      .NET Framework 4.5 Advanced Services
      ASP.NET 4.5
      WCF Services
      HTTP Activation [Note: This is required.]
      TCP Port Sharing
      Windows Process Activation Service
      Process Model
      .NET Environment
      Configuration APIs
      Dynamic Content Compression

## <a name="install-and-configure-includessmdsshort_mdincludesssmdsshort-mdmd-web-application"></a>Установка и настройка [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] веб-приложения

Для установки и настройки [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]необходимо завершить следующие шаги.

1. Установите компонент SQL Server 2019 [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] include.
2. [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] Создание базы данных на экземпляре управления.
3. Создайте и настройте веб-приложение [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]для.
  
**Установка SQL Server 2019**

Для установки [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]используется мастер установки SQL Server установки или Командная строка.

1. Дважды щелкните файл Setup.exe и следуйте инструкциям мастера установки.

2. На [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] странице Выбор компонентов выберите Общие компоненты.
При этом устанавливается [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)], сборки, оснастка Windows PowerShell, папки и файлы для веб-приложений и служб.

    ![MDS-SQLServer2019-config-MI-склфеатуреселектион](../master-data-services/media/mds-sqlserver2019-config-mi-sqlfeatureselection.png "MDS-SQLServer2019-config-MI_SQLFeatureSelection")  

**Настройка базы данных и веб-сайта**

1. Подключите виртуальную сеть Azure, чтобы убедиться, что вы можете подключиться к управляемому экземпляру.

    ![MDS-SQLServer2019-config-MI-P2SVPNConnect](../master-data-services/media/mds-sqlserver2019-config-mi-p2svpnconnect.png "MDS-SQLServer2019-config-MI_P2SVPNConnect")  

2. [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]Запустите. И щелкните **Конфигурация базы данных** в левой области.

3. Щелкните **создать базу данных**, а затем нажмите кнопку Далее в мастере **создания базы данных** .

4. На странице **сервер базы данных** заполните **экземпляр SQL Server** и выберите **тип проверки** подлинности, а затем нажмите кнопку **проверить подключение** , чтобы убедиться, что можно подключиться к базе данных, используя учетные данные для типа проверки подлинности, который вы выбрать. Нажмите кнопку Далее.

   > [!NOTE]
   > - Экземпляр SQL Server для управляемого экземпляра, например "xxxxxxx.xxxxxxx.database.windows.net"
   > - Для управляемого экземпляра мы поддерживаем тип проверки подлинности **"учетная запись SQL Server"** и **"текущий пользователь — Active Directory интегрирован"** .
   > - При выборе параметра **текущий пользователь — Active Directory** , интегрированный в качестве типа проверки подлинности, поле **имя пользователя** доступно только для чтения и отображает имя учетной записи пользователя Windows, выполнившего вход на компьютер. Если вы используете SQL Server 2019 [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] на виртуальной машине Azure, в поле **имя пользователя** отображается имя виртуальной машины и имя пользователя для учетной записи локального администратора на виртуальной машине.

    Убедитесь, что проверка подлинности содержит правило **"sysadmin"** для управляемого экземпляра.
![MDS-SQLServer2019-config-MI-креатедбконнект](../master-data-services/media/mds-sqlserver2019-config-mi-createdbconnect.png "MDS-SQLServer2019-config-MI_CreateDBConnect")  

5. Введите имя в поле **Имя базы данных** . Если необходимо выбрать параметры сортировки Windows, снимите флажок **Параметры сортировки SQL Server по умолчанию** и укажите один или несколько доступных параметров, например **С учетом регистра**. Нажмите кнопку **Далее**.

    ![MDS-SQLServer2019-config-MI-креатеддбнаме](../master-data-services/media/mds-sqlserver2019-config-mi-createddbname.png "MDS-SQLServer2019-config-MI_CreatedDBName")  

6. В поле **имя пользователя** укажите учетную запись пользователя Windows, которая будет являться суперпользователя по умолчанию для [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]. Суперпользователь имеет доступ ко всем функциональным областям и может добавлять, удалять и обновлять все модели.

    ![MDS-SQLServer2019-config-MI-креатедбусернаме](../master-data-services/media/mds-sqlserver2019-config-mi-createdbusername.png "MDS-SQLServer2019-config-MI_createDBUserName")

7. Нажмите кнопку **Далее** , чтобы просмотреть сводку параметров для базы данных [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] , а затем нажмите кнопку **Далее** еще раз, чтобы создать базу данных. Откроется страница **Ход выполнения и завершение**.

8. После создания и настройки базы данных нажмите кнопку **Готово**.

    Дополнительные сведения о параметрах **мастера создания базы данных**см. в разделе [Мастер &#40; [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] создания базы данных&#41;Configuration Manager](../master-data-services/create-database-wizard-master-data-services-configuration-manager.md).

9. На странице **Конфигурация базы данных** в [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]выберите пункт **выбрать базу данных**.

10. Нажмите кнопку **подключить**, выберите [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] базу данных, созданную на шаге 8, и нажмите кнопку **ОК**.

    ![MDS-SQLServer2019-config-MI-коннектдбнаме](../master-data-services/media/mds-sqlserver2019-config-mi-connectdbname.png "MDS-SQLServer2019-config-MI_connectDBName")

11. В [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]щелкните **Веб-конфигурация** в области слева.

12. В поле со списком **Веб-сайт** выберите элемент **Веб-сайт по умолчанию**, а затем нажмите кнопку **Создать** , чтобы создать веб-приложение.
![MDS-SQLServer2019-config-MI-Web Configuration](../master-data-services/media/mds-sqlserver2019-config-mi-webconfiguration.png "MDS-SQLServer2019-config-MI_WebConfiguration")

   > [!NOTE] 
   > Если выбран элемент **Веб-сайт по умолчанию**, необходимо создать веб-приложение. Если в списке выбран элемент **Создать новый веб-сайт** , приложение создается автоматически.

    

13. В разделе **пул приложений** введите другое имя пользователя, введите пароль и нажмите кнопку ОК.
![MDS-SQLServer2019-config-MI-креатевебаппликатион](../master-data-services/media/mds-sqlserver2019-config-mi-createwebapplication.png "MDS-SQLServer2019-config-MI_CreateWebApplication")

   > [!NOTE]
   > Необходимо убедиться, что пользователь может получить доступ к базе данных, используя только что созданную встроенную проверку подлинности Active Directory. Также необходимо изменить подключение в файле Web. config позже.

    

14. Дополнительные сведения о диалоговом окне " **Создание веб-приложения** " см. в разделе [диалоговое окно "Создание веб-приложения" &#40; [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] Configuration Manager&#41;](../master-data-services/create-web-application-dialog-box-master-data-services-configuration-manager.md).

15. На странице **веб-конфигурация** в поле **веб-приложение** выберите созданное приложение и нажмите кнопку **выбрать** в разделе **связать приложение с базой данных** .

16. Нажмите кнопку **Подключить**, выберите базу данных [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] , которую нужно связать в веб-приложением, а затем нажмите кнопку **ОК**.

    Настройка веб-сайта завершена. Теперь на странице **веб-конфигурация** отображается выбранный веб-сайт, созданное веб-приложение и [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] база данных, связанная с приложением.

    ![MDS-SQLServer2019-config-MI-вебконфигселектдб](../master-data-services/media/mds-sqlserver2019-config-mi-webconfigselectdb.png "MDS-SQLServer2019-config-MI_WebConfigSelectDB")

17. Нажмите кнопку **Применить**. Появится сообщение о **завершении настройки**. Нажмите кнопку **ОК** в окне сообщения, чтобы запустить веб-приложение. Адрес веб-сайта — http://server имя/веб-приложение/.

## <a name="other-authentication-type-to-connect-managed-instance-database-on-web-application"></a>Другой тип проверки подлинности для подключения базы данных управляемого экземпляра к веб-приложению

Файл **Web. config** можно получить в папке C:\PROGRAM Files\Microsoft SQL Server\150\Master Data Services\WebApplication. Мы можем изменить connectionString, чтобы изменить другой тип проверки подлинности для подключения базы данных управляемого экземпляра.

По умолчанию используется тип проверки подлинности "**Active Directory Integrated**", а ниже приведен пример строки подключения.

```xml
<add name="MDS1" connectionString="Data Source=*****.*****.database.windows.net;Initial Catalog=MasterDataServices;Integrated Security=False;Connect Timeout=60;Authentication=&quot;Active Directory Integrated&quot;" />
```

Мы также поддерживаем проверку подлинности Active Directory пароля и проверку подлинности SQL Server. пример строки подключения приведен ниже.

Проверка подлинности Active Directory пароля

```xml
<add name="MDS1" connectionString="Data Source=*****.*****.database.windows.net;Initial Catalog=MasterDataServices;Integrated Security=False;Connect Timeout=60;Authentication=&quot;Active Directory Password&quot; ; UID=bob@contoso.onmicrosoft.com; PWD=MyPassWord!" />
```

Проверка подлинности SQL Server

```xml
<add name="MDS1" connectionString="Data Source=*****.*****.database.windows.net;Initial Catalog=MasterDataServices;Integrated Security=False;Connect Timeout=60;User ID=UserName;Password=MyPassword!;" />
```

## <a name="upgrade-includessmdsshort_mdincludesssmdsshort-mdmd-and-database-version"></a>Обновление [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] и версия базы данных

**Обновления[!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]**

Установите **накопительный пакет обновления**SQL Server 2019, [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] который будет обновлен автоматически.

**Обновление версии базы данных**

Если вы получаете сообщение "версия клиента несовместима с версией базы данных" после установки **накопительного обновления**SQL Server 2019, необходимо обновить версию базы данных.

![MDS-SQLServer2019-config-MI-упградедбпаже](../master-data-services/media/mds-sqlserver2019-config-mi-upgradedbpage.png "MDS-SQLServer2019-config-MI_UpgradeDBPage")

1. [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]Запустите. И щелкните **Конфигурация базы данных** в левой области.

2. На странице **Конфигурация базы данных** в [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]выберите пункт **выбрать базу данных**.

3. Нажмите кнопку **подключить**, выберите [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] базу данных, связанную с веб-приложением, и нажмите кнопку **ОК**.

    ![MDS-SQLServer2019-config-MI-коннектдбнаме](../master-data-services/media/mds-sqlserver2019-config-mi-connectdbname.png "MDS-SQLServer2019-config-MI_ConnectDBName")

4. Нажмите кнопку **обновить базу данных...** переключатель

    ![MDS-SQLServer2019-config-MI-селектупградедб](../master-data-services/media/mds-sqlserver2019-config-mi-selectupgradedb.png "MDS-SQLServer2019-config-MI_SelectUpgradeDB")

5. В мастере обновления базы данных нажмите кнопку **Далее** на странице **Приветствие** и странице " **Проверка обновления** ".

    ![MDS-SQLServer2019-config-MI-упградедбвизард](../master-data-services/media/mds-sqlserver2019-config-mi-upgradedbwizard.png "MDS-SQLServer2019-config-MI_UpgradeDBWizard")

6. Нажмите кнопку **"Готово** ", когда завершится вся задача.

## <a name="see-also"></a>См. также

 [База данных Master Data Services](../master-data-services/master-data-services-database.md) [Веб-приложение Диспетчер основных данных](../master-data-services/master-data-manager-web-application.md) [ &#40;Диспетчер конфигурации Master Data Services&#41; страницы конфигурации базы данных](../master-data-services/database-configuration-page-master-data-services-configuration-manager.md) [Новые возможности Master Data Services &#40;MDS&#41; ](../master-data-services/what-s-new-in-master-data-services-mds.md)
