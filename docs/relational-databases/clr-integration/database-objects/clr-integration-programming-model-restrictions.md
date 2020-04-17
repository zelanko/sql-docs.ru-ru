---
title: CLR Интеграция Программирование Модель Ограничения (ru) Документы Майкрософт
description: Сервер S'L Server выполняет проверку кода на управляемых объектах базы данных, когда они впервые зарегистрированы с помощью CREATE ASSEMBLY и во время выполнения.
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
ms.openlocfilehash: 83b73909cf1844796640a83910ee609eadd7dba4
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488557"
---
# <a name="clr-integration-programming-model-restrictions"></a>Ограничения модели программирования на основе интеграции со средой CLR
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  При создании управляемой процедуры хранения или другого управляемого объекта [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] базы данных необходимо учитывать определенные проверки кода, которые необходимо учитывать. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]выполняет проверки управляемой сборки кода, когда он впервые зарегистрирован в базе данных, используя выписку **CREATE ASSEMBLY,** а также во время выполнения. Управляемый код проверяется также во время выполнения, поскольку в сборке могут быть кодовые пути, фактически не достижимые во время выполнения.  Благодаря этому достигается гибкость при регистрации сборок сторонних производителей, поскольку сборка не блокируется из-за наличия в ней «небезопасного» кода, предназначенного для выполнения в клиентской среде, но никогда не выполняющегося во внутрипроцессной среде CLR. Требования, которым должен соответствовать управляемый код, зависят от того, зарегистрирована ли сборка как **SAFE,** **EXTERNAL_ACCESS,** или **UNSAFE,** **SAFE,** самая строгая, и перечислены ниже.  
  
 Кроме ограничений, которые распространяются на сборки управляемого кода, им также предоставляются права доступа к коду. Среда CLR поддерживает модель безопасности, называемую управлением доступом для кода (CAS). В этой модели разрешения предоставляются сборкам на основе идентификатора кода. **SAFE**, **EXTERNAL_ACCESS,** и **UNSAFE** сборки имеют различные разрешения CAS. Для получения дополнительной [CLR Integration Code Access Security](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)информации см.  
  
## <a name="create-assembly-checks"></a>Проверки CREATE ASSEMBLY  
 При запуске оператора **CREATE ASSEMBLY** для каждого уровня безопасности выполняются следующие проверки.  Если какая-либо проверка не удается, **CREATE ASSEMBLY** не справляется с сообщением об ошибке.  
  
### <a name="global-any-security-level"></a>Глобальная проверка (любой уровень безопасности)  
 Все сборки, на которые имеются ссылки, должны удовлетворять одному или нескольким из следующих критериев.  
  
-   Сборка уже зарегистрирована в базе данных.  
  
-   Сборка принадлежит к числу поддерживаемых сборок. Для получения дополнительной информации [см.](../../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md)  
  
-   Вы используете **CREATE ASSEMBLY FROM**_\<location>,_ и все ссылки на сборки и их зависимости доступны в * \<>местоположении. *  
  
-   Вы используете **CREATE ASSEMBLY FROM**_\<байты ...>,_ и все ссылки указаны через пространство разделенных байтов.  
  
### <a name="external_access"></a>EXTERNAL_ACCESS  
 Все **EXTERNAL_ACCESS** собрания должны соответствовать следующим критериям:  
  
-   Статические поля не используются для хранения информации. Допускаются статические поля только для чтения.  
  
-   Тест PEVerify пройден успешно. Средство проверки PEVerify (peverify.exe), проверяющее соответствие кода MSIL и связанных с ним метаданных требованиям безопасности, поставляется в комплекте с пакетом разработчика .NET Framework SDK.  
  
-   Синхронизация, например с классом **СинхронизацииAttribute,** не используется.  
  
-   Методы завершения не используются.  
  
 Следующие пользовательские атрибуты запрещены в **EXTERNAL_ACCESS** сборках:  
  
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
  
-   Проверяются **все EXTERNAL_ACCESS** условия сборки.  
  
## <a name="runtime-checks"></a>Проверки времени выполнения  
 Во время выполнения код сборки проверяется на соответствие ряду условий. Если имеет место хотя бы одно из этих условий, выполнение управляемого кода не разрешается и активизируется исключение.  
  
### <a name="unsafe"></a>UNSAFE  
 Загрузка сборки - либо явно, позвонив в **метод System.Reflection.Assembly.Load()** из массива байт, либо неявно с помощью **Reflection.Emit** namespace-не допускается.  
  
### <a name="external_access"></a>EXTERNAL_ACCESS  
 Проверяются все условия **UNSAFE.**  
  
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
  
 Для получения дополнительной информации о HPA и списке запрещенных типов и [Host Protection Attributes and CLR Integration Programming](../../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)участников поддерживаемых сборок см.  
  
### <a name="safe"></a>SAFE  
 Проверяются **все EXTERNAL_ACCESS** условия.  
  
## <a name="see-also"></a>См. также:  
 [Поддерживаемые рамочные библиотеки .NET](../../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md)   
 [ClR Интеграция Код Безопасности доступа](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [Атрибуты защиты хоста и программирование интеграции CLR](../../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [Создание сборки](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)  
  
  
