---
title: Запрещенные типы и элементы в библиотеке System.Data.dll | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- host protection attributes [CLR integration]
- common language runtime [SQL Server], host protection attributes
ms.assetid: ee5f55e9-fbef-401a-be18-a2e5873c8720
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 4233bc1ddd98d6fe678d9d37f1acd7a4b66b687e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48143204"
---
# <a name="disallowed-types-and-members-in-systemdatadll"></a>Недопустимые типы и элементы в библиотеке System.Data.dll
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] общего программирования интеграции (со средой CLR) языка не допускает использования типа или члена, имеющего `HostProtectionAttribute` , указывающий `System.Security.Permissions.HostProtectionResource` перечисление со значением `ExternalProcessMgmt`, `ExternalThreading`, `MayLeakOnAbort`, `SecurityInfrastructure`, `SelfAffectingProcessMgmnt`, `SelfAffectingThreading`, **SharedState**, `Synchronization`, или `UI`. В следующей таблице приводится перечень членов и типов сборки System.Data.dll, чьи значения атрибутов защиты узла недопустимы.  
  
> [!NOTE]  
>  Этот список был создан из поддерживаемых сборок. Дополнительные сведения см. в разделе [поддерживаемые библиотеки платформы .NET Framework](../clr-integration/database-objects/supported-net-framework-libraries.md).  
  
|Тип или элемент|Значения атрибутов защиты узла|  
|--------------------|--------------------|  
|System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery()|ExternalThreading|  
|System.Data.SqlClient.SqlCommand.BeginExecuteReader()|ExternalThreading|  
|System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader()|ExternalThreading|  
|System.Data.SqlClient.SqlDependency..ctor()|ExternalThreading|  
|System.Data.SqlClient.SqlDependency.Start()|ExternalThreading|  
|System.Data.SqlClient.SqlDependency.Stop()|ExternalThreading|  
|System.Data.TypedDataSetGenerator|SharedState, Synchronization|  
|System.Xml.XmlDataDocument|Синхронизация|  
  
## <a name="see-also"></a>См. также  
 [Атрибуты защиты узла и программирование интеграции со средой CLR](host-protection-attributes-and-clr-integration-programming.md)   
 [Запрещенные типы и элементы в Microsoft.VisualBasic.dll](disallowed-types-and-members-in-microsoft-visualbasic-dll.md)   
 [Запрещенные типы и элементы в библиотеке mscorlib.dll](disallowed-types-and-members-in-mscorlib-dll.md)   
 [Запрещенные типы и элементы в System.dll](disallowed-types-and-members-in-system-dll.md)   
 [Недопустимые типы и элементы в библиотеке System.Core.dll](disallowed-types-and-members-in-system-core-dll.md)  
  
  
