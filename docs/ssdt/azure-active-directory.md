---
title: Azure Active Directory в SSDT
description: Узнайте о методах проверки подлинности Azure Active Directory, предоставляемых SQL Server Data Tools (SSDT) для базы данных SQL Azure и Azure Synapse Analytics.
ms.prod: sql
ms.technology: ssdt
ms.topic: conceptual
author: markingmyname
ms.author: maghan
reviewer: ''
ms.custom: seo-lt-2019
ms.date: 10/28/2019
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: cde082f95bc7ff150c263742450a69fa9c90e6b7
ms.sourcegitcommit: a5398f107599102af7c8cda815d8e5e9a367ce7e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/13/2020
ms.locfileid: "92005922"
---
# <a name="azure-active-directory-support-in-sql-server-data-tools-ssdt"></a>Поддержка Azure Active Directory в SQL Server Data Tools (SSDT)

[!INCLUDE[appliesto-xx-asdb-asdb-xxx-md.md](../includes/appliesto-xx-asdb-asdw-xxx-md.md)]

SQL Server Data Tools (SSDT) предоставляет несколько методов проверки подлинности [Azure Active Directory (Azure AD)](/azure/active-directory/active-directory-whatis).

В Visual Studio откройте **Обозреватель объектов SQL Server** (в меню **Представление**) и выберите **Добавить SQL Server**:

![Диалоговое окно подключения SSDT](media/azure-active-directory/interactive.png)

#### <a name="which-azure-sql-products"></a>Какие продукты SQL Azure?

В этой статье рассматривается Azure AD для следующего списка *продуктов SQL Azure*  в [облаке Azure](https://azure.microsoft.com/).

- База данных SQL Azure
- Azure Synapse Analytics

## <a name="active-directory-password-authentication"></a>Проверка подлинности с помощью пароля Active Directory

*Проверка подлинности с помощью пароля Active Directory* — это механизм подключения к перечисленным ранее продуктам SQL Azure. Механизм использует удостоверения Azure Active Directory (Azure AD). Используйте этот метод для подключения, если:

- вы вошли в Windows с помощью учетных данных из домена, не включенного в федерацию с Azure; или
- вы используете проверку подлинности Azure AD с Azure AD на базе первоначального домена или домена клиента.

См. дополнительные сведения об [использовании аутентификации Azure Active Directory для аутентификации с помощью SQL](/azure/sql-database/sql-database-aad-authentication).  

## <a name="active-directory-integrated-authentication"></a>Интегрированная проверка подлинности Active Directory

*Интегрированная проверка подлинности Active Directory* — это механизм подключения к перечисленным продуктам SQL Azure с помощью удостоверений в Azure Active Directory (Azure AD). Используйте этот метод для подключения, если вы вошли в Windows с учетными данными Azure Active Directory из федеративного домена. См. дополнительные сведения об [использовании аутентификации Azure Active Directory для аутентификации с помощью SQL](/azure/sql-database/sql-database-aad-authentication).

## <a name="active-directory-interactive-authentication"></a>Интерактивная проверка подлинности Active Directory

*Интерактивная проверка подлинности Active Directory* доступна при подключении к перечисленным продуктам SQL Azure с помощью SSDT, но только с [.NET Framework 4.7.2](/dotnet/api/?view=netframework-4.7.2) или более поздней версии.

- [Скачайте и установите для .NET Framework (любую версию)](https://www.microsoft.com/net/download/all).
- [Visual Studio 2017 версия 15.6](/visualstudio/releasenotes/vs2017-relnotes) или более поздняя.

#### <a name="multi-factor-authentication-mfa"></a>Многофакторная идентификация (MFA)

Интерактивная проверка подлинности Active Directory поддерживает интерактивную проверку подлинности, что позволяет применять многофакторную идентификацию (MFA) Azure Active Directory (AD) для проверки подлинности перечисленных продуктов SQL Azure. Этот метод поддерживается для пользователей Azure AD из собственного и федеративного домена, гостевых пользователей из других учетных записей. Другие типы учетных записей:

- пользователи Azure AD B2B;
- учетные записи Майкрософт, такие как @outlook.com, @hotmail.com, @live.com;
- сторонние учетные записи, такие как @gmail.com.

Если выбран метод MFA, нужно указать **имя пользователя**. Поле **Пароль** будет отключено. 

#### <a name="password-entry"></a>Ввод пароля

При *интерактивной проверке подлинности Active Directory* откроется окно проверки подлинности, в котором пользователи должны ввести пароль вручную.

![Диалоговое окно входа](media/azure-active-directory/sign-in.png)

Принудительное применение MFA реализуется Azure AD через это дополнительное всплывающее окно MFA.

> [!NOTE]
> Использование *интерактивной проверки подлинности Active Directory* приведет к блокировке автоматических рабочих процессов. При такой проверке подлинности пользователь должен вручную (интерактивно) вводить свой пароль.

## <a name="known-issues-and-limitations"></a>Известные проблемы и ограничения

- *Интерактивная проверка подлинности Active Directory* поддерживается только при подключении к продуктам SQL Azure, которые были перечислены в начале этой статьи. Она не поддерживается для SQL Server (в локальной среде или на виртуальной машине).
- *Интерактивная проверка подлинности Active Directory* не поддерживается в диалоговом окне подключения в *обозревателе сервера*. Вам нужно подключиться к *обозревателю объектов SQL Server* с помощью SSDT.
- Интеграция единого входа с текущей учетной записью Visual Studio, которая использовалась для входа, не поддерживается для SSDT.
- Пакет SQLPackage.exe, установленный в каталоге Extensions во время установки Visual Studio, не предназначен для использования в этом расположении. Чтобы использовать SQLpackage.exe с AAD, перейдите по адресу [https://www.microsoft.com/download/details.aspx?id=55088](https://www.microsoft.com/download/details.aspx?id=55088). 
- Сравнение данных SSDT не поддерживается для проверки подлинности Azure AD.  


## <a name="see-also"></a>См. также:  

[Многофакторная проверка подлинности](/azure/sql-database/sql-database-ssms-mfa-authentication)  
[Настройка аутентификации Azure Active Directory и управление ею с использованием базы данных SQL или хранилища данных SQL](/azure/sql-database/sql-database-aad-authentication-configure)  
[Форум MSDN по SSDT](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=ssdt)  
[Блог группы разработчиков SSDT](/archive/blogs/ssdt/)  
[Справочник по API DACFx](/previous-versions/sql/sql-server-2014/dn645454(v=sql.120))  
[Скачивание SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)