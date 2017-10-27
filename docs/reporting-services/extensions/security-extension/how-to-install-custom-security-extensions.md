---
title: "Как установить настраиваемые модули безопасности | Документы Microsoft"
ms.custom: 
ms.date: 07/10/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: bfa0a35b-ccfb-4279-bae6-106c227c5f16
caps.latest.revision: 3
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 47182ebd082dfae0963d761e54c4045be927d627
ms.openlocfilehash: 58cfeef7d74e0641b965c307551f0fba4a7ff09c
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---

# <a name="how-to-install-custom-security-extensions"></a>Как установить настраиваемые модули безопасности

[!INCLUDE[ssrs-appliesto](../../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../../includes/ssrs-appliesto-pbirs.md)]

Службы Reporting Services 2016 появился новый веб-портал для размещаются новые интерфейсы API Odata и также новых рабочих нагрузок отчета, например мобильные отчеты и ключевые показатели Эффективности. Новый портал использует более новыми технологиями и изолирован от знакомый ReportingServicesService, выполнив в отдельном процессе. Этот процесс не является приложением ASP.NET в размещенных и таким образом разбивает данные, полученные с существующие пользовательские модули безопасности. Кроме того, не разрешать имеющиеся интерфейсы настраиваемых модулей безопасности для любого внешнего контекста передан в систему, оставляя исполнители, с единственным вариантом для проверки хорошо известных объектов глобальных ASP.NET всю необходимую внести некоторые изменения в интерфейсе.

## <a name="what-changed"></a>Что изменилось?

Появился новый интерфейс, может быть реализован предоставляющий IRSRequestContext, обеспечивая более общих свойств, используемых расширения для принятия решений, связанных с проверкой подлинности.

В предыдущих версиях диспетчер отчетов был внешнего интерфейса и могут быть настроены собственную настраиваемую страницу входа. В службы Reporting Services 2016 только на одной странице, размещенной reportserver поддерживается и выполняет проверку подлинности для обоих приложений.

## <a name="implementation"></a>Реализация

В предыдущих версиях расширения могли полагаться на общие предположения, что ASP.NET объекта будут доступны. Так как новый портал не работает в ASP.NET, расширение может достигнут проблемы с объектами, значение NULL.

Наиболее общий пример обращается к HttpContext.Current прочитать сведения о запросе, такие как заголовки и файлы cookie. Чтобы разрешить расширения принимать те же решения, мы представили новый метод в модуле, который предоставляет сведения о запросе и вызывается при проверке подлинности на портале. 

Расширения, придется реализовать <xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension2> интерфейс для использования этого. Расширения, должен реализовывать обе версии <xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension.GetUserInfo%2A> метод называется контекстом reportserver и других используемых в процессе webhost. В следующем примере показан один из простых реализаций для портала, где используется удостоверение разрешаемым reportserver.

``` 
public void GetUserInfo(IRSRequestContext requestContext, out IIdentity userIdentity, out IntPtr userId)
{
    userIdentity = null;
    if (requestContext.User != null)
    {
        userIdentity = requestContext.User;
    }

    // initialize a pointer to the current user id to zero
    userId = IntPtr.Zero;
}
```

## <a name="deployment-and-configuration"></a>Развертывание и настройка

Основные конфигурации, необходимые для настраиваемого модуля безопасности совпадают с предыдущими выпусками. Изменения необходимы для web.config и rsreportserver.config: Дополнительные сведения см. в разделе [Настройка нестандартной проверки подлинности или проверки подлинности форм на сервере отчетов](../../../reporting-services/security/configure-custom-or-forms-authentication-on-the-report-server.md).

Больше не отдельный файл web.config для диспетчера отчетов, портала будут наследовать те же параметры, как конечная точка reportserver.

## <a name="machine-keys"></a>Ключи компьютера

В случае проверки подлинности форм, в которой требуется расшифровка файла cookie проверки подлинности оба процесса необходимо настроить с помощью того же ключа машины алгоритма расшифровки. Это было шаг знакомы, которые раньше установки Reporting Services для работы в средах с горизонтальным масштабированием, но теперь является обязательным, даже для развертывания на одном компьютере.

Следует использовать определенный ключа проверки развертывания вы, существует несколько средств для формирования ключей, как и диспетчер служб Internet Information (IIS). Другие средства можно найти в Интернете.

### <a name="sql-server-reporting-services-2017-and-later"></a>SQL Server Reporting Services 2017 и более поздние версии

**\ReportServer\rsReportServer.config**

Добавьте под `<configuration>`.

```
<machineKey validationKey="[YOUR KEY]" decryptionKey=="[YOUR KEY]" validation="AES" decryption="AES" />
```

### <a name="sql-server-reporting-services-2016"></a>SQL Server Reporting Services 2016

**\ReportServer\web.config**

Добавьте под `<system.web>`.
    
```
    <machineKey validationKey="[YOUR KEY]" decryptionKey=="[YOUR KEY]" validation="AES" decryption="AES" />
```

**\RSWebApp\Microsoft.ReportingServices.Portal.WebHost.exe.config**

Добавьте под `<configuration>`.

```
    <system.web>
        <machineKey validationKey=="[YOUR KEY]" decryptionKey=="[YOUR KEY]" validation="AES" decryption="AES" />
    </system.web>
```

### <a name="power-bi-report-server"></a>Сервер отчетов Power BI

Эта функция доступна начиная с выпуска июня 2017 г. (сборка 14.0.600.301).

**\ReportServer\rsReportServer.config**

Добавьте под `<configuration>`.

```
<machineKey validationKey="[YOUR KEY]" decryptionKey=="[YOUR KEY]" validation="AES" decryption="AES" />
```

## <a name="configure-passthrough-cookies"></a>Настройка транзитных файлы cookie

Новый портал и reportserver обмениваться данными с использованием внутренней soap API-интерфейсы для некоторых операций (аналогично предыдущей версии диспетчера отчетов). При дополнительных куки-файлов необходимо передать на сервер с портала свойства PassThroughCookies по-прежнему доступен. Дополнительные сведения см. в разделе [настроить веб-портал для передачи файлов cookie проверки подлинности пользовательского](../../../reporting-services/security/configure-the-web-portal-to-pass-custom-authentication-cookies.md).

```
<UI>
   <CustomAuthenticationUI>
      <PassThroughCookies>
         <PassThroughCookie>sqlAuthCookie</PassThroughCookie>
      </PassThroughCookies>
   </CustomAuthenticationUI>
</UI>
```

## <a name="next-steps"></a>Следующие шаги

[Настройка нестандартной проверки подлинности или проверки подлинности форм на сервере отчетов](../../../reporting-services/security/configure-custom-or-forms-authentication-on-the-report-server.md)  
[Настройка диспетчера отчетов для передачи файлов cookie нестандартной проверки подлинности](https://msdn.microsoft.com/library/ms345241(v=sql.120).aspx)

Дополнительные вопросы? [Попробуйте задать вопрос на форуме служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)

