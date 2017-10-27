---
title: "Создание библиотеки модулей доставки | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
- delivery extensions [Reporting Services], namespace assignments
- library [Reporting Services]
- assigning namespaces to extensions
ms.assetid: 63b32f93-4bab-4b07-bd72-39a47aca1cda
caps.latest.revision: 36
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: bcfb5b69df148108531e9e5b843f127af0e3fbb4
ms.contentlocale: ru-ru
ms.lasthandoff: 08/12/2017

---
# <a name="creating-a-delivery-extension-library"></a>Создание библиотеки модулей доставки
  Каждому созданному модулю доставки служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] необходимо присвоить уникальное пространство имен. Также он должен быть встроен в библиотеку или файл сборки. Конкретное имя пространства имен не имеет значения, однако оно должно быть уникальным и не должно использоваться в других расширениях. Для модулей доставки своей компании следует создавать собственные уникальные пространства имен.  
  
 В следующем примере показывается код, позволяющий начать создание модуля доставки служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], использующего пространства имен, содержащие интерфейсы доставки и служебные классы.  
  
```vb  
Imports System  
Imports Microsoft.ReportingServices.Interfaces  
  
Namespace CompanyName.ExtensionName  
   ...  
```  
  
```csharp  
using System;  
using Microsoft.ReportingServices.Interfaces;  
  
namespace CompanyName.ExtensionName  
{  
   ...  
```  
  
 При компиляции модуля доставки служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] следует предоставить компилятору ссылку на файл Microsoft.ReportingServices.Interfaces.dll, поскольку в нем хранятся интерфейсы модуля доставки и классы. Пространство имен <xref:Microsoft.ReportingServices.Interfaces> необходимо для реализации интерфейсов <xref:Microsoft.ReportingServices.Interfaces.IExtension>, <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> и др. Например, если все файлы, содержащие код для реализации [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] модуль доставки, написанные на C# находились в одном каталоге с расширением CS, следующая команда будет выдан для компиляции файлов, хранящихся в CompanyName.ExtensionName.dll из данного каталога.  
  
```csharp  
csc /t:library /out:CompanyName.ExtensionName.dll *.cs /r:System.dll   
/r:Microsoft.ReportingServices.Interfaces.dll  
```  
  
 В следующем примере кода показана команда, который будет использоваться для [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] файлы с расширением. vb.  
  
```vb  
vbc /t:library /out:CompanyName.ExtensionName.dll *.vb /r:System.dll   
/r:Microsoft.ReportingServices.Interfaces.dll  
```  
  
> [!NOTE]  
>  Также можно проектировать, разрабатывать и строить модуль доставки в среде [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]. Дополнительные сведения о разработке сборок в среде [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] см. в документации по среде [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Модули служб Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Реализация модуля доставки](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Библиотека служб Reporting Services расширения](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  

