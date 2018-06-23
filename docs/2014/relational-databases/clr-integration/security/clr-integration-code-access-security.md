---
title: Среда CLR Integration Code Access Security | Документы Microsoft
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
- UNSAFE assemblies
- permissions [CLR integration]
- common language runtime [SQL Server], security
- SAFE assemblies
- code access security [CLR integration]
- EXTERNAL_ACCESS assemblies
ms.assetid: 2111cfe0-d5e0-43b1-93c3-e994ac0e9729
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8ccb03b45b27150c00a5620f772afc764dc6ff0c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36098671"
---
# <a name="clr-integration-code-access-security"></a>Управление доступом для кода на основе интеграции со средой CLR
  Среда CLR поддерживает модель безопасности, называемую управлением доступом для кода. В этой модели разрешения предоставляются сборкам на основе идентификатора кода. Дополнительные сведения см. в разделе «Управление доступом для кода» справочной документации пакета средств разработки программного обеспечения .NET Framework.  
  
 Политика безопасности, которая регламентирует разрешения, предоставляемые сборкам, определяется в трех разных местах.  
  
-   Политики компьютера: — это политика действует для всего управляемого кода, выполнение на компьютере, на котором [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] установлен.  
  
-   Политика пользователя: политики, применяемые для управляемого кода в процессе. Для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] служба запущена.  
  
-   Политика размещения: политики, Настройка узлом среды CLR (в этом случае [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]), действует для управляемого кода, выполняемый на узле.  
  
 Механизм управления доступом к коду, поддерживаемый средой CLR, основан на предположении, что в среде времени выполнения может размещаться код, доверенный полностью или частично. Ресурсы, которые защищены с помощью управления доступом для кода среды CLR, обычно окружены управляемые прикладные программные интерфейсы, requirethe соответствующего разрешения доступа к ресурсу. Demandfor разрешения удовлетворяется только в том случае, если все вызывающие элементы (на уровне сборки) в стеке вызовов обладают соответствующими разрешениями ресурсов.  
  
 Набор разрешений CAS, предоставленные для управляемого кода при выполнении в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] предоставляет ряд разрешений сборке, загруженной в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], в конечном итоге набор разрешений, предоставляемых пользовательскому коду может быть ограничен продолжается пользователь и политики уровня компьютера.  
  
## <a name="sql-server-host-policy-level-permission-sets"></a>Наборы разрешений на уровне политики узла SQL Server  
 Набор разрешений CAS, который предоставляется определяемым пользователем сборкам на уровне политики узла [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], определяется набором разрешений, заданным при создании сборки. Существуют три набора разрешений: `SAFE`, `EXTERNAL_ACCESS` и `UNSAFE` (указанный с помощью **PERMISSION_SET** параметр[CREATE ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-assembly-transact-sql)) .  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Эта политика не предназначена для домена приложения по умолчанию, который применяется при создании в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] экземпляра среды CLR.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Fixedpolicy для системных сборок и пользовательской политики для пользовательских сборок.  
  
 Фиксированная политика для сборок CLR и системных сборок [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] предоставляет этим сборкам полное доверие.  
  
 В основе пользовательской части политики сервера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] лежит указание владельцем сборки одного из трех сегментов разрешений для каждой сборки. Дополнительные сведения о правах доступа, перечисленных ниже, см. в документации пакета SDK для платформы .NET Framework.  
  
### <a name="safe"></a>SAFE  
 Разрешаются только внутренние вычисления и локальный доступ к данным. Набор разрешений `SAFE` является наиболее ограниченным. Код, выполняемый сборкой с разрешениями `SAFE`, не может получить доступ к внешним системным ресурсам, таким как файлы, сеть, переменные среды или реестр.  
  
 Сборки `SAFE` обладают следующими разрешениями и значениями свойств.  
  
|Разрешение|Значения и описание|  
|----------------|-----------------------------|  
|`SecurityPermission`|`Execution:` разрешение на выполнение управляемого кода.|  
|`SqlClientPermission`|`Context connection = true`, `context connection = yes`. Можно использовать только контекстное соединение; в строке соединения можно задавать только значение «context connection=true» или «context connection=yes».<br /><br /> **AllowBlankPassword = false:** пустые пароли не допускаются.|  
  
### <a name="externalaccess"></a>EXTERNAL_ACCESS  
 Сборки EXTERNAL_ACCESS имеют те же разрешения, что `SAFE` сборки с дополнительными возможностями для доступа к внешним системным ресурсам, например файлы, сети, переменные среды и реестр.  
  
 Сборки `EXTERNAL_ACCESS` обладают также следующими разрешениями и значениями свойств.  
  
