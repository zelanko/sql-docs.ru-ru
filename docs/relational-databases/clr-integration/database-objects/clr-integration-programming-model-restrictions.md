---
title: Ограничения модели программирования интеграции со средой CLR | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], programming model restrictions
- assemblies [CLR integration], CREATE ASSEMBLY checks
- programming model restrictions [CLR integration]
- assemblies [CLR integration], runtime checks
ms.assetid: 2446afc2-9d21-42d3-9847-7733d3074de9
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 7c39bb3499302ef1b60744a4332c665506c7fd21
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47809042"
---
# <a name="clr-integration-programming-model-restrictions"></a>Ограничения модели программирования на основе интеграции со средой CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  При построении управляемой хранимой процедуры или другого объекта управляемой базы данных, существуют выполняет определенные проверки кода [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , необходимо учитывать. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] проверяет сборку управляемого кода при ее первой регистрации в базе данных с помощью **CREATE ASSEMBLY** инструкции, а также во время выполнения. Управляемый код проверяется также во время выполнения, поскольку в сборке могут быть кодовые пути, фактически не достижимые во время выполнения.  Благодаря этому достигается гибкость при регистрации сборок сторонних производителей, поскольку сборка не блокируется из-за наличия в ней «небезопасного» кода, предназначенного для выполнения в клиентской среде, но никогда не выполняющегося во внутрипроцессной среде CLR. Требования, которым должны соответствовать управляемый код, зависят от того, ли сборка регистрируется как **БЕЗОПАСНОМ**, **EXTERNAL_ACCESS**, или **UNSAFE**, **SAFE** являются самыми строгими и перечислены ниже.  
  
 Кроме ограничений, которые распространяются на сборки управляемого кода, им также предоставляются права доступа к коду. Среда CLR поддерживает модель безопасности, называемую управлением доступом для кода (CAS). В этой модели разрешения предоставляются сборкам на основе идентификатора кода. **БЕЗОПАСНЫЙ**, **EXTERNAL_ACCESS**, и **UNSAFE** сборки имеют различные разрешения CAS. Дополнительные сведения см. в разделе [CLR Integration Code Access Security](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md).  
  
## <a name="create-assembly-checks"></a>Проверки CREATE ASSEMBLY  
 Когда **CREATE ASSEMBLY** выполняется инструкция, для каждого уровня безопасности выполняются следующие проверки.  Если любой проверка завершается с ошибкой, **CREATE ASSEMBLY** завершится ошибкой с сообщением об ошибке.  
  
### <a name="global-any-security-level"></a>Глобальная проверка (любой уровень безопасности)  
 Все сборки, на которые имеются ссылки, должны удовлетворять одному или нескольким из следующих критериев.  
  
-   Сборка уже зарегистрирована в базе данных.  
  
-   Сборка принадлежит к числу поддерживаемых сборок. Дополнительные сведения см. в разделе [поддерживаемые библиотеки платформы .NET Framework](../../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md).  
  
-   При использовании **CREATE ASSEMBLY FROM ***\<расположение >,* и все связанные сборки и их зависимости были доступны в  *\<расположение >*.  
  
-   При использовании **CREATE ASSEMBLY FROM ***\<байт... >,* и все ссылки заданы с помощью пространства байтов, разделенных.  
  
### <a name="externalaccess"></a>EXTERNAL_ACCESS  
 Все **EXTERNAL_ACCESS** сборки должны удовлетворять следующим условиям:  
  
-   Статические поля не используются для хранения информации. Допускаются статические поля только для чтения.  
  
-   Тест PEVerify пройден успешно. Средство проверки PEVerify (peverify.exe), проверяющее соответствие кода MSIL и связанных с ним метаданных требованиям безопасности, поставляется в комплекте с пакетом разработчика .NET Framework SDK.  
  
-   Синхронизации, например, с помощью **SynchronizationAttribute** класса, не используется.  
  
-   Методы завершения не используются.  
  
 Следующие настраиваемые атрибуты не допускаются в **EXTERNAL_ACCESS** сборки:  
  
-   System.ContextStaticAttribute  
  
-   System.MTAThreadAttribute  
  
-   System.Runtime.CompilerServices.MethodImplAttribute  
  
-   System.Runtime.CompilerServices.CompilationRelaxationsAttribute  
  
-   System.Runtime.Remoting.Contexts.ContextAttribute  
  
-   System.Runtime.Remoting.Contexts.SynchronizationAttribute  
  
-   System.Runtime.InteropServices.DllImportAttribute  
  
-   System.Security.Permissions.CodeAccessSecurityAttribute  
  
-   System.Security.SuppressUnmanagedCodeSecurityAttribute  
  
-   System.Security.UnverifiableCodeAttribute  
  
-   System.STAThreadAttribute  
  
-   System.ThreadStaticAttribute  
  
### <a name="safe"></a>SAFE  
  
-   Все **EXTERNAL_ACCESS** сборки условия проверяются.  
  
## <a name="runtime-checks"></a>Проверки времени выполнения  
 Во время выполнения код сборки проверяется на соответствие ряду условий. Если имеет место хотя бы одно из этих условий, выполнение управляемого кода не разрешается и активизируется исключение.  
  
### <a name="unsafe"></a>UNSAFE  
 Загрузка сборки — явным образом с помощью вызова методов **System.Reflection.Assembly.Load()** метод из массива байтов, или неявно путем использования **Reflection.Emit** пространство имен — не допускается.  
  
### <a name="externalaccess"></a>EXTERNAL_ACCESS  
 Все **UNSAFE** условия проверяются.  
  
 Не допускаются все типы и методы, помеченные следующими значениями атрибутов защиты сервера в поддерживаемом списке сборок.  
  
-   SelfAffectingProcessMgmt  
  
-   SelfAffectingThreading  
  
-   Синхронизация  
  
-   SharedState  
  
-   ExternalProcessMgmt  
  
-   ExternalThreading  
  
-   SecurityInfrastructure  
  
-   MayLeakOnAbort  
  
-   UI  
  
 Дополнительные сведения об атрибутах защиты сервера и список запрещенных типов и членов в поддерживаемых сборок см. в разделе [атрибуты защиты узла и программирование интеграции со средой CLR](../../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md).  
  
### <a name="safe"></a>SAFE  
 Все **EXTERNAL_ACCESS** условия проверяются.  
  
## <a name="see-also"></a>См. также  
 [Поддерживаемые платформы библиотеки платформы .NET](../../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md)   
 [CLR Integration Code Access Security](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [Атрибуты защиты узла и программирование интеграции со средой CLR](../../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [Создание сборки](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)  
  
  
