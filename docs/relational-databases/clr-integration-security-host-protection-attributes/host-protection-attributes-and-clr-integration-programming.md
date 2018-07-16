---
title: Атрибуты защиты и программирование интеграции со средой CLR | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: clr
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- host protection attributes [CLR integration]
- HostProtectionAttribute [CLR integration]
- common language runtime [SQL Server], host protection attributes
- disallowed types and members [CLR integration]
- common language runtime [SQL Server], disallowed types and members
- HPAs [CLR integration]
ms.assetid: 268078df-63ca-4c03-a8e7-7108bcea9697
caps.latest.revision: 28
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 501c85065f0519987a7837042bec45b5d5b4db9d
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37350316"
---
# <a name="host-protection-attributes-and-clr-integration-programming"></a>Атрибуты защиты узла и программирование средств интеграции со средой CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Среда CLR предоставляет механизм для аннотирования управляемых API, входящих в состав платформы .NET Framework, при помощи определенных атрибутов, которые могут потребоваться серверу CLR (такому как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]), начиная с версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Примеры таких атрибутов защиты сервера включают следующее:  
  
-   **SharedState**, который указывает, предоставляет ли API возможность создания и управления общим состоянием (например, статическими полями классов).  
  
-   **Синхронизация**, который указывает, предоставляет ли API возможность выполнять синхронизацию между потоками.  
  
-   **ExternalProcessMgmt**, который указывает, предоставляет ли API способ управления процессом узла.  
  
 C учетом этих атрибутов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при помощи управления доступом для кода определяет список атрибутов защиты сервера, которые запрещены в размещенной среде. Требования управления доступом для кода применяется один из трех [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] наборов разрешений: **БЕЗОПАСНОМ**, **EXTERNAL_ACCESS**, или **UNSAFE**. Один из этих трех уровней безопасности задается при регистрации сборки на сервере, с помощью **CREATE ASSEMBLY** инструкции. Код, выполняемый в **БЕЗОПАСНОМ** или **EXTERNAL_ACCESS** наборы разрешений необходимо избегать определенных типов или членов, имеющих **System.Security.Permissions.HostProtectionAttribute** применен атрибут. Дополнительные сведения см. в разделе [Creating an Assembly](../../relational-databases/clr-integration/assemblies/creating-an-assembly.md) и [ограничения модели программирования интеграции со средой CLR](../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md).  
  
 **HostProtectionAttribute** не является разрешением безопасности так же, как способ повышения надежности, поскольку он определяет конкретный код создает типы или методы, что ведущее приложение может запрещать. Использование **HostProtectionAttribute** обеспечивает модель программирования, которая позволяет гарантировать стабильность узла.  
  
## <a name="host-protection-attributes"></a>Атрибуты защиты сервера  
 Атрибуты защиты сервера определяют типы или элементы, которые не подходят для серверной модели программирования и представляют следующие возрастающие уровни угрозы надежности:  
  
-   Во всем остальном являются безопасными.  
  
-   Могут привести к дестабилизации управляемого сервером кода пользователя.  
  
-   Могут привести к дестабилизации самого процесса сервера.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не допускает использования типа или члена, имеющего **HostProtectionAttribute** , указывающий **System.Security.Permissions.HostProtectionResource** перечисление со значением ** ExternalProcessMgmt**, **ExternalThreading**, **MayLeakOnAbort**, **SecurityInfrastructure**, ** SelfAffectingProcessMgmnt**, **SelfAffectingThreading**, **SharedState**, **синхронизации**, или **пользовательскогоинтерфейса**. В силу этого сборки утрачивают возможность вызывать элементы, которые включают общее состояние, выполняют синхронизацию, могут вызвать утечку ресурсов при завершении или повлиять на целостность процесса [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="disallowed-types-and-members"></a>Запрещенные типы и элементы  
 В следующих разделах указаны типы и члены которого **HostProtectionResource** значения которых запрещены в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Списки в этих разделах содержат поддерживаемые сборки.  Дополнительные сведения см. в разделе [поддерживаемые библиотеки платформы .NET Framework](../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md).  
  
## <a name="in-this-section"></a>в этом разделе  
 [Недопустимые типы и элементы в Microsoft.VisualBasic.dll](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-microsoft-visualbasic-dll.md)  
 Приведены типы и элементы из файла Microsoft.VisualBasic.dll, для которых запрещены значения атрибутов защиты сервера.  
  
 [Недопустимые типы и элементы в библиотеке mscorlib.dll](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-mscorlib-dll.md)  
 Приведены типы и элементы из файла mscorlib.dll, для которых запрещены значения атрибутов защиты сервера.  
  
 [Недопустимые типы и элементы в System.dll](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-system-dll.md)  
 Приведены типы и элементы из файла System.dll, для которых запрещены значения атрибутов защиты сервера.  
  
 [Недопустимые типы и элементы в библиотеке System.Data.dll](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-system-data-dll.md)  
 Приведены типы и элементы из файла System.Data.dll, для которых запрещены значения атрибутов защиты сервера.  
  
 [Недопустимые типы и элементы в библиотеке System.Core.dll](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-system-core-dll.md)  
 Приведены типы и элементы из файла System.Core.dll, для которых запрещены значения атрибутов защиты сервера.  
  
## <a name="see-also"></a>См. также  
 [CLR Integration Code Access Security](../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [Ограничения модели программирования интеграции со средой CLR](../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)   
 [Создание сборки](../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)  
  
  
