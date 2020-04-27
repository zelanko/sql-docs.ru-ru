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
ms.openlocfilehash: a9b51e0fc192c94b32b4d496523dbf3c9216efd6
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62873818"
---
# <a name="clr-integration-programming-model-restrictions"></a>Ограничения модели программирования на основе интеграции со средой CLR
  При построении управляемой хранимой процедуры или другого управляемого объекта базы данных выполняются определенные проверки кода, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] выполняющие проверки сборки управляемого кода при ее первой регистрации в базе данных с помощью `CREATE ASSEMBLY` инструкции, а также во время выполнения. Управляемый код проверяется также во время выполнения, поскольку в сборке могут быть кодовые пути, фактически не достижимые во время выполнения.  Благодаря этому достигается гибкость при регистрации сборок сторонних производителей, поскольку сборка не блокируется из-за наличия в ней «небезопасного» кода, предназначенного для выполнения в клиентской среде, но никогда не выполняющегося во внутрипроцессной среде CLR. Требования, которым должен удовлетворять управляемый код, зависят от того, зарегистрирована `EXTERNAL_ACCESS`ли сборка `UNSAFE`как `SAFE` ,, или, которая является максимально `SAFE`допустимой и приведена ниже.  
  
 Кроме ограничений, которые распространяются на сборки управляемого кода, им также предоставляются права доступа к коду. Среда CLR поддерживает модель безопасности, называемую управлением доступом для кода (CAS). В этой модели разрешения предоставляются сборкам на основе идентификатора кода. Сборки `SAFE`, `EXTERNAL_ACCESS` и `UNSAFE` имеют различные разрешения CAS. Дополнительные сведения см. в статье [Безопасность доступа к коду для интеграции со средой CLR](../security/clr-integration-code-access-security.md).  
  
## <a name="create-assembly-checks"></a>Проверки CREATE ASSEMBLY  
 При запуске инструкции `CREATE ASSEMBLY` для каждого уровня безопасности выполняются следующие проверки.  В случае неудачного завершения любой из проверок выполнение инструкции `CREATE ASSEMBLY` оканчивается неудачей с возвратом сообщения об ошибке.  
  
### <a name="global-any-security-level"></a>Глобальная проверка (любой уровень безопасности)  
 Все сборки, на которые имеются ссылки, должны удовлетворять одному или нескольким из следующих критериев.  
  
-   Сборка уже зарегистрирована в базе данных.  
  
-   Сборка принадлежит к числу поддерживаемых сборок. Дополнительные сведения см. в разделе [supported .NET Framework librarys](supported-net-framework-libraries.md).  
  
-   Вы используете `CREATE ASSEMBLY FROM` * \<расположение>,* а все сборки, на которые имеются ссылки, и их зависимости доступны в * \<расположении>*.  
  
-   Вы используете `CREATE ASSEMBLY FROM` * \<байты... >,* а все ссылки указаны с помощью разделенных пробелами байтов.  
  
### <a name="external_access"></a>EXTERNAL_ACCESS  
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
 Не допускается загрузка сборки явным образом путем вызова `System.Reflection.Assembly.Load()` метода из массива байтов или неявного использования `Reflection.Emit` пространства имен.  
  
### <a name="external_access"></a>EXTERNAL_ACCESS  
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
  
 Дополнительные сведения о hPa и списке запрещенных типов и членов в поддерживаемых сборках см. в разделе [атрибуты защиты узла и программирование интеграции со средой CLR](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md).  
  
### <a name="safe"></a>SAFE  
 Проверяются все условия `EXTERNAL_ACCESS`.  
  
## <a name="see-also"></a>См. также  
 [Поддерживаемые библиотеки .NET Framework](supported-net-framework-libraries.md)   
 [Безопасность доступа к коду при интеграции со средой CLR](../security/clr-integration-code-access-security.md)   
 [Атрибуты защиты узла и программирование интеграции со средой CLR](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [Создание сборки](../assemblies/creating-an-assembly.md)  
  
  
