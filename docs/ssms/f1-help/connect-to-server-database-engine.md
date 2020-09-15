---
description: Соединение с сервером (ядро СУБД)
title: Соединение с сервером (ядро СУБД)
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.swb.connectoserverunknownservertype.f1
- sql13.swb.connection.login.sqlce.f1
- sql13.swb.connecttoce.f1
- SQL13.SWB.CONNECTION.LOGIN.SQLSERVER.F1
- sql13.swb.connection.login.sqlserver.f1
- sql13.swb.manageSS2k.f1
ms.assetid: ee9017b4-8a19-4360-9003-9e6484082d41
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 04/07/2020
ms.openlocfilehash: d46002843574b54c803ed0da33c02f1d795494ab
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88317930"
---
# <a name="connect-to-server-database-engine"></a>Соединение с сервером (ядро СУБД)

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Используйте это диалоговое окно для просмотра или настройки параметров при подключении к [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]. В большинстве случаев при подключении в поле **Имя сервера** нужно ввести имя компьютера, на котором расположена база данных, а затем нажать кнопку **Соединить**. При подключении к именованному экземпляру укажите имя компьютера, введите обратную косую черту, а затем — имя экземпляра. Например, `mycomputer\myinstance`. Если выполняется соединение с [!INCLUDE[ssExpress](../../includes/ssexpress_md.md)], введите имя компьютера, а после него — **\sqlexpress**.
  
На возможность подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]влияют многие факторы. Справочные сведения см. в следующих документах.

- [Урок 1. Подключение к ядру СУБД](../../relational-databases/lesson-1-connecting-to-the-database-engine.md)  

- [Устранение неполадок при соединении с SQL Server Database Engine](../../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md)  

- [Устранение ошибок подключения к SQL Server](https://support.microsoft.com/help/4009936/solving-connectivity-errors-to-sql-server)   
  
## <a name="options"></a>Параметры

**Тип сервера**  
При регистрации сервера из обозревателя объектов выберите тип сервера для подключения: [!INCLUDE[ssDE](../../includes/ssde_md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion_md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]или [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. В остальной части диалогового окна показаны параметры, которые применяются только к выбранному типу сервера. При регистрации сервера c панели "Зарегистрированные серверы" поле **Тип сервера** не может быть изменено и совпадает с типом сервера, показанного в компоненте "Зарегистрированные серверы". Чтобы зарегистрировать другой тип сервера, выберите компонент [!INCLUDE[ssDE](../../includes/ssde_md.md)], службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion_md.md)], службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssEW](../../includes/ssew-md.md)]или службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на панели инструментов «Зарегистрированные серверы», прежде чем начать регистрацию нового сервера.  
  
**Имя сервера**  
Выберите экземпляр сервера для подключения. По умолчанию выводится экземпляр сервера, к которому подключение выполнялось в последний раз.  
  
> [!NOTE]  
> Для подключения к активному пользовательскому экземпляру [!INCLUDE[ssExpress](../../includes/ssexpress_md.md)] установите подключение с использованием протокола именованных каналов, указав имя канала, например, `np:\\.\pipe\3C3DF6B1-2262-47\tsql\query`. Дополнительные сведения см. в документации по [!INCLUDE[ssExpress](../../includes/ssexpress_md.md)].  

> [!NOTE]  
> Обычно данные о подключениях хранятся в журнале "Недавно использовавшиеся" (MRU). Чтобы удалить записи из журнала MRU, просто щелкните поле со списком **Имя сервера**, выберите имя сервера для удаления и нажмите клавишу **DEL**.  

**Аутентификация**  
Текущая версия SSMS предлагает пять режимов проверки подлинности при подключении к экземпляру [!INCLUDE[ssDE](../../includes/ssde_md.md)]. Если диалоговое окно проверки подлинности не соответствует перечисленным ниже, скачайте последнюю версию SSMS на странице [Скачивание SQL Server Management Studio (SSMS)](../download-sql-server-management-studio-ssms.md).  

