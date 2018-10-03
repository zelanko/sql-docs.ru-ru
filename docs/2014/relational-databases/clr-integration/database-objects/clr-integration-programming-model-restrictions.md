---
title: Ограничения модели программирования интеграции со средой CLR | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
ms.openlocfilehash: a7b7dfcbd9d7cc7407ed33cc0ea00e93df839b93
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48187944"
---
# <a name="clr-integration-programming-model-restrictions"></a>Ограничения модели программирования на основе интеграции со средой CLR
  При построении управляемой хранимой процедуры или другого объекта управляемой базы данных, существуют выполняет определенные проверки кода [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] проверяет сборку управляемого кода при ее первой регистрации в базе данных с помощью `CREATE ASSEMBLY` инструкции, а также во время выполнения. Управляемый код проверяется также во время выполнения, поскольку в сборке могут быть кодовые пути, фактически не достижимые во время выполнения.  Благодаря этому достигается гибкость при регистрации сборок сторонних производителей, поскольку сборка не блокируется из-за наличия в ней «небезопасного» кода, предназначенного для выполнения в клиентской среде, но никогда не выполняющегося во внутрипроцессной среде CLR. Требования, которым должны соответствовать управляемый код, зависят от того, ли сборка регистрируется как `SAFE`, `EXTERNAL_ACCESS`, или `UNSAFE`, `SAFE` являются самыми строгими и перечислены ниже.  
  
 Кроме ограничений, которые распространяются на сборки управляемого кода, им также предоставляются права доступа к коду. Среда CLR поддерживает модель безопасности, называемую управлением доступом для кода (CAS). В этой модели разрешения предоставляются сборкам на основе идентификатора кода. Сборки `SAFE`, `EXTERNAL_ACCESS` и `UNSAFE` имеют различные разрешения CAS. Дополнительные сведения см. в разделе [CLR Integration Code Access Security](../security/clr-integration-code-access-security.md).  
  
## <a name="create-assembly-checks"></a>Проверки CREATE ASSEMBLY  
 При запуске инструкции `CREATE ASSEMBLY` для каждого уровня безопасности выполняются следующие проверки.  В случае неудачного завершения любой из проверок выполнение инструкции `CREATE ASSEMBLY` оканчивается неудачей с возвратом сообщения об ошибке.  
  
### <a name="global-any-security-level"></a>Глобальная проверка (любой уровень безопасности)  
 Все сборки, на которые имеются ссылки, должны удовлетворять одному или нескольким из следующих критериев.  
  
-   Сборка уже зарегистрирована в базе данных.  
  
-   Сборка принадлежит к числу поддерживаемых сборок. Дополнительные сведения см. в разделе [поддерживаемые библиотеки платформы .NET Framework](supported-net-framework-libraries.md).  
  
-   При использовании `CREATE ASSEMBLY FROM`  *\<расположение >,* и все связанные сборки и их зависимости были доступны в  *\<расположение >*.  
  
-   При использовании `CREATE ASSEMBLY FROM`  *\<байт... >,* и все ссылки заданы с помощью пространства байтов, разделенных.  
  
### <a name="externalaccess"></a>EXTERNAL_ACCESS  
 Все сборки `EXTERNAL_ACCESS` должны отвечать следующим требованиям.  
  
-   Статические поля не используются для хранения информации. Допускаются статические поля только для чтения.  
  
-   Тест PEVerify пройден успешно. Средство проверки PEVerify (peverify.exe), проверяющее соответствие кода MSIL и связанных с ним метаданных требованиям безопасности, поставляется в комплекте с пакетом разработчика .NET Framework SDK.  
  
-   Синхронизация (например, с помощью класса `SynchronizationAttribute`) не используется.  
  
-   Методы завершения не используются.  
  
 В сборках `EXTERNAL_ACCESS` запрещено использовать следующие настраиваемые атрибуты.  
  
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
  
-   Проверяются все условия, относящиеся к сборкам `EXTERNAL_ACCESS`.  
  
## <a name="runtime-checks"></a>Проверки времени выполнения  
 Во время выполнения код сборки проверяется на соответствие ряду условий. Если имеет место хотя бы одно из этих условий, выполнение управляемого кода не разрешается и активизируется исключение.  
  
### <a name="unsafe"></a>UNSAFE  
 Не допускается загрузка сборки явным образом из массива байтов с помощью метода `System.Reflection.Assembly.Load()` или неявно с использованием пространства имен `Reflection.Emit`.  
  
### <a name="externalaccess"></a>EXTERNAL_ACCESS  
 Проверяются все условия `UNSAFE`.  
  
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
  
 Дополнительные сведения об атрибутах защиты сервера и список запрещенных типов и членов в поддерживаемых сборок см. в разделе [атрибуты защиты узла и программирование интеграции со средой CLR](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md).  
  
### <a name="safe"></a>SAFE  
 Проверяются все условия `EXTERNAL_ACCESS`.  
  
## <a name="see-also"></a>См. также  
 [Поддерживаемые платформы библиотеки платформы .NET](supported-net-framework-libraries.md)   
 [CLR Integration Code Access Security](../security/clr-integration-code-access-security.md)   
 [Атрибуты защиты узла и программирование интеграции со средой CLR](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [Создание сборки](../assemblies/creating-an-assembly.md)  
  
  
