---
title: Azure Active Directory в SQL Server Data Tools (SSDT) | Документы Майкрософт
ms.custom: ''
ms.date: 05/31/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: ssdt
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 4d607a7fa7dd9ce91c5ca97bf144f89e1624ed93
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62660160"
---
# <a name="azure-active-directory-support-in-sql-server-data-tools-ssdt"></a>Поддержка Azure Active Directory в SQL Server Data Tools (SSDT)

[!INCLUDE[appliesto-xx-asdb-asdb-xxx-md.md](../includes/appliesto-xx-asdb-asdw-xxx-md.md)]

SQL Server Data Tools (SSDT) предоставляет несколько методов проверки подлинности [Azure Active Directory (Azure AD)](https://docs.microsoft.com/azure/active-directory/active-directory-whatis).

![Диалоговое окно подключения SSDT](media/azure-active-directory/interactive.png)

#### <a name="which-azure-sql-products"></a>Какие продукты SQL Azure?

В этой статье рассматривается Azure AD для следующего списка *продуктов SQL Azure*  в [облаке Azure](https://azure.microsoft.com/).

- База данных SQL Azure
- Хранилище данных SQL Azure

## <a name="active-directory-password-authentication"></a>Проверка подлинности с помощью пароля Active Directory

*Проверка подлинности с помощью пароля Active Directory* — это механизм подключения к перечисленным ранее продуктам SQL Azure. Механизм использует удостоверения Azure Active Directory (Azure AD). Используйте этот метод для подключения, если:

- вы вошли в Windows с помощью учетных данных из домена, не включенного в федерацию с Azure; или
- вы используете проверку подлинности Azure AD с Azure AD на базе первоначального домена или домена клиента.

Дополнительные сведения см. в статье [Подключение к базе данных SQL с использованием проверки подлинности Azure Active Directory](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication).  

## <a name="active-directory-integrated-authentication"></a>Интегрированная проверка подлинности Active Directory

*Интегрированная проверка подлинности Active Directory* — это механизм подключения к перечисленным продуктам SQL Azure с помощью удостоверений в Azure Active Directory (Azure AD). Используйте этот метод для подключения, если вы вошли в Windows с учетными данными Azure Active Directory из федеративного домена. Дополнительные сведения см. в статье [Подключение к базе данных SQL с использованием проверки подлинности Azure Active Directory](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication).

## <a name="active-directory-interactive-authentication"></a>Интерактивная проверка подлинности Active Directory

*Интерактивная проверка подлинности Active Directory* доступна при подключении к перечисленным продуктам SQL Azure с помощью SSDT, но только с [.NET Framework 4.7.2](https://docs.microsoft.com/dotnet/api/?view=netframework-4.7.2) или более поздней версии.

- [Скачайте и установите для .NET Framework (любую версию)](https://www.microsoft.com/net/download/all).
- [Visual Studio 2017 версия 15.6](https://docs.microsoft.com/visualstudio/releasenotes/vs2017-relnotes) или более поздняя.

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

[Универсальная проверка подлинности для Базы данных SQL и хранилища данных SQL (поддержка SSMS для MFA)](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication)  
[Настройка аутентификации Azure Active Directory и управление ею с использованием базы данных SQL или хранилища данных SQL](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication-configure)  
[Форум MSDN по SSDT](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=ssdt)  
[Блог группы разработчиков SSDT](https://blogs.msdn.com/b/ssdt/)  
[Справочник по API DACFx](https://msdn.microsoft.com/library/dn645454.aspx)  
[Скачивание SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)  