> **Проверка подлинности Windows.**  
> [!INCLUDE[msCoName](../../includes/msconame_md.md)] Режим проверки подлинности Windows позволяет подключаться с учетной записью Windows.  
> 
> **Проверка подлинности SQL Server**  
> При подключении пользователя с указанным именем входа и паролем не через доверенное соединение [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняет проверку подлинности самостоятельно по наличию учетной записи входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и совпадения указанного пароля с ранее сохраненным. Если в службе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не задана учетная запись входа, проверка подлинности завершается ошибкой, о которой пользователь получит сообщение. По возможности используйте проверку подлинности Windows или проверку подлинности "Active Directory — пароль".  
> 
> **Azure Active Directory — универсальный с поддержкой MFA**  
> Проверка подлинности "Active Directory — универсальная с поддержкой MFA" представляет собой интерактивный рабочий процесс, поддерживающий Многофакторную идентификацию Azure (MFA). Azure MFA помогает защитить доступ к данным и приложениям, а также удовлетворить потребность пользователей в простом процессе входа. Она обеспечивает надежную проверку подлинности с помощью целого спектра простых способов — телефонного звонка, текстового сообщения, смарт-карт с ПИН-кодом или уведомления мобильного приложения, чтобы пользователи могли выбрать наиболее удобный для них метод. Когда учетная запись пользователя настроена для MFA, рабочий процесс интерактивной проверки подлинности требует от пользователя дополнительного взаимодействия посредством всплывающих диалоговых окон, использования смарт-карт и т. д. Если учетная запись пользователя настроена для MFA, для подключения пользователь должен выбрать универсальную проверку подлинности Azure. Если учетная запись пользователя не требует применения MFA, пользователь может использовать два других варианта проверки подлинности Azure Active Directory. Дополнительные сведения см. в разделе [Поддержка SSMS для Azure AD MFA с использованием Базы данных SQL и хранилища данных SQL](https://azure.microsoft.com/documentation/articles/sql-database-ssms-mfa-authentication/). При необходимости вы можете изменить домен, который проверяет подлинность имени входа, щелкнув **Параметры**, выбрав вкладку **Свойства соединения** и заполнив поле **Доменное имя AD или идентификатор клиента**.  
> 
> **Azure Active Directory — пароль**  
> Проверка подлинности Azure Active Directory — это механизм подключения к [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] с помощью удостоверений в Azure Active Directory (Azure AD).  Используйте этот метод для подключения к [!INCLUDE[ssSDS](../../includes/sssds-md.md)], если вы вошли в Windows с учетными данными из домена, не включенного в федерацию с Azure, или если применяется проверка подлинности Azure AD на базе первоначального домена или домена клиента. См. дополнительные сведения об [использовании аутентификации Azure Active Directory для аутентификации с помощью SQL](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/).  
> 
> **Active Directory — встроенная**  
> Проверка подлинности Azure Active Directory — это механизм подключения к [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] с помощью удостоверений в Azure Active Directory (Azure AD). Используйте этот метод для подключения к [!INCLUDE[ssSDS](../../includes/sssds-md.md)], если вы вошли в Windows с учетными данными Azure Active Directory из федеративного домена. См. дополнительные сведения об [использовании аутентификации Azure Active Directory для аутентификации с помощью SQL](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/).  
  
**User name**  
Имя пользователя Windows для соединения. Этот параметр доступен только в том случае, если выбрано соединение с использованием проверки подлинности **Azure Active Directory — пароль**. Он доступен только для чтения при выборе типа проверки подлинности **Проверка подлинности Windows** или **Active Directory — встроенная**.  
  
**Имя входа**  
Введите имя входа для подключения. Этот параметр доступен только в том случае, если выбрано подключение с использованием проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или проверки подлинности "Active Directory — пароль".  
  
> [!NOTE]  
> Обычно данные о подключениях хранятся в журнале "Недавно использовавшиеся" (MRU). Чтобы удалить записи из журнала MRU, просто щелкните поле со списком **Имя сервера**, выберите имя сервера для удаления и нажмите клавишу **DEL**. Эта возможность предоставляется в SSMS 18.5.

**Пароль**  
Введите пароль для этого имени входа. Этот параметр можно изменить только в том случае, если выбрано подключение с использованием проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или проверки подлинности "Active Directory — пароль".  

**Подключить**  
Щелкните, чтобы подключиться к серверу.

**Параметры**  
Щелкните, чтобы открыть вкладки **Свойства соединения** и **Дополнительные параметры соединения**.
