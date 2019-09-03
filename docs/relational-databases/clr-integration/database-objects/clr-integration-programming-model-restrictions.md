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
ms.openlocfilehash: c019b50f896109a699869d748d8eef20b57d6edb
ms.sourcegitcommit: 734529a6f108e6ee6bfce939d8be562d405e1832
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2019
ms.locfileid: "70212364"
---
# <a name="clr-integration-programming-model-restrictions"></a>Ограничения модели программирования на основе интеграции со средой CLR
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  При построении управляемой хранимой процедуры или другого управляемого объекта базы данных выполняются определенные проверки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] кода, которые необходимо учитывать. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]выполняет проверки сборки управляемого кода при ее первой регистрации в базе данных, с помощью инструкции **CREATE ASSEMBLY** , а также во время выполнения. Управляемый код проверяется также во время выполнения, поскольку в сборке могут быть кодовые пути, фактически не достижимые во время выполнения.  Благодаря этому достигается гибкость при регистрации сборок сторонних производителей, поскольку сборка не блокируется из-за наличия в ней «небезопасного» кода, предназначенного для выполнения в клиентской среде, но никогда не выполняющегося во внутрипроцессной среде CLR. Требования, которым должен удовлетворять управляемый код, зависят от того, зарегистрирована ли сборка как **Безопасность**, **EXTERNAL_ACCESS**или незащищенная, а какие — нет, и они перечислены ниже.  
  
 Кроме ограничений, которые распространяются на сборки управляемого кода, им также предоставляются права доступа к коду. Среда CLR поддерживает модель безопасности, называемую управлением доступом для кода (CAS). В этой модели разрешения предоставляются сборкам на основе идентификатора кода. Сборки " **Безопасность**", " **EXTERNAL_ACCESS**" и "ненадежные" имеют разные разрешения CAS. Дополнительные сведения см. в статье [Безопасность доступа к коду для интеграции со средой CLR](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md).  
  
## <a name="create-assembly-checks"></a>Проверки CREATE ASSEMBLY  
 При выполнении инструкции **CREATE ASSEMBLY** для каждого уровня безопасности выполняются следующие проверки.  Если какая – либо проверка завершается неудачей, **CREATE ASSEMBLY** завершится с сообщением об ошибке.  
  
### <a name="global-any-security-level"></a>Глобальная проверка (любой уровень безопасности)  
 Все сборки, на которые имеются ссылки, должны удовлетворять одному или нескольким из следующих критериев.  
  
-   Сборка уже зарегистрирована в базе данных.  
  
-   Сборка принадлежит к числу поддерживаемых сборок. Дополнительные сведения см. в разделе [supported .NET Framework librarys](../../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md).  
  
-   Вы используете **Создание сборки из** _\<расположения >,_ а все сборки, на которые имеются ссылки, и их зависимости доступны в  *\<> расположения*.  
  
-   Вы используете **Создание сборки из** _\<байт... >,_ а все ссылки указываются с помощью разделенных пробелами байтов.  
  
### <a name="external_access"></a>EXTERNAL_ACCESS  
 Все сборки **EXTERNAL_ACCESS** должны соответствовать следующим критериям:  
  
-   Статические поля не используются для хранения информации. Допускаются статические поля только для чтения.  
  
-   Тест PEVerify пройден успешно. Средство проверки PEVerify (peverify.exe), проверяющее соответствие кода MSIL и связанных с ним метаданных требованиям безопасности, поставляется в комплекте с пакетом разработчика .NET Framework SDK.  
  
-   Синхронизация, например с классом **SynchronizationAttribute** , не используется.  
  
-   Методы завершения не используются.  
  
 Следующие пользовательские атрибуты запрещены в сборках **EXTERNAL_ACCESS** :  
  
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
  
-   Проверяются все условия сборки **EXTERNAL_ACCESS** .  
  
## <a name="runtime-checks"></a>Проверки времени выполнения  
 Во время выполнения код сборки проверяется на соответствие ряду условий. Если имеет место хотя бы одно из этих условий, выполнение управляемого кода не разрешается и активизируется исключение.  
  
### <a name="unsafe"></a>UNSAFE  
 Явная загрузка сборки путем вызова метода **System. Reflection. Assembly. Load ()** из массива байтов или неявного использования **отражения. Emit** пространства имен — не разрешено.  
  
### <a name="external_access"></a>EXTERNAL_ACCESS  
 Проверяются все **ненадежные** условия.  
  
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
  
 Дополнительные сведения о hPa и списке запрещенных типов и членов в поддерживаемых сборках см. в разделе [атрибуты защиты узла и программирование интеграции со средой CLR](../../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md).  
  
### <a name="safe"></a>SAFE  
 Проверяются все условия **EXTERNAL_ACCESS** .  
  
## <a name="see-also"></a>См. также  
 [Поддерживаемые библиотеки .NET Framework](../../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md)   
 [Безопасность доступа к коду при интеграции со средой CLR](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [Атрибуты защиты узла и программирование интеграции со средой CLR](../../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [Создание сборки](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)  
  
  
