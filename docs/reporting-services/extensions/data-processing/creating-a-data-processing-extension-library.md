---
title: "Создание библиотеки модулей обработки данных | Документы Microsoft"
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
- data processing extensions [Reporting Services], namespace assignments
- library [Reporting Services]
- assigning namespaces to extensions
ms.assetid: 82f4b71b-dd39-467d-8d8c-6771eb2b12de
caps.latest.revision: 39
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: f8b4f2e9254eb34745d36ccbffe36c21fdb0d75d
ms.contentlocale: ru-ru
ms.lasthandoff: 08/12/2017

---
# <a name="creating-a-data-processing-extension-library"></a>Создание библиотеки модулей обработки данных
  Каждому созданному модулю обработки данных служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] необходимо присвоить уникальное пространство имен. Кроме того, он должен быть встроен в библиотеку или файл сборки. Конкретное имя пространства имен не имеет значения, однако оно должно быть уникальным и не должно использоваться в других расширениях. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] использует пространства имен <xref:Microsoft.ReportingServices.DataProcessing> для модулей обработки данных, поставляемых со службами [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Для модулей обработки данных своей компании следует создавать собственные уникальные пространства имен.  
  
 В следующем примере показывается код, позволяющий начать создание модуля обработки данных служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], использующего пространства имен, содержащие интерфейсы обработки данных и служебные классы.  
  
```vb  
Imports System  
Imports Microsoft.ReportingServices.DataProcessing  
Imports Microsoft.ReportingServices.Interfaces  
  
Namespace CompanyName.ExtensionName  
   ...  
```  
  
```csharp  
using System;  
using Microsoft.ReportingServices.DataProcessing;  
using Microsoft.ReportingServices.Interfaces;  
  
namespace CompanyName.ExtensionName  
{  
   ...  
```  
  
 При компиляции модуля обработки данных служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] следует предоставить компилятору ссылку на файл Microsoft.ReportingServices.Interfaces.dll, поскольку в нем хранятся интерфейсы модуля обработки данных и классы. Пространство имен <xref:Microsoft.ReportingServices.DataProcessing> необходимо для реализации интерфейсов модулей обработки данных; пространство имен <xref:Microsoft.ReportingServices.Interfaces> необходимо для реализации интерфейса <xref:Microsoft.ReportingServices.Interfaces.IExtension>. Например, если бы все файлы, содержащие код (на языке C#), необходимый для реализации модуля обработки данных служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], находились в одном каталоге с расширением CS, то для компиляции файлов, хранимых в библиотеке CompanyName.ExtensionName.dll из данного каталога, нужно было выполнить следующую команду:  
  
```csharp  
csc /t:library /out:CompanyName.ExtensionName.dll *.cs /r:System.dll /r:Microsoft.ReportingServices.Interfaces.dll  
```  
  
 В следующем примере кода показана команда, который будет использоваться для [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] файлы с расширением. vb.  
  
```vb  
vbc /t:library /out:CompanyName.ExtensionName.dll *.vb /r:System.dll /r:Microsoft.ReportingServices.Interfaces.dll  
```  
  
> [!NOTE]  
>  Также можно проектировать, разрабатывать и строить модуль обработки данных в среде [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]. Дополнительные сведения о разработке сборок в среде [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] см. в документации по среде [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Модули служб Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Реализация модуля обработки данных](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Библиотека служб Reporting Services расширения](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
