---
title: Поддержка Azure Active Directory в SQL Server Data Tools (SSDT) | Документация Майкрософт
ms.custom: ''
ms.date: 03/05/2018
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssdt
ms.reviewer: ''
ms.suite: sql
ms.technology:
- tools-ssdt
ms.tgt_pltfrm: ''
ms.topic: article
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Active
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 7ea6a2c1a0617eaa7855470f8f8edf87308c9d22
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="azure-active-directory-support-in-sql-server-data-tools-ssdt"></a>Поддержка Azure Active Directory в SQL Server Data Tools (SSDT)

[!INCLUDE[appliesto-xx-asdb-xxxx-xxx-md.md](../includes/appliesto-xx-asdb-xxxx-xxx-md.md)]

SQL Server Data Tools предоставляет несколько методов проверки подлинности [Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-whatis).

![Диалоговое окно подключения SSDT](media/azure-active-directory/interactive.png)

## <a name="active-directory-password-authentication"></a>Проверка подлинности с помощью пароля Active Directory

Проверка пароля Active Directory — это механизм подключения к базе данных Azure SQL с помощью удостоверений в Azure Active Directory (Azure AD).  Используйте этот метод для подключения, если вы вошли в Windows с учетными данными из домена, не включенного в федерацию с Azure, или если применяется проверка подлинности Azure AD на базе первоначального домена или домена клиента. Дополнительные сведения см. в статье [Подключение к базе данных SQL с использованием проверки подлинности Azure Active Directory](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication).  

## <a name="active-directory-integrated-authentication"></a>Интегрированная проверка подлинности Active Directory

Интегрированная проверка подлинности Active Directory — это механизм подключения к базе данных Azure SQL с помощью удостоверений в Azure Active Directory. Используйте этот метод для подключения, если вы вошли в Windows с учетными данными Azure Active Directory из федеративного домена. Дополнительные сведения см. в статье [Подключение к базе данных SQL с использованием проверки подлинности Azure Active Directory](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication).

## <a name="active-directory-interactive-authentication-preview"></a>Интерактивная проверка подлинности Active Directory (предварительная версия)

В SSDT предусмотрен новый метод проверки подлинности для подключения к базе данных Azure SQL — **интерактивная проверка подлинности Active Directory**.


> [!NOTE]
> Этот метод проверки подлинности доступен при подключении к SSDT в [Visual Studio 2017 (предварительная версия)](https://www.visualstudio.com/vs/preview/). Для него нужно установить [предварительную версию .NET 4.7.2 (KB4038188)](https://go.microsoft.com/fwlink/?linkid=867317) на компьютере, где запущены инструменты SSDT. Если предварительная версия .NET 4.7.2 (KB4038188) не установлена, параметр интерактивной проверки подлинности Active Directory не будет доступен.


Этот метод поддерживает интерактивную проверку подлинности, что позволяет применять многофакторную идентификацию (MFA) Azure Active Directory (AD) для проверки подлинности в базе данных Azure SQL. Он поддерживается для пользователей Azure AD из собственного и федеративного домена, гостевых пользователей из других учетных записей (включая пользователей B2B, а также пользователей с учетными записями Майкрософт и сторонними учетными записями, например @outlook.com, @hotmail.com, @live.com и @gmail.com). Если выбран этот метод, нужно указать **имя пользователя**. Поле пароля поле будет отключено. 

При *интерактивной проверке подлинности Active Directory* откроется окно проверки подлинности, в котором пользователи должны ввести пароль вручную.

![Диалоговое окно входа](media/azure-active-directory/sign-in.png)

Принудительное применение MFA реализуется Azure AD через это дополнительное всплывающее окно MFA при проверке подлинности.

> [!NOTE]
> Так как при *интерактивной проверке подлинности Active Directory* пользователи должны вручную (интерактивно) вводить свой пароль, этот метод не рекомендуется для автоматических рабочих процессов.


## <a name="known-issues-and-limitations"></a>Известные проблемы и ограничения

- *Интерактивная проверка подлинности Active Directory* поддерживается только при подключении к базе данных Azure SQL. Она не поддерживается для SQL Server (в локальной среде или на виртуальной машине) или хранилища данных SQL Azure.
- *Интерактивная проверка подлинности Active Directory* не поддерживается в диалоговом окне подключения в *обозревателе сервера*. Вам нужно подключиться к *обозревателю объектов SQL Server* с помощью SSDT.
- Интеграция единого входа с текущей учетной записью Visual Studio, которая использовалась для входа, не поддерживается для SSDT.
- Пакет SQLPackage.exe, установленный в каталоге Extensions во время установки Visual Studio, не предназначен для использования в этом расположении. Чтобы использовать SQLpackage.exe с AAD, перейдите по адресу https://www.microsoft.com/en-us/download/details.aspx?id=55088 
- SSDT Data Compare не поддерживается для проверки подлинности AAD, включая новый метод проверки подлинности.  





## <a name="see-also"></a>См. также:  
[Универсальная проверка подлинности для Базы данных SQL и хранилища данных SQL (поддержка SSMS для MFA)](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication)  
[Настройка аутентификации Azure Active Directory и управление ею с использованием базы данных SQL или хранилища данных SQL](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication-configure)  
[SQL Server Data Tools в Visual Studio](https://msdn.microsoft.com/library/hh272686(v=vs.103).aspx)  
[Форум MSDN по SSDT](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=ssdt)  
[Блог группы разработчиков SSDT](http://blogs.msdn.com/b/ssdt/)  
[Справочник по API DACFx](https://msdn.microsoft.com/library/dn645454.aspx)  
[Скачивание SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)  
