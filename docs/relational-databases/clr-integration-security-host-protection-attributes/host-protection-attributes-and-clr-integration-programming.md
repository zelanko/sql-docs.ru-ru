---
title: Общие язык Runtime (CLR) Атрибуты защиты хоста
description: CLR предоставляет механизм аннотации управляемых AIS в рамочном узлах .NET с такими атрибутами, как SharedState, Синхронизация и ВнешнийProcessMgmt.
ms.custom: seo-lt-2019
ms.date: 03/17/2017
ms.prod: sql
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
ms.openlocfilehash: 2aeaeb5d4eb06d6d632a59300225d01cc4376369
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488063"
---
# <a name="host-protection-attributes-and-clr-integration-programming"></a>Атрибуты защиты узла и программирование средств интеграции со средой CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Среда CLR предоставляет механизм для аннотирования управляемых API, входящих в состав платформы .NET Framework, при помощи определенных атрибутов, которые могут потребоваться серверу CLR (такому как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]), начиная с версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Примеры таких атрибутов защиты сервера включают следующее:  
  
-   **SharedState**, который указывает, предоставляет ли API возможность создания или управления общим состоянием (например, статические поля класса).  
  
-   **Синхронизация,** которая указывает, предоставляет ли API возможность синхронизации между потоками.  
  
-   **ExternalProcessMgmt**, который указывает, предоставляет ли API способ управления процессом узла.  
  
 C учетом этих атрибутов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при помощи управления доступом для кода определяет список атрибутов защиты сервера, которые запрещены в размещенной среде. Требования CAS указаны одним [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из трех наборов разрешений: **SAFE**, **EXTERNAL_ACCESS,** или **UNSAFE.** Один из этих трех уровней безопасности указывается, когда сборка зарегистрирована на сервере, используя заявление **CREATE ASSEMBLY.** Код, исполняемый в наборах разрешений **SAFE** или **EXTERNAL_ACCESS,** должен избегать определенных типов или элементов, которые применяют атрибут **System.Security.Permissions.HostProtectionAttribute.** Для получения дополнительной информации [CLR Integration Programming Model Restrictions](../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md) [см.](../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)  
  
 **HostProtectionAttribute** — это не столько разрешение на безопасность, сколько способ повышения надежности, поскольку оно определяет определенные конструкции кода, типы или методы, которые узел может запретить. Использование **HostProtectionAttribute** обеспечивает использование модели программирования, которая помогает защитить стабильность узла.  
  
## <a name="host-protection-attributes"></a>Атрибуты защиты сервера  
 Атрибуты защиты сервера определяют типы или элементы, которые не подходят для серверной модели программирования и представляют следующие возрастающие уровни угрозы надежности:  
  
-   Во всем остальном являются безопасными.  
  
-   Могут привести к дестабилизации управляемого сервером кода пользователя.  
  
-   Могут привести к дестабилизации самого процесса сервера.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]запрещает использование типа или члена, который имеет **HostProtectionAttribute,** который указывает **System.Security.Permissions.HostProtectionResource** перечисление со значением **ВнешнегоProcessMgmt**, **ExternalThreading**, **MayLeakOnAbort**, **SecurityInfrastructure**, **SelfAffectingProcessMgmnt**, **SelfAffectingThreading**, **SharedState**, **синхронизация**, или **UI**. В силу этого сборки утрачивают возможность вызывать элементы, которые включают общее состояние, выполняют синхронизацию, могут вызвать утечку ресурсов при завершении или повлиять на целостность процесса [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="disallowed-types-and-members"></a>Запрещенные типы и элементы  
 Следующие темы определяют типы и членов, чьи значения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **HostProtectionResource** запрещены .  
  
> [!NOTE]  
>  Списки в этих разделах содержат поддерживаемые сборки.  Для получения дополнительной информации [см.](../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md)  
  
## <a name="in-this-section"></a>В этом разделе  
 [Запрещенные типы и элементы в Microsoft.VisualBasic.dll](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-microsoft-visualbasic-dll.md)  
 Приведены типы и элементы из файла Microsoft.VisualBasic.dll, для которых запрещены значения атрибутов защиты сервера.  
  
 [Недопустимые типы и элементы в библиотеке mscorlib.dll](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-mscorlib-dll.md)  
 Приведены типы и элементы из файла mscorlib.dll, для которых запрещены значения атрибутов защиты сервера.  
  
 [Запрещенные типы и элементы в System.dll](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-system-dll.md)  
 Приведены типы и элементы из файла System.dll, для которых запрещены значения атрибутов защиты сервера.  
  
 [Недопустимые типы и элементы в библиотеке System.Data.dll](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-system-data-dll.md)  
 Приведены типы и элементы из файла System.Data.dll, для которых запрещены значения атрибутов защиты сервера.  
  
 [Недопустимые типы и элементы в библиотеке System.Core.dll](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-system-core-dll.md)  
 Приведены типы и элементы из файла System.Core.dll, для которых запрещены значения атрибутов защиты сервера.  
  
## <a name="see-also"></a>См. также:  
 [ClR Интеграция Код Безопасности доступа](../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [ClR Интеграция Программирование Модель Ограничения](../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)   
 [Создание сборки](../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)  
  
  
