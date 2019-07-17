---
title: Протоколы для свойств MSSQLSERVER (вкладка "Дополнительно") | Документы Майкрософт
ms.custom: ''
ms.date: 01/24/2019
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: abd5ca68-825f-4c07-b27c-3b3a79d03d74
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: craigg
ms.openlocfilehash: a8ff4689c4b9746178d9030d82b9ed8fccdb961f
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733421"
---
# <a name="protocols-for-mssqlserver-properties-advanced-tab"></a>Протоколы для свойств MSSQLSERVER (вкладка «Дополнительно»)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Используйте вкладку **Дополнительно** в диалоговом окне **Протоколы для свойств MSSQLSERVER** , чтобы настроить функцию **Расширенная защита для проверки подлинности** для компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]. **Расширенная защита** представляет собой функцию сетевых компонентов, реализованную операционной системой. **Расширенная защита** доступна в Windows 7 и Windows Server 2008 R2 и включена в пакеты обновления для операционных систем предыдущих версий. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при помощи **Расширенная защита**. Для включения определенных функций **Расширенной защиты** необходимо установить на вкладке **Флаги** флажок **Принудительное шифрование** .

> [!IMPORTANT]  
> В Windows **Расширенная защита** не включается по умолчанию. Сведения о том, как включить **расширенной защиты**, см. в следующем:
> - [Расширенная защита Windows \<extendedProtection\>](https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/windowsauthentication/extendedprotection/)
> - [Общие сведения о расширенной защите для проверки подлинности](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/extended-protection-for-authentication-overview)

Дополнительные сведения о настройке других служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и полное описание функции **Расширенная защита**см. на сайте [Microsoft.com](https://go.microsoft.com/fwlink/?LinkId=177752).

**Расширенная защита** полностью поддерживается [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, начиная с [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]. Поддержка **расширенной защиты** для других поставщиков клиентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в настоящее время отсутствует.

## <a name="options"></a>Параметры

### <a name="extended-protection"></a>расширенную защиту

Возможны три значения.  

- **Отключение**: означает, что **расширенной защиты** отключена. Экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] принимает соединения от всех клиентов, независимо от того, является клиент защищенным или нет. При задании**Выкл.** обеспечивается совместимость с предыдущими версиями операционных систем и версиями без установленных обновлений, но этот режим отличается меньшей безопасностью. Этот режим можно использовать, если известно, что клиентские операционные системы не поддерживают расширенную защиту.

- **Разрешено**. Функция **Расширенная защита** требуется для установки подключений от операционных систем, поддерживающих функцию **Расширенная защита**. Соединения незащищенных клиентских приложений, выполняемых на защищенных клиентских операционных системах, отклоняются. **Расширенная защита** пропускается для соединений от незащищенных операционных систем. Этот параметр обеспечивает более высокий уровень защиты, чем **Выкл**, но, тем не менее, не обеспечивает самый высокий уровень защиты. Этот параметр следует использовать в смешанных средах, где одни операционные системы и приложения поддерживают **расширенную защиту** , а другие — нет.

- **Требуется**: означает, что для подключения был принят, он должны поступать из защищенных приложений на защищенных операционных систем. Этот параметр обеспечивает максимальную защиту из трех параметров. Но соединений от операционных систем, которые не поддерживают **расширенной защиты** не смогут подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

### <a name="accepted-ntlm-spns"></a>Принятые имена участников-служб NTLM

Экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может определяться несколько NTLM имя субъекта-службы (SPN). Как набор строк, разделенных точкой с запятой список имен участников-служб. Например, значение **MSSQLSvc/HostName1.Contoso.com;MSSQLSvc/HostName2.Contoso.com** указывает, что разрешены клиенты, пытающиеся подключиться к SPN с именами **MSSQLSvc/HOST1.Contoso.com** или **MSSQLSvc/HOST2.Contoso.com**. Максимальная длина этой переменной 2048 символов.

## <a name="see-also"></a>См. также:

[Расширенная защита для проверки подлинности служб Reporting Services](../../reporting-services/security/extended-protection-for-authentication-with-reporting-services.md)

