---
title: Атрибуты защиты и программирование интеграции со средой CLR | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- host protection attributes [CLR integration]
- HostProtectionAttribute [CLR integration]
- common language runtime [SQL Server], host protection attributes
- disallowed types and members [CLR integration]
- common language runtime [SQL Server], disallowed types and members
- HPAs [CLR integration]
ms.assetid: 268078df-63ca-4c03-a8e7-7108bcea9697
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 68f1f114002ab0ef38c7565a523723a06958048d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48205594"
---
# <a name="host-protection-attributes-and-clr-integration-programming"></a>Атрибуты защиты узла и программирование средств интеграции со средой CLR
  Среда CLR предоставляет механизм для аннотирования управляемых API, входящих в состав платформы .NET Framework, при помощи определенных атрибутов, которые могут потребоваться серверу CLR (такому как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]), начиная с версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Примеры таких атрибутов защиты сервера включают следующее:  
  
-   `SharedState`, который указывает, предоставляет ли API доступ к средствам создания или управления общим состоянием (например, к полям статического класса).  
  
-   `Synchronization`, который указывает, предоставляет ли API возможность выполнять синхронизацию потоков.  
  
-   `ExternalProcessMgmt`, который указывает, предоставляет ли API способ управления процессом узла.  
  
 C учетом этих атрибутов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при помощи управления доступом для кода определяет список атрибутов защиты сервера, которые запрещены в размещенной среде. Требования управления доступом для кода применяется один из трех [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] наборов разрешений: `SAFE`, `EXTERNAL_ACCESS`, или `UNSAFE`. Один из этих трех уровней безопасности задается с помощью инструкции `CREATE ASSEMBLY` при регистрации сборки на сервере. В коде, выполняющемся с наборами разрешений `SAFE` или `EXTERNAL_ACCESS`, необходимо избегать использования элементов определенных типов, к которым применен атрибут `System.Security.Permissions.HostProtectionAttribute`. Дополнительные сведения см. в разделе [Creating an Assembly](../clr-integration/assemblies/creating-an-assembly.md) и [ограничения модели программирования интеграции со средой CLR](../clr-integration/database-objects/clr-integration-programming-model-restrictions.md).  
  
 Атрибут `HostProtectionAttribute` представляет собой скорее не право доступа, а способ повышения надежности, поскольку он определяет конкретные конструкции в коде (типы или методы), которые могут быть запрещены сервером. В результате применения атрибута `HostProtectionAttribute` в действие вводится модель программирования, которая позволяет защитить стабильность сервера.  
  
## <a name="host-protection-attributes"></a>Атрибуты защиты сервера  
 Атрибуты защиты сервера определяют типы или элементы, которые не подходят для серверной модели программирования и представляют следующие возрастающие уровни угрозы надежности:  
  
-   Во всем остальном являются безопасными.  
  
-   Могут привести к дестабилизации управляемого сервером кода пользователя.  
  
-   Могут привести к дестабилизации самого процесса сервера.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не допускает использования типа или члена, имеющего `HostProtectionAttribute` , указывающий `System.Security.Permissions.HostProtectionResource` перечисление со значением `ExternalProcessMgmt`, `ExternalThreading`, `MayLeakOnAbort`, `SecurityInfrastructure`, `SelfAffectingProcessMgmnt`, `SelfAffectingThreading`, `SharedState`, `Synchronization`, или `UI`. В силу этого сборки утрачивают возможность вызывать элементы, которые включают общее состояние, выполняют синхронизацию, могут вызвать утечку ресурсов при завершении или повлиять на целостность процесса [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="disallowed-types-and-members"></a>Запрещенные типы и элементы  
 В следующих разделах приведены типы и элементы, значения `HostProtectionResource` которых запрещены в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Списки в этих разделах содержат поддерживаемые сборки.  Дополнительные сведения см. в разделе [поддерживаемые библиотеки платформы .NET Framework](../clr-integration/database-objects/supported-net-framework-libraries.md).  
  
## <a name="in-this-section"></a>в этом разделе  
 [Недопустимые типы и элементы в Microsoft.VisualBasic.dll](disallowed-types-and-members-in-microsoft-visualbasic-dll.md)  
 Приведены типы и элементы из файла Microsoft.VisualBasic.dll, для которых запрещены значения атрибутов защиты сервера.  
  
 [Недопустимые типы и элементы в библиотеке mscorlib.dll](disallowed-types-and-members-in-mscorlib-dll.md)  
 Приведены типы и элементы из файла mscorlib.dll, для которых запрещены значения атрибутов защиты сервера.  
  
 [Недопустимые типы и элементы в System.dll](disallowed-types-and-members-in-system-dll.md)  
 Приведены типы и элементы из файла System.dll, для которых запрещены значения атрибутов защиты сервера.  
  
 [Недопустимые типы и элементы в библиотеке System.Data.dll](disallowed-types-and-members-in-system-data-dll.md)  
 Приведены типы и элементы из файла System.Data.dll, для которых запрещены значения атрибутов защиты сервера.  
  
 [Недопустимые типы и элементы в библиотеке System.Core.dll](disallowed-types-and-members-in-system-core-dll.md)  
 Приведены типы и элементы из файла System.Core.dll, для которых запрещены значения атрибутов защиты сервера.  
  
## <a name="see-also"></a>См. также  
 [CLR Integration Code Access Security](../clr-integration/security/clr-integration-code-access-security.md)   
 [Ограничения модели программирования интеграции со средой CLR](../clr-integration/database-objects/clr-integration-programming-model-restrictions.md)   
 [Создание сборки](../clr-integration/assemblies/creating-an-assembly.md)  
  
  
