---
title: Ограничения модели программирования интеграции со средой CLR | Документы Microsoft
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: clr
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], programming model restrictions
- assemblies [CLR integration], CREATE ASSEMBLY checks
- programming model restrictions [CLR integration]
- assemblies [CLR integration], runtime checks
ms.assetid: 2446afc2-9d21-42d3-9847-7733d3074de9
caps.latest.revision: 22
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 6f8e62bc460062b96a43f09bf1296cf6acd8636f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32924549"
---
# <a name="clr-integration-programming-model-restrictions"></a>Ограничения модели программирования на основе интеграции со средой CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  При построении управляемой хранимой процедуры или другой управляемый объект базы данных, существуют выполняет определенные проверки программного кода [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , следует учитывать. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] проверяет сборку управляемого кода при первой регистрации в базе данных с помощью **CREATE ASSEMBLY** инструкции, а также во время выполнения. Управляемый код проверяется также во время выполнения, поскольку в сборке могут быть кодовые пути, фактически не достижимые во время выполнения.  Благодаря этому достигается гибкость при регистрации сборок сторонних производителей, поскольку сборка не блокируется из-за наличия в ней «небезопасного» кода, предназначенного для выполнения в клиентской среде, но никогда не выполняющегося во внутрипроцессной среде CLR. Требования, которым должен удовлетворять управляемого кода зависят от того, является ли сборка регистрируется как **БЕЗОПАСНОМ**, **EXTERNAL_ACCESS**, или **UNSAFE**, **SAFE** являются самыми строгими и перечислены ниже.  
  
 Кроме ограничений, которые распространяются на сборки управляемого кода, им также предоставляются права доступа к коду. Среда CLR поддерживает модель безопасности, называемую управлением доступом для кода (CAS). В этой модели разрешения предоставляются сборкам на основе идентификатора кода. **БЕЗОПАСНЫЙ**, **EXTERNAL_ACCESS**, и **UNSAFE** сборки имеют различные разрешения CAS. Дополнительные сведения см. в разделе [CLR Integration Code Access Security](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md).  
  
## <a name="create-assembly-checks"></a>Проверки CREATE ASSEMBLY  
 Когда **CREATE ASSEMBLY** выполняется инструкция, для каждого уровня безопасности выполняются следующие проверки.  Если любой проверка завершается ошибкой, **CREATE ASSEMBLY** завершится ошибкой с сообщением об ошибке.  
  
### <a name="global-any-security-level"></a>Глобальная проверка (любой уровень безопасности)  
 Все сборки, на которые имеются ссылки, должны удовлетворять одному или нескольким из следующих критериев.  
  
-   Сборка уже зарегистрирована в базе данных.  
  
-   Сборка принадлежит к числу поддерживаемых сборок. Дополнительные сведения см. в разделе [поддерживаемые библиотеки платформы .NET Framework](../../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md).  
  
-   Вы используете **CREATE ASSEMBLY FROM ***\<расположение >,* и все связанные сборки и их зависимости, доступных в  *\<расположение >*.  
  
-   Вы используете **CREATE ASSEMBLY FROM ***\<байт... >,* и все ссылки заданы с помощью пространства байтов, разделенных.  
  
### <a name="externalaccess"></a>EXTERNAL_ACCESS  
 Все **EXTERNAL_ACCESS** сборки должны удовлетворять следующим условиям:  
  
-   Статические поля не используются для хранения информации. Допускаются статические поля только для чтения.  
  
-   Тест PEVerify пройден успешно. Средство проверки PEVerify (peverify.exe), проверяющее соответствие кода MSIL и связанных с ним метаданных требованиям безопасности, поставляется в комплекте с пакетом разработчика .NET Framework SDK.  
  
-   Синхронизации, например, с **SynchronizationAttribute** класса, не используется.  
  
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
 Загрузка сборки — явным образом с помощью вызова методов **System.Reflection.Assembly.Load()** метод из массива байтов, либо неявно путем использования **Reflection.Emit** пространство имен — не допускается.  
  
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
 [Библиотеки поддерживаемые .NET Framework](../../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md)   
 [Среда CLR Integration Code Access Security](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [Атрибуты защиты узла и программирование средств интеграции со средой CLR](../../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [Создание сборки](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)  
  
  
