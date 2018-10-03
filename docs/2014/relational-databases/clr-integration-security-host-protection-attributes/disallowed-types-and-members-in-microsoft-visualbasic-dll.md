---
title: Запрещенные типы и элементы в Microsoft.VisualBasic.dll | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- host protection attributes [CLR integration]
- common language runtime [SQL Server], host protection attributes
ms.assetid: 45f55646-4bf1-4493-9f72-d1363c9a9ac6
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 7905d620cb9bff24f92e73929322ed995a1d8ba0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48090100"
---
# <a name="disallowed-types-and-members-in-microsoftvisualbasicdll"></a>Запрещенные типы и элементы в Microsoft.VisualBasic.dll
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] общего программирования интеграции (со средой CLR) языка не допускает использования типа или члена, имеющего `HostProtectionAttribute` , указывающий `System.Security.Permissions.HostProtectionResource` перечисление со значением `ExternalProcessMgmt`, `ExternalThreading`, `MayLeakOnAbort`, `SecurityInfrastructure`, `SelfAffectingProcessMgmnt`, `SelfAffectingThreading`, **SharedState**, `Synchronization`, или `UI`. В следующей таблице перечислены элементы и типы сборки `Microsoft.VisualBasic.dll`, значения атрибута защиты узла которых недопустимы.  
  
> [!NOTE]  
>  Этот список был создан из поддерживаемых сборок. Дополнительные сведения см. в разделе [поддерживаемые библиотеки платформы .NET Framework](../clr-integration/database-objects/supported-net-framework-libraries.md).  
  
|**Тип или член**|**Значения атрибутов защиты узла**|  
|------------------------|------------------------|  
|Microsoft.VisualBasic.ApplicationServices.ApplicationBase|ExternalProcessMgmt|  
|Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeCulture()|ExternalProcessMgmt|  
|Microsoft.VisualBasic.ApplicationServices.ApplicationBase.get_Info()|ExternalProcessMgmt|  
|Microsoft.VisualBasic.ApplicationServices.AssemblyInfo|ExternalProcessMgmt|  
|Microsoft.VisualBasic.ApplicationServices.BuiltInRoleConverter|SharedState|  
|Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase|ExternalProcessMgmt|  
|Microsoft.VisualBasic.ApplicationServices.User|ExternalProcessMgmt|  
|Microsoft.VisualBasic.ApplicationServices.WebUser|ExternalProcessMgmt|  
|Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase|ExternalProcessMgmt|  
|Microsoft.VisualBasic.CompilerServices.HostServices|SharedState|  
|Microsoft.VisualBasic.CompilerServices.ProjectData.EndApp()|SelfAffectingProcessMgmt|  
|Microsoft.VisualBasic.CompilerServices.Utils.SetCultureInfo()|SelfAffectingThreading|  
|Microsoft.VisualBasic.DateAndTime.set_DateString()|ExternalProcessMgmt|  
|Microsoft.VisualBasic.DateAndTime.set_TimeOfDay()|ExternalProcessMgmt|  
|Microsoft.VisualBasic.DateAndTime.set_TimeString()|ExternalProcessMgmt|  
|Microsoft.VisualBasic.DateAndTime.set_Today()|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Devices.Audio|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Devices.Clock|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Devices.Computer|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Devices.ComputerInfo|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Devices.Keyboard|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Devices.Mouse|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Devices.Network|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Devices.Ports|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Devices.ServerComputer|ExternalProcessMgmt|  
|Microsoft.VisualBasic.FileIO.FileSystem|ExternalProcessMgmt|  
|Microsoft.VisualBasic.FileIO.SpecialDirectories|ExternalProcessMgmt|  
|Microsoft.VisualBasic.FileIO.TextFieldParser..ctor()|ExternalProcessMgmt|  
|Microsoft.VisualBasic.FileSystem|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Interaction.CreateObject()|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Interaction.DeleteSetting()|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Interaction.GetObject()|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Interaction.InputBox()|UI|  
|Microsoft.VisualBasic.Interaction.MsgBox()|UI|  
|Microsoft.VisualBasic.Logging.AspLog|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Logging.FileLogTraceListener..ctor()|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Logging.FileLogTraceListener.Close()|Синхронизация|  
|Microsoft.VisualBasic.Logging.FileLogTraceListener.Dispose()|Синхронизация|  
|Microsoft.VisualBasic.Logging.FileLogTraceListener.Flush()|Синхронизация|  
|Microsoft.VisualBasic.Logging.FileLogTraceListener.GetSupportedAttributes()|Синхронизация|  
|Microsoft.VisualBasic.Logging.FileLogTraceListener.TraceData()|Синхронизация|  
|Microsoft.VisualBasic.Logging.FileLogTraceListener.TraceEvent()|Синхронизация|  
|Microsoft.VisualBasic.Logging.FileLogTraceListener.Write()|Синхронизация|  
|Microsoft.VisualBasic.Logging.FileLogTraceListener.WriteLine()|Синхронизация|  
|Microsoft.VisualBasic.Logging.Log|ExternalProcessMgmt|  
|Microsoft.VisualBasic.MyServices.ClipboardProxy|ExternalProcessMgmt|  
|Microsoft.VisualBasic.MyServices.FileSystemProxy|ExternalProcessMgmt|  
|Microsoft.VisualBasic.MyServices.RegistryProxy|ExternalProcessMgmt|  
|Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy|ExternalProcessMgmt|  
  
## <a name="see-also"></a>См. также  
 [Атрибуты защиты узла и программирование интеграции со средой CLR](host-protection-attributes-and-clr-integration-programming.md)   
 [Запрещенные типы и элементы в библиотеке mscorlib.dll](disallowed-types-and-members-in-mscorlib-dll.md)   
 [Запрещенные типы и элементы в System.dll](disallowed-types-and-members-in-system-dll.md)   
 [Запрещенные типы и элементы в библиотеке System.Data.dll](disallowed-types-and-members-in-system-data-dll.md)   
 [Недопустимые типы и элементы в библиотеке System.Core.dll](disallowed-types-and-members-in-system-core-dll.md)  
  
  
