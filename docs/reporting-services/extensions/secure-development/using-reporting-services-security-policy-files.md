---
title: "Использование службы Reporting Services Security Policy Files | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- code groups [Reporting Services]
- CodeGroup elements
- configuration files [Reporting Services]
- code access security [Reporting Services], security policies
- security policies [Reporting Services]
- security configuration files [Reporting Services]
- named permission sets [Reporting Services]
ms.assetid: 2280fff6-3de7-44b1-87da-5db0ec975928
caps.latest.revision: 33
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 490f32a022606157376f7c8402d11cd8f027bc04
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="using-reporting-services-security-policy-files"></a>Использование файлов политики безопасности служб Reporting Services
  Службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] хранят сведения о политике безопасности компонентов в реестре и файлах конфигурации, которые копируются в файловую систему при установке. В этих файлах конфигурации хранится сочетание внутренней и пользовательской политики безопасности для сборок программного кода в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Три файла конфигурации соответствуют трем защищаемым компонентам [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]: сервер отчетов и службы Windows, диспетчера отчетов веб-приложения и окна предварительного просмотра конструктора отчетов.  
  
> [!NOTE]  
>  Существует два режима предварительного просмотра конструктора отчетов: на вкладке предварительного просмотра и всплывающее окно предварительного просмотра, открывающегося при запуске проекта отчета в **DebugLocal** режим. **Предварительного просмотра** tab не является защищаемым компонентом и не применяются параметры политики безопасности. Окно предварительного просмотра предназначено для имитации функциональной возможности сервера отчетов и поэтому имеет файл конфигурации политики безопасности, который необходимо изменить, если используются пользовательские сборки или пользовательские модули в конструкторе отчетов.  
  
 Файлы конфигурации политики безопасности содержат сведения класса безопасности, некоторые именованные наборы разрешений по умолчанию и группы программного кода для сборки в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Файлы конфигурации политики безопасности служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] напоминают файл Security.config, который определяет иерархию группы кода и наборы разрешений, связанные с политиками на уровне компьютера и предприятия в [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Этот файл находится в C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\CONFIG\security.config.  
  
## <a name="policy-files-in-reporting-services"></a>Файлы политик в службах Reporting Services  
 В следующей таблице приводится список файлов конфигурации в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], их расположение (предполагается установка по умолчанию) и соответствующие функции.  
  
|Имя файла|Расположение (установка по умолчанию)|Description|  
|---------------|---------------------------------------|-----------------|  
|rssrvpolicy.config|C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer|Файл конфигурации политики безопасности сервера отчетов. Эти политики безопасности в первую очередь касаются выражений отчетов и пользовательских сборок после развертывания отчета на сервере отчетов. Этот файл также влияет на пользовательские данные, доставку, модули подготовки отчета и безопасности, развернутые на сервере отчетов.|  
|rsmgrpolicy.config|C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportManager|Файл конфигурации политики диспетчера отчетов. Эти политики безопасности касаются всех сборок, расширяющих функции диспетчера отчетов, например расширения подписки для пользовательских модулей доставки.|  
|rspreviewpolicy.config|C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies|Файл конфигурации политики изолированного предварительного просмотра для конструктора отчетов. Эти политики безопасности касаются пользовательских сборок и выражений отчета, которые используются в отчете во время предварительного просмотра и разработки. Они влияют также на пользовательские модули, например модули обработки данных, развернутые в конструкторе отчетов.|  
  
## <a name="modifying-configuration-files"></a>Изменение файлов конфигурации  
 Параметры конфигурации задаются либо как элементы XML, либо как атрибуты. Если вы знакомы с XML и файлами конфигурации, то можете использовать редактор текста или кода для настройки пользовательских параметров. Файлы конфигурации политики безопасности содержат сведения о иерархии группы программных кодов и набора разрешений, связанных с уровнем политики в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Для изменения политики безопасности в файле Security.config рекомендуется использовать вначале программу настройки .NET Framework (Mscorcfg.msc) или программу политики управления доступом для кода (Caspol.exe), чтобы изменения политики соответствовали допустимым XML-элементам конфигурации для файлов политик. Сразу после этого можно вырезать и вставлять в файл политики новые группы кодов и наборы разрешений из файла Security.config для компонентов, к которым добавляются разрешения на программный код.  
  
> [!IMPORTANT]  
>  До внесения изменений необходимо создать резервные копии файлов конфигурации политик.  
  
 При таком подходе достигается следующее. Во-первых, это дает возможность использовать визуальные средства при создании групп кодов и наборов разрешений для служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Это гораздо легче, чем писать XML-элементы конфигурации с самого начала. Во-вторых, обеспечивает сохранность файлов конфигурации политики безопасности при неправильных XML-элементах и атрибутах. Дополнительные сведения о программе политики управления доступом для кода см. в MSDN, раздел «Использование файлов политики безопасности служб Reporting Services».  
  
 Перед изменением файлов конфигурации политик следует прочитать все сведения, изложенные в этом разделе, а также относящиеся к нему темы. Изменение конфигураций политик служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] может в значительной степени повлиять на безопасность выполнения компонентами служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] внешних программных модулей.  
  
## <a name="placement-of-codegroup-elements-for-extensions"></a>Размещение элементов CodeGroup для модулей  
 Размещение элементов CodeGroup в файле политики безопасности имеет большое значение. Для модулей и разработанных пользовательских сборок рекомендуется размещать группы программного кода непосредственно под элементом URL-членства «$CodeGen$/*», как показано ниже:  
  
```  
<CodeGroup  
    class="UnionCodeGroup"  
    version="1"  
    PermissionSetName="FullTrust">  
    <IMembershipCondition   
        class="UrlMembershipCondition"  
        version="1"  
        Url="$CodeGen$/*"  
    />  
</CodeGroup>  
<CodeGroup   
    class="UnionCodeGroup"  
    version="1"  
    PermissionSetName="FullTrust"  
    Name="MyCustomCodeGroup"  
    Description="Code group for my custom extension">  
        <IMembershipCondition class="UrlMembershipCondition"  
        version="1"  
        Url="C:\Program Files\Microsoft SQL Server\MSSQL\Reporting Services\ReportServer\bin\MyAssembly.dll"  
        />  
</CodeGroup>  
```  
  
 Дополнительные группы программных кодов можно размещать одну за другой.  
  
## <a name="see-also"></a>См. также:  
 [Основные сведения о политиках безопасности](../../../reporting-services/extensions/secure-development/understanding-security-policies.md)  
  
  