|Разрешение|Значения и описание|  
|----------------|-----------------------------|  
|`DistributedTransactionPermission`|`Unrestricted:` Распределенные транзакции допускаются.|  
|`DNSPermission`|`Unrestricted:` Разрешение для запроса данных от DNS-серверов.|  
|`EnvironmentPermission`|`Unrestricted:` разрешается полный доступ к системным и пользовательским переменным среды.|  
|`EventLogPermission`|`Administer:` разрешаются следующие действия: создание источника события, чтение существующих журналов, удаление источников событий или журналов, формирование ответов на записи, очистка журнала событий, прослушивание событий и доступ к коллекции всех журналов событий.|  
|`FileIOPermission`|`Unrestricted:` разрешен полный доступ к файлам и папкам.|  
|`KeyContainerPermission`|`Unrestricted:` разрешен полный доступ к ключевым контейнерам.|  
|`NetworkInformationPermission`|`Access:` разрешено выполнять команду ping.|  
|`RegistryPermission`|Предоставляет право чтения разделов `HKEY_CLASSES_ROOT`, `HKEY_LOCAL_MACHINE`, `HKEY_CURRENT_USER`, `HKEY_CURRENT_CONFIG` и `HKEY_USERS.`|  
|`SecurityPermission`|`Assertion:` способность подтверждать, что все объекты, вызывающие этот код, имеют нужные разрешения на эту операцию.<br /><br /> `ControlPrincipal:` способность манипулировать основным объектом.<br /><br /> `Execution:` разрешение на выполнение управляемого кода.<br /><br /> `SerializationFormatter:` способность предоставлять услуги сериализации.|  
|**SmtpPermission**|`Access:` разрешены исходящие соединения с портом сервера SMTP 25.|  
|`SocketPermission`|`Connect:` разрешены исходящие соединения для всех портов и протоколов по транспортному адресу.|  
|`SqlClientPermission`|`Unrestricted:` разрешен полный доступ к источнику данных.|  
|`StorePermission`|`Unrestricted:` разрешен полный доступ к хранилищам сертификатов X.509.|  
|`WebPermission`|`Connect:` разрешены исходящие соединения с веб-ресурсами.|  
  
### <a name="unsafe"></a>UNSAFE  
 Набор UNSAFE предоставляет сборкам неограниченный доступ к внутренним и внешним ресурсам [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Код, вызываемый на выполнение из сборки `UNSAFE`, может также вызывать неуправляемый код.  
  
 Сборки `UNSAFE` получают набор разрешений `FullTrust`.  
  
> [!IMPORTANT]  
>  `SAFE` является рекомендованной установкой разрешений для сборок, которые выполняют задачи вычисления и управления данными без доступа к ресурсам вне [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. `EXTERNAL_ACCESS` сборки по умолчанию, выполняются как [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] учетная запись службы, разрешение на выполнение `EXTERNAL_ACCESS` должно предоставляться только именам входа, которым доверено выполняться как учетная запись службы. С точки зрения безопасности сборки `EXTERNAL_ACCESS` и `UNSAFE` являются идентичными. Но сборки `EXTERNAL_ACCESS` предоставляют различные средства защиты, обладающие надежностью и прочностью, которые не предусмотрены в сборках `UNSAFE`. Указание `UNSAFE` позволяет коду в сборке выполнять запрещенные операции в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Дополнительные сведения о создании сборок CLR в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], в разделе [Управление сборками интеграции со средой CLR](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md).  
  
## <a name="accessing-external-resources"></a>Доступ к внешним ресурсам  
 Если сборка с определяемыми пользователем типами (UDT), хранимыми процедурами или конструкциями другого типа зарегистрирована с набором разрешений `SAFE`, то управляемый код, который выполняется в конструкции, не способен получить доступ к внешним ресурсам. Но если задан набор разрешений `EXTERNAL_ACCESS` или `UNSAFE` и в управляемом коде предпринимается попытка получить доступ к внешним ресурсам, то в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] применяются следующие правила.  
  
|Если оператор|То|  
|--------|----------|  
|Контекст выполнения соответствует имени входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|Попытки получить доступ к внешним ресурсам отклоняются, и активизируется исключение безопасности.|  
|Контекст выполнения соответствует имени входа Windows, и контекстом выполнения является первоначальный вызывающий объект.|Доступ к внешнему ресурсу предоставляется в контексте безопасности учетной записи [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|Вызывающий объект не является первоначальным вызывающим объектом.|Доступ запрещается, и активизируется исключение безопасности.|  
|Контекст выполнения соответствует имени входа Windows, контекст выполнения является исходным вызывающим объектом, а к вызывающему объекту применяется олицетворение.|При доступе используется контекст безопасности вызывающего объекта, а не учетная запись службы.|  
  
## <a name="permission-set-summary"></a>Сводные данные о наборе разрешений  
 На следующей диаграмме показаны ограничения и разрешения, предоставленные наборам разрешений `SAFE`, `EXTERNAL_ACCESS` и `UNSAFE`.  
  
|||||  
|-|-|-|-|  
||`SAFE`|`EXTERNAL_ACCESS`|`UNSAFE`|  
|`Code Access Security Permissions`|Только выполнение|Выполнение и доступ к внешним ресурсам|Неограниченное (включая P/Invoke)|  
|`Programming model restrictions`|Да|Да|Без ограничений|  
|`Verifiability requirement`|Да|Да|Нет|  
|`Local data access`|Да|Да|Да|  
|`Ability to call native code`|Нет|Нет|Да|  
  
## <a name="see-also"></a>См. также  
 [Безопасность интеграции со средой CLR](clr-integration-security.md)   
 [Атрибуты защиты узла и программирование средств интеграции со средой CLR](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [Ограничения модели программирования интеграции со средой CLR](../../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)   
 [Среда размещения CLR](../clr-integration-architecture-clr-hosted-environment.md)  
  
  
