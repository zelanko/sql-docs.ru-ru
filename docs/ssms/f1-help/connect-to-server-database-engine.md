---
title: "Соединение с сервером (ядро СУБД) | Документация Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 01/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.connectoserverunknownservertype.f1
- sql13.swb.connection.login.sqlce.f1
- sql13.swb.connecttoce.f1
- SQL13.SWB.CONNECTION.LOGIN.SQLSERVER.F1
- sql13.swb.connection.login.sqlserver.f1
- sql13.swb.manageSS2k.f1
ms.assetid: ee9017b4-8a19-4360-9003-9e6484082d41
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: d421bcb09ec7ebde28b5d1cce6eca2263cfb1c48
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="connect-to-server-database-engine"></a>Соединение с сервером (ядро СУБД)
Используйте это диалоговое окно для просмотра или задания параметров при соединении со службами [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]. В большинстве случаев при подключении в поле **Имя сервера** нужно ввести имя компьютера, на котором расположена база данных, а затем нажать кнопку **Соединить**. Если выполняется соединение с [!INCLUDE[ssExpress](../../includes/ssexpress_md.md)], введите имя компьютера, а после него — **\sqlexpress**.  
  
На возможность подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]влияют многие факторы.  
  
## <a name="options"></a>Параметры  
**Тип сервера**  
При регистрации сервера из обозревателя объектов выберите тип сервера для подключения: [!INCLUDE[ssDE](../../includes/ssde_md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion_md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion_md.md)]или [!INCLUDE[ssISnoversion](../../includes/ssisnoversion_md.md)]. В остальной части диалогового окна показаны параметры, которые применяются только к выбранному типу сервера. При регистрации сервера c панели "Зарегистрированные серверы" поле **Тип сервера** не может быть изменено и совпадает с типом сервера, показанного в компоненте "Зарегистрированные серверы". Чтобы зарегистрировать другой тип сервера, выберите компонент [!INCLUDE[ssDE](../../includes/ssde_md.md)], службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion_md.md)], службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion_md.md)], [!INCLUDE[ssEW](../../includes/ssew_md.md)]или службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion_md.md)] на панели инструментов «Зарегистрированные серверы», прежде чем начать регистрацию нового сервера.  
  
**Имя сервера**  
Выберите экземпляр сервера для подключения. По умолчанию выводится экземпляр сервера, к которому подключение выполнялось в последний раз.  
  
> [!NOTE]  
> Для подключения к активному экземпляру [!INCLUDE[ssExpress](../../includes/ssexpress_md.md)] выполните подключение с использованием протокола именованных каналов, указав имя канала, например "\\\\.\pipe\3C3DF6B1-2262-47\tsql\query". Дополнительные сведения см. в документации по [!INCLUDE[ssExpress](../../includes/ssexpress_md.md)] .  
  
**Проверка подлинности**  
При подключении к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde_md.md)]доступны три режима проверки подлинности.  
  
**Проверка подлинности Windows.**  
[!INCLUDE[msCoName](../../includes/msconame_md.md)] Режим проверки подлинности Windows позволяет подключаться с учетной записью Windows.  
  
**Проверка подлинности SQL Server**  
При подключении пользователя с указанным именем входа и паролем не через доверенное соединение [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] выполняет проверку подлинности самостоятельно по наличию учетной записи входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] и совпадения указанного пароля с ранее сохраненным. Если в службе [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] не задана учетная запись входа, проверка подлинности завершается ошибкой, о которой пользователь получит сообщение.  
  
> [!IMPORTANT]  
> По возможности используйте проверку подлинности Windows или проверку подлинности с помощью пароля Active Directory.  
  
**Универсальная проверка подлинности Active Directory**  
Универсальная проверка подлинности Active Directory — это интерактивный рабочий процесс, поддерживающий Многофакторную идентификацию Azure (MFA). Azure MFA помогает защитить доступ к данным и приложениям, а также удовлетворить потребность пользователей в простом процессе входа. Она обеспечивает надежную проверку подлинности с помощью целого спектра простых способов — телефонного звонка, текстового сообщения, смарт-карт с ПИН-кодом или уведомления мобильного приложения, чтобы пользователи могли выбрать наиболее удобный для них метод. Когда учетная запись пользователя настроена для MFA, рабочий процесс интерактивной проверки подлинности требует от пользователя дополнительного взаимодействия посредством всплывающих диалоговых окон, использования смарт-карт и т. д. Если учетная запись пользователя настроена для MFA, для подключения пользователь должен выбрать универсальную проверку подлинности Azure. Если учетная запись пользователя не требует применения MFA, пользователь может использовать два других варианта проверки подлинности Azure Active Directory. Дополнительные сведения см. в разделе [Поддержка SSMS для Azure AD MFA с использованием Базы данных SQL и хранилища данных SQL](https://azure.microsoft.com/documentation/articles/sql-database-ssms-mfa-authentication/). Требуется SSMS версии не ниже 16.3 (август 2016 г.).

**Проверка подлинности с помощью пароля Active Directory**  
Проверка подлинности Azure Active Directory — это механизм подключения к [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssSDSfull](../../includes/sssdsfull_md.md)] с помощью удостоверений в Azure Active Directory (Azure AD).  Используйте этот метод для подключения к [!INCLUDE[ssSDS](../../includes/sssds_md.md)] , если выполнен вход в Windows с применением учетных данных из домена, не включенного в федерацию с Azure, или применяется проверка подлинности Azure AD с помощью Azure AD на базе первоначального домена или домена клиента. Дополнительные сведения см. в статье [Подключение к базе данных SQL с использованием проверки подлинности Azure Active Directory](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/).  
  
**Интегрированная проверка подлинности Active Directory**  
Проверка подлинности Azure Active Directory — это механизм подключения к [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssSDSfull](../../includes/sssdsfull_md.md)] с помощью удостоверений в Azure Active Directory (Azure AD). Используйте этот метод для подключения к [!INCLUDE[ssSDS](../../includes/sssds_md.md)] , если выполнен вход в Windows с применением учетных данных Azure Active Directory из федеративного домена. Дополнительные сведения см. в статье [Подключение к базе данных SQL с использованием проверки подлинности Azure Active Directory](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/).  
  
**Имя пользователя**  
Имя пользователя Windows для соединения. Этот параметр доступен только в том случае, если выбрано соединение с использованием проверки подлинности **Проверка пароля Active Directory**. При выборе значения **Проверка подлинности Windows**он доступен только для чтения.  
  
**Имя входа**  
Введите имя входа для подключения. Этот параметр доступен только в том случае, если выбрано соединение с использованием проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или проверки подлинности с помощью пароля Active Directory.  
  
**Пароль**  
Введите пароль для этого имени входа. Этот параметр доступен для изменения только в том случае, если выбрано соединение с использованием проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или проверки подлинности с помощью пароля Active Directory.  
  
**Соединить**  
Нажмите, чтобы подключиться к выбранному выше серверу.  
  
**Параметры**  
Нажмите, чтобы вывести дополнительные параметры соединения с сервером, такие как регистрация сервера и запоминание пароля.  
  

