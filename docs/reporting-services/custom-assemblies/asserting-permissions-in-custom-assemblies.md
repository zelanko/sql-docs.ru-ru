---
title: Проверка разрешений в пользовательских сборках | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: custom-assemblies
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- secure calls [Reporting Services]
- custom assemblies [Reporting Services], permissions
- permission sets [Reporting Services]
- asserting permissions
- permissions [Reporting Services], custom assemblies
- limited permission sets
- security configuration files [Reporting Services]
ms.assetid: 3afb9631-f15e-405e-990b-ee102828f298
caps.latest.revision: 34
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 3d258a83f7c36baf7cab148661ad5cab91972233
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="asserting-permissions-in-custom-assemblies"></a>Проверка предположений о наличии разрешений в пользовательских сборках
  По умолчанию код пользовательской сборки выполняется с ограниченным набором разрешений **Execution**. В некоторых случаях требуется реализация пользовательских сборок, выполняющих безопасные вызовы к защищенным ресурсам внутри системы безопасности (например, к файлу или реестру). Для этого необходимо выполнить следующие действия.  
  
1.  Определить, какие именно разрешения необходимы, чтобы в коде можно было выполнить безопасный вызов. Если рассматриваемый метод входит в состав библиотеки [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], эти сведения должны быть включены в документацию по методу.  
  
2.  Предоставить пользовательской сборке необходимые разрешения путем внесения изменений в файлы конфигурации политики сервера отчетов. Дополнительные сведения о файлах конфигурации политик безопасности см. в разделе [Использование файлов политики безопасности служб Reporting Services](../../reporting-services/extensions/secure-development/using-reporting-services-security-policy-files.md).  
  
3.  Предположить, что требуемые разрешения являются частью метода, в котором выполняется безопасный вызов. Этот шаг является обязательным, так как код пользовательской сборки, вызываемый сервером отчетов, является частью хранилища сборки выражений отчета, которое по умолчанию используется с разрешением **Execution**. Набор разрешений **Execution** разрешает выполнение кода, но не использование защищенных ресурсов.  
  
4.  Обозначьте пользовательскую сборку атрибутом **AllowPartiallyTrustedCallersAttribute**, если она подписана строгим именем. Это необходимо по той причине, что пользовательские сборки вызываются из выражения отчета, которое является частью хранилища сборки выражений отчета, а ему по умолчанию не предоставляются права **FullTrust**. Таким образом, этот вызывающий код рассматривается как "частично доверенный". Дополнительные сведения см. в статье [Использование пользовательских сборок со строгими именами](../../reporting-services/custom-assemblies/using-strong-named-custom-assemblies.md).  
  
## <a name="implementing-a-secure-call"></a>Реализация безопасного вызова  
 Можно предоставить сборке конкретные разрешения путем изменения файлов конфигурации политик. Например, если создается пользовательская сборка для конвертирования валют, может потребоваться обеспечить чтение курсов валют из файла. Чтобы получить сведения о курсах, потребуется добавить к уже заданным разрешениям сборки дополнительное право доступа **FileIOPermission**. Внесите в файл конфигурации политики следующую дополнительную запись.  
  
```  
<PermissionSet class="NamedPermissionSet"  
   version="1"  
   Name="CurrencyRatesFilePermissionSet"  
   Description="A special permission set that grants read access to my currency rates file.">  
      <IPermission class="FileIOPermission"  
         version="1"  
         Read="C:\CurrencyRates.xml"/>  
      <IPermission class="SecurityPermission"  
         version="1"  
         Flags="Execution, Assertion"/>  
</PermissionSet>  
```  
  
 Затем добавьте группу кода, которая ссылается на этот набор разрешений.  
  
```  
<CodeGroup class="UnionCodeGroup"  
   version="1"  
   PermissionSetName="CurrencyRatesFilePermissionSet"  
   Name="MyNewCodeGroup"  
   Description="A special code group for my custom assembly.">  
   <IMembershipCondition class="UrlMembershipCondition"  
      version="1"  
      Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\MSSQL\Reporting Services\ReportServer\bin\CurrencyConversion.dll"/>  
</CodeGroup>  
```  
  
 Чтобы код получил соответствующее разрешение, необходимо подтвердить это разрешение в коде пользовательской сборки. Например, если требуется предусмотреть доступ только для чтения XML-файла C:\CurrencyRates.xml, то в метод следует добавить приведенный ниже код.  
  
```  
// C#  
FileIOPermission permission = new FileIOPermission(FileIOPermissionAccess.Read, @"C:\CurrencyRates.xml");  
try  
{  
   permission.Assert();  
   // Load the XML currency rates file  
   XmlDocument doc = new XmlDocument();  
   doc.Load(@"C:\CurrencyRates.xml");  
...  
```  
  
 Кроме того, подтверждение можно добавить и в качестве атрибута метода.  
  
```  
[FileIOPermissionAttribute(SecurityAction.Assert, Read=@"C:\CurrencyRates.xml")]  
```  
  
 Дополнительные сведения см. в разделе «Безопасность .NET Framework» документа «Руководство разработчика для платформы .NET Framework».  
  
## <a name="see-also"></a>См. также:  
 [Использование пользовательских сборок с отчетами](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
  
  
