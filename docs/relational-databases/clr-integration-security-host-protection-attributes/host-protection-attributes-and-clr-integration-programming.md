---
title: Атрибуты защиты узла среды CLR
description: Среда CLR предоставляет механизм для комментирования управляемых программных интерфейсов (API), которые являются частью .NET Framework с определенными атрибутами.
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
ms.openlocfilehash: 733e4adc69570dd98e6e0ad5448820607ade6329
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "75258754"
---
# <a name="host-protection-attributes-and-clr-integration-programming"></a>Атрибуты защиты узла и программирование средств интеграции со средой CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Среда CLR предоставляет механизм для аннотирования управляемых API, входящих в состав платформы .NET Framework, при помощи определенных атрибутов, которые могут потребоваться серверу CLR (такому как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]), начиная с версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Примеры таких атрибутов защиты сервера включают следующее:  
  
-   **Шаредстате**, который указывает, предоставляет ли API возможность создания общего состояния или управления им (например, поля статических классов).  
  
-   **Синхронизация**, которая указывает, предоставляет ли API возможность выполнения синхронизации между потоками.  
  
-   **Екстерналпроцессмгмт**, который указывает, предоставляет ли API способ управления ведущим процессом.  
  
 C учетом этих атрибутов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при помощи управления доступом для кода определяет список атрибутов защиты сервера, которые запрещены в размещенной среде. Требования к CAS задаются одним из трех [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] наборов разрешений: " **надежный**", " **EXTERNAL_ACCESS**" или " **ненадежный**". Один из этих трех уровней безопасности указывается при регистрации сборки на сервере с помощью инструкции **CREATE ASSEMBLY** . Код, исполняемый в наборах разрешений " **безопасный** " или " **EXTERNAL_ACCESS** ", должен избегать определенных типов или членов, к которым применен атрибут **System. Security. Permissions. HostProtectionAttribute** . Дополнительные сведения см. в разделе [Создание сборки](../../relational-databases/clr-integration/assemblies/creating-an-assembly.md) и [ограничения модели программирования интеграции со средой CLR](../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md).  
  
 **HostProtectionAttribute** не является разрешениями безопасности, как и способ повышения надежности, в том смысле, что он определяет конкретные конструкции кода, либо типы, либо методы, которые может запретить узел. Использование **HostProtectionAttribute** обеспечивает модель программирования, которая помогает защитить стабильность узла.  
  
## <a name="host-protection-attributes"></a>Атрибуты защиты сервера  
 Атрибуты защиты сервера определяют типы или элементы, которые не подходят для серверной модели программирования и представляют следующие возрастающие уровни угрозы надежности:  
  
-   Во всем остальном являются безопасными.  
  
-   Могут привести к дестабилизации управляемого сервером кода пользователя.  
  
-   Могут привести к дестабилизации самого процесса сервера.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]запрещает использование типа или члена с **HostProtectionAttribute** , который указывает перечисление **System. Security. Permissions. Хостпротектионресаурце** со значением **екстерналпроцессмгмт**, **екстерналсреадинг**, **майлеаконаборт**, **секуритинфраструктуре**, **SelfAffectingProcessMgmnt**, **SelfAffectingThreading**, **SharedState**, **Synchronization**или **UI**. В силу этого сборки утрачивают возможность вызывать элементы, которые включают общее состояние, выполняют синхронизацию, могут вызвать утечку ресурсов при завершении или повлиять на целостность процесса [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="disallowed-types-and-members"></a>Запрещенные типы и элементы  
 В следующих разделах определяются типы и члены, значения **хостпротектионресаурце** которых запрещены [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Списки в этих разделах содержат поддерживаемые сборки.  Дополнительные сведения см. в разделе [supported .NET Framework librarys](../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md).  
  
## <a name="in-this-section"></a>в этом разделе  
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
 [Безопасность доступа к коду при интеграции со средой CLR](../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [Ограничения модели программирования интеграции со средой CLR](../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)   
 [Создание сборки](../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)  
  
  
