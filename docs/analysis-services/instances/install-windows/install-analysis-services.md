---
title: "Установка служб Analysis Services | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/20/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cd6ac80d-b735-4e3e-a024-489f1409ad33
caps.latest.revision: 20
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 19
---
# Установка служб Analysis Services
  [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] — сервер аналитических баз данных для размещения табличных моделей, многомерных кубов и моделей интеллектуального анализа данных, которые можно получить из отчетов, электронных таблиц и панелей мониторинга.  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] имеет несколько экземпляров. Это значит, что вы можете установить больше одной копии [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] на одном компьютере или использовать новые и старые версии параллельно. Все установленные экземпляры работают в одном из трех режимов, определяемых во время установки: многомерный и интеллектуальный анализ данных, а также режим для работы с табличными моделями или моделями SharePoint. Если вы хотите использовать несколько режимов, вам потребуется отдельный экземпляр для каждого из них.  
  
 После установки сервера в определенном режиме вы можете использовать его для размещения решений, поддерживаемых этим режимом. Например, сервер в табличном режиме необходим, если требуется сетевой доступ к данным табличной модели.  
  
## Получение средств и конструкторов  
 Программа установки SQL Server больше не устанавливает конструкторы моделей и средства управления, используемые для разработки решений и администрирования сервера. В этом выпуске для средств предусмотрена отдельная установка — см. следующие ссылки:  
  
-   [Скачать SQL Server Management Studio для SQL Server 2016](https://msdn.microsoft.com/en-US/library/mt238290.aspx)  
  
-   [Скачать SQL Server Data Tools для SQL Server 2016](https://msdn.microsoft.com/en-US/library/mt204009.aspx)  
  
 Для работы с данными и экземплярами служб Analysis Services вам потребуется как Management Studio, так и SQL Server Data Tools. Средства можно установить в любом расположении — не забудьте только настроить порты на сервере перед подключением. Дополнительные сведения см. в разделе [Configure the Windows Firewall to Allow Analysis Services Access](../../../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md) .  
  
## Установка с помощью мастера  
 В следующем списке приведены страницы в мастере установки SQL Server, используемые при установке служб Analysis Services.  
  
1.  Выберите **Службы Analysis Services** в дереве компонентов в программе установки.  
  
     ![Setup feature tree showing Analsyis Services](../../../analysis-services/instances/install-windows/media/ssas-setupas.gif "Setup feature tree showing Analsyis Services")  
  
2.  Если вам нужен табличный экземпляр, на странице "Настройка служб Analysis Services" обязательно выберите **Табличный режим** . В противном случае оставьте значение по умолчанию — **Режим многомерных данных и интеллектуального анализа данных**.  
  
     ![Setup page with Analysis Services config options](../../../analysis-services/instances/install-windows/media/ssas-setupasconfig.png "Setup page with Analysis Services config options")  
  
 Режим многомерных данных и интеллектуального анализа данных использует MOLAP в качестве стандартного хранилища для моделей, развертываемых в службах Analysis Services. После развертывания на сервере вы можете настроить решение для использования ROLAP, если планируете выполнять запросы непосредственно к реляционной базе данных, а не хранить данные запроса в многомерной базе данных служб Analysis Services.  
  
 Табличный режим использует подсистему VertiPaq аналитики в памяти xVelocity, которая является хранилищем по умолчанию для табличных моделей, развертываемых в службах Analysis Services. После развертывания решений табличных моделей на сервере можно выборочно настроить в табличных решениях использование дискового хранилища DirectQuery в качестве альтернативы хранилищу, размещенному в оперативной памяти.  
  
 Управление памятью и параметры ввода-вывода можно настраивать, чтобы добиться более высокой производительности при использовании нестандартных режимов хранения. Дополнительные сведения см. в статье [Свойства сервера в службах Analysis Services](../../../analysis-services/server-properties/server-properties-in-analysis-services.md).  
  
## Установка из командной строки  
 В программе установки SQL Server предусмотрен новый параметр (**ASSERVERMODE**), который определяет режим сервера. В приведенном ниже примере показана установка служб Analysis Services в табличном режиме сервера из командной строки.  
  
```  
  
Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /FEATURES=AS /ASSERVERMODE=TABULAR /INSTANCENAME=ASTabular /INDICATEPROGRESS/ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
```  
  
 Значение**INSTANCENAME** должно иметь длину менее 17 символов.  
  
 Все заполнители значений учетных записей должны быть заменены на действительные учетные записи и пароли.  
  
 Параметр **ASSERVERMODE** учитывает регистр.  Все значения должны задаваться в верхнем регистре. В следующей таблице приведены допустимые значения параметра **ASSERVERMODE**.  
  
|Значение|Описание|  
|-----------|-----------------|  
|MULTIDIMENSIONAL|Это значение по умолчанию. Если не задать значение **ASSERVERMODE**, сервер будет установлен в многомерном режиме.|  
|POWERPIVOT|Это значение является необязательным. На практике, если задан параметр **ROLE**, режим сервера автоматически получает значение 1, что делает **ASSERVERMODE** необязательным в установке [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] для SharePoint. Дополнительные сведения см. в статье [Установка Power Pivot из командной строки](http://msdn.microsoft.com/ru-ru/7f1f2b28-c9f5-49ad-934b-02f2fa6b9328).|  
|TABULAR|Это значение является обязательным при установке служб Analysis Services в табличном режиме из командной строки.|  
  
## См. также:  
 [Определение режима работы сервера экземпляра служб Analysis Services](../../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)   
 [Преобразование табличной базы данных в памяти в DirectQuery в SQL Server Management Studio (SSMS)](../Topic/Convert%20an%20in-memory%20Tabular%20Database%20to%20DirectQuery%20in%20SQL%20Server%20Management%20Studio%20\(SSMS\).md)   
 [Табличное моделирование (SSMS)](../Topic/Tabular%20Modeling%20\(SSAS\).md)  
  
  