---
title: Проектирование сборок | Документация Майкрософт
description: В этой статье описываются факторы, которые следует учитывать при проектировании сборки для размещения на SQL Server, включая упаковку, управление и ограничения на сборки.
ms.custom: ''
ms.date: 04/24/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- designing assemblies [SQL Server]
- assemblies [CLR integration], designing
ms.assetid: 9c07f706-6508-41aa-a4d7-56ce354f9061
author: rothja
ms.author: jroth
ms.openlocfilehash: 4f2a5281d0e5fd7ac18f908ba4c28302b3bfdd5f
ms.sourcegitcommit: bfb5e79586fd08d8e48e9df0e9c76d1f6c2004e9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/29/2020
ms.locfileid: "82262060"
---
# <a name="assemblies---designing"></a>Конструирование сборок
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом подразделе описываются факторы, которые следует принять во внимание при конструировании сборок:  
  
-   компоновка сборок;  
  
-   управление безопасностью сборок;  
  
-   ограничения на сборки.  
  
## <a name="packaging-assemblies"></a>Компоновка сборок  
 Сборка может содержать в своих классах и методах функциональность более чем одной подпрограммы или типа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В большинстве случаев имеет смысл компоновать в одну сборку функциональность подпрограмм, выполняющих связанные функции, особенно если данные подпрограммы относятся к классам, методы которых вызывают друг друга. Например, классы, выполняющие задачи по управлению вводом данных для триггеров и хранимых процедур среды CLR, могут быть скомпонованы в одной сборке. Это связано с тем, что методы данных классов с большей вероятностью будут вызывать друг друга, а не методы менее связных задач.  
  
 При компоновке кода в сборку надо учитывать следующее.  
  
