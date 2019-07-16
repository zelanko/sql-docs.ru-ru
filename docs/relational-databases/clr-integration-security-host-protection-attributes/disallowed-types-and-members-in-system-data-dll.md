---
title: Запрещенные типы и элементы в библиотеке System.Data.dll | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- host protection attributes [CLR integration]
- common language runtime [SQL Server], host protection attributes
ms.assetid: ee5f55e9-fbef-401a-be18-a2e5873c8720
author: rothja
ms.author: jroth
ms.openlocfilehash: 50f7f8aacfc61b55e969ea0d57f82d58e50e093b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68028118"
---
# <a name="disallowed-types-and-members-in-systemdatadll"></a>Недопустимые типы и элементы в библиотеке System.Data.dll
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] общего программирования интеграции (со средой CLR) языка не допускает использования типа или члена, имеющего **HostProtectionAttribute** , указывающий **System.Security.Permissions.HostProtectionResource** Перечисление со значением **ExternalProcessMgmt**, **ExternalThreading**, **MayLeakOnAbort**, **SecurityInfrastructure**, **SelfAffectingProcessMgmnt**, **SelfAffectingThreading**, **SharedState**, **синхронизации**, или **Пользовательского интерфейса**. В следующей таблице приводится перечень членов и типов сборки System.Data.dll, чьи значения атрибутов защиты узла недопустимы.  
  
> [!NOTE]  
>  Этот список был создан из поддерживаемых сборок. Дополнительные сведения см. в разделе [поддерживаемые библиотеки платформы .NET Framework](../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md).  
  
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
 [Атрибуты защиты узла и программирование интеграции со средой CLR](../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [Запрещенные типы и элементы в Microsoft.VisualBasic.dll](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-microsoft-visualbasic-dll.md)   
 [Запрещенные типы и элементы в библиотеке mscorlib.dll](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-mscorlib-dll.md)   
 [Запрещенные типы и элементы в System.dll](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-system-dll.md)   
 [Недопустимые типы и элементы в библиотеке System.Core.dll](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-system-core-dll.md)  
  
  
