---
title: Ограничения модели программирования интеграции со средой CLR | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], programming model restrictions
- assemblies [CLR integration], CREATE ASSEMBLY checks
- programming model restrictions [CLR integration]
- assemblies [CLR integration], runtime checks
ms.assetid: 2446afc2-9d21-42d3-9847-7733d3074de9
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 039afe6cbe5892d2422eec3c92a4d2bb942d5de0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095491"
---
# <a name="clr-integration-programming-model-restrictions"></a>Ограничения модели программирования на основе интеграции со средой CLR
  При построении управляемой хранимой процедуры или другой управляемый объект базы данных, существуют выполняет определенные проверки программного кода [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] проверяет сборку управляемого кода при первой регистрации в базе данных с помощью `CREATE ASSEMBLY` инструкции, а также во время выполнения. Управляемый код проверяется также во время выполнения, поскольку в сборке могут быть кодовые пути, фактически не достижимые во время выполнения.  Благодаря этому достигается гибкость при регистрации сборок сторонних производителей, поскольку сборка не блокируется из-за наличия в ней «небезопасного» кода, предназначенного для выполнения в клиентской среде, но никогда не выполняющегося во внутрипроцессной среде CLR. Требования, которым должен удовлетворять управляемого кода зависят от того, является ли сборка регистрируется как `SAFE`, `EXTERNAL_ACCESS`, или `UNSAFE`, `SAFE` являются самыми строгими и перечислены ниже.  
  
 Кроме ограничений, которые распространяются на сборки управляемого кода, им также предоставляются права доступа к коду. Среда CLR поддерживает модель безопасности, называемую управлением доступом для кода (CAS). В этой модели разрешения предоставляются сборкам на основе идентификатора кода. Сборки `SAFE`, `EXTERNAL_ACCESS` и `UNSAFE` имеют различные разрешения CAS. Дополнительные сведения см. в разделе [CLR Integration Code Access Security](../security/clr-integration-code-access-security.md).  
  
## <a name="create-assembly-checks"></a>Проверки CREATE ASSEMBLY  
 При запуске инструкции `CREATE ASSEMBLY` для каждого уровня безопасности выполняются следующие проверки.  В случае неудачного завершения любой из проверок выполнение инструкции `CREATE ASSEMBLY` оканчивается неудачей с возвратом сообщения об ошибке.  
  
### <a name="global-any-security-level"></a>Глобальная проверка (любой уровень безопасности)  
 Все сборки, на которые имеются ссылки, должны удовлетворять одному или нескольким из следующих критериев.  
  
-   Сборка уже зарегистрирована в базе данных.  
  
-   Сборка принадлежит к числу поддерживаемых сборок. Дополнительные сведения см. в разделе [поддерживаемые библиотеки платформы .NET Framework](supported-net-framework-libraries.md).  
  
-   Вы используете `CREATE ASSEMBLY FROM`  *\<расположение >,* и все связанные сборки и их зависимости, доступных в  *\<расположение >*.  
  
-   Вы используете `CREATE ASSEMBLY FROM`  *\<байт... >,* и все ссылки заданы с помощью пространства байтов, разделенных.  
  
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
 [Библиотеки поддерживаемые .NET Framework](supported-net-framework-libraries.md)   
 [Среда CLR Integration Code Access Security](../security/clr-integration-code-access-security.md)   
 [Атрибуты защиты узла и программирование средств интеграции со средой CLR](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [Создание сборки](../assemblies/creating-an-assembly.md)  
  
  