-   Определяемые пользователем типы данных CLR и индексы, зависящие от определяемых пользователем функций среды CLR, могут вызвать появление в базе данных материализованных данных, зависящих от сборки. Часто изменение кода сборки является более сложным, если в базе данных присутствуют материализованные данные, зависящие от сборки. Таким образом, в общем случае лучше отделять код, от которого зависят материализованные данные (такие как определяемые пользователем типы и индексы, использующие определяемые пользователем функции), от кода, от которого не зависят никакие материализованные данные. Дополнительные сведения см. в статьях [Реализация сборок](../../relational-databases/clr-integration/assemblies-implementing.md) и [ALTER ASSEMBLY &#40;&#41;Transact-SQL ](../../t-sql/statements/alter-assembly-transact-sql.md).  
  
-   Если часть управляемого кода требует разрешения более высокого уровня, лучше поместить данный код в отдельную сборку, отдельно от кода, не требующего этого разрешения.  
  
## <a name="managing-assembly-security"></a>Управление безопасностью сборок  
 Можно управлять доступом сборки к ресурсам, защищенным системой безопасности доступа к коду платформы .NET, когда она выполняет управляемый код. Это можно сделать, указав один из трех наборов разрешений при создании или изменении сборки: "Сейф", "EXTERNAL_ACCESS" или "ненадежный".  
  
### <a name="safe"></a>SAFE  
 Набор SAFE является набором разрешений по умолчанию и наиболее ограничен. Код, выполняемый в сборке с набором разрешений SAFE, не может получить доступ к внешним системным ресурсам, таким как файлы, сеть, переменные среды или реестр. Код с набором SAFE может получать доступ к данным из местных баз данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или производить вычисления и обрабатывать бизнес-логику, для которых доступ к ресурсам за пределами местных баз данных не нужен.  
  
 Большинство сборок выполняют вычисления и задачи управления данными, не имея доступа к ресурсам за пределами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Таким образом, набор SAFE рекомендуется в качестве набора разрешений для сборки.  
  
### <a name="external_access"></a>EXTERNAL_ACCESS  
 Набор EXTERNAL_ACCESS позволяет сборкам получать доступ к определенным внешним системным ресурсам, таким как файлы, сети, веб-службы, переменные среды и реестр. Сборки с набором EXTERNAL_ACCESS могут создавать только пользователи [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с разрешениями EXTERNAL ACCESS.  
  
 Сборки с наборами SAFE и EXTERNAL_ACCESS могут содержать только код, который является проверяемым типизированным кодом. Это означает, что данные сборки могут получать доступ к классам только через правильно определенные точки входа, доступные для определения типа. Таким образом, они не могут произвольно обращаться к буферам памяти, не принадлежащим коду. К тому же они не могут выполнять операции, которые могли бы вызвать отрицательные последствия для устойчивости процесса [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="unsafe"></a>UNSAFE  
 Набор UNSAFE предоставляет сборкам неограниченный доступ к ресурсам как внутри, так и за пределами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Код, выполняемый в сборке с набором разрешений UNSAFE, может вызвать неуправляемый код.  
  
 Кроме того, выбор набора UNSAFE позволяет коду в сборке выполнять операции, которые рассматриваются средством проверки среды CLR как нетипичные. Эти операции потенциально могут получать бесконтрольный доступ к буферам памяти в пространстве процесса [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сборки UNSAFE потенциально могут подвергнуть опасности систему безопасности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или среды CLR. Разрешения UNSAFE должны предоставляться только высоконадежным сборкам опытными разработчиками или администраторами. Только члены предопределенной роли сервера **sysadmin** могут создавать ненадежные сборки.  
  
## <a name="restrictions-on-assemblies"></a>Ограничения на сборки  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] налагает определенные ограничения на управляемый код в сборках, делая их выполнение надежным и масштабируемым. Это означает, что некоторые операции, способные нарушить устойчивость сервера, не разрешены в сборках с набором разрешений SAFE и EXTERNAL_ACCESS.  
  
### <a name="disallowed-custom-attributes"></a>Запрещенные пользовательские атрибуты  
 Сборки не могут иметь следующих пользовательских атрибутов.  
  
```  
System.ContextStaticAttribute  
System.MTAThreadAttribute  
System.Runtime.CompilerServices.MethodImplAttribute  
System.Runtime.CompilerServices.CompilationRelaxationsAttribute  
System.Runtime.Remoting.Contexts.ContextAttribute  
System.Runtime.Remoting.Contexts.SynchronizationAttribute  
System.Runtime.InteropServices.DllImportAttribute   
System.Security.Permissions.CodeAccessSecurityAttribute  
System.STAThreadAttribute  
System.ThreadStaticAttribute  
```  
  
 Кроме того, сборки с набором разрешений SAFE и EXTERNAL_ACCESS не могут иметь следующих пользовательских атрибутов.  
  
```  
System.Security.SuppressUnmanagedCodeSecurityAttribute  
System.Security.UnverifiableCodeAttribute  
```  
  
### <a name="disallowed-net-framework-apis"></a>Неразрешенные API-интерфейсы платформы .NET Framework  
 Любой [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] API, помеченный одним из запрещенных **HostProtectionAttributes** , не может быть вызван из сборок из безопасного и EXTERNAL_ACCESS.  
  
```  
eSelfAffectingProcessMgmt  
eSelfAffectingThreading  
eSynchronization  
eSharedState   
eExternalProcessMgmt  
eExternalThreading  
eSecurityInfrastructure  
eMayLeakOnAbort  
eUI  
```  
  
### <a name="supported-net-framework-assemblies"></a>Поддержка сборок платформы .NET Framework  
 Любая сборка, на которую ссылается пользовательская сборка, должна загружаться в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью инструкции CREATE ASSEMBLY. Следующие сборки [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] уже загружены в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], и поэтому на них могут ссылаться пользовательские сборки без использования инструкции CREATE ASSEMBLY.  
  
```  
CustomMarshalers.dll  
Microsoft.VisualBasic.dll  
Microsoft.VisualC.dll  
mscorlib.dll  
System.dll  
System.Configuration.dll  
System.Core.dll  
System.Data.dll  
System.Data.OracleClient.dll  
System.Data.SqlXml.dll  
System.Deployment.dll  
System.Security.dll  
System.Transactions.dll  
System.Web.Services.dll  
system.Xml.dll  
System.Xml.Linq.dll  
```  
  
## <a name="see-also"></a>См. также  
 [Сборки &#40;ядро СУБД&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md)   
 [Безопасность интеграции со средой CLR](../../relational-databases/clr-integration/security/clr-integration-security.md)  
  
  
