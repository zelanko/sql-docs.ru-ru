---
title: Недопустимые типы и члены в System. Data. dll | Документация Майкрософт
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62874368"
---
# <a name="disallowed-types-and-members-in-systemdatadll"></a>Недопустимые типы и элементы в библиотеке System.Data.dll
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Программирование в среде `HostProtectionAttribute` CLR запрещает использование типа или члена, имеющего тип, который задает `System.Security.Permissions.HostProtectionResource` перечисление со значением `ExternalProcessMgmt`, `ExternalThreading`, `MayLeakOnAbort`, `SecurityInfrastructure`, `SelfAffectingProcessMgmnt`, `SelfAffectingThreading`, **шаредстате**, `Synchronization`или. `UI` В следующей таблице приводится перечень членов и типов сборки System.Data.dll, чьи значения атрибутов защиты узла недопустимы.  
  
> [!NOTE]  
>  Этот список был создан из поддерживаемых сборок. Дополнительные сведения см. в разделе [supported .NET Framework librarys](../clr-integration/database-objects/supported-net-framework-libraries.md).  
  
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
  
## <a name="see-also"></a>См. также:  
 [Атрибуты защиты узла и программирование интеграции со средой CLR](host-protection-attributes-and-clr-integration-programming.md)   
 [Недопустимые типы и члены в Microsoft. VisualBasic. dll](disallowed-types-and-members-in-microsoft-visualbasic-dll.md)   
 [Недопустимые типы и элементы в mscorlib. dll](disallowed-types-and-members-in-mscorlib-dll.md)   
 [Недопустимые типы и члены в System. dll](disallowed-types-and-members-in-system-dll.md)   
 [Недопустимые типы и элементы в библиотеке System.Core.dll](disallowed-types-and-members-in-system-core-dll.md)  
  
  
