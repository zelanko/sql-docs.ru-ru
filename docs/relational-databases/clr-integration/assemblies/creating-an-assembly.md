---
title: Создание сборки | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- creating assemblies
- UNSAFE assemblies
- CREATE ASSEMBLY statement
- SAFE assemblies
- EXTERNAL_ACCESS assemblies
- assemblies [CLR integration], creating
ms.assetid: a2bc503d-b6b2-4963-8beb-c11c323f18e0
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 7d1c6c05e196e1a845c073545c3f79f0f83a19b5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47622282"
---
# <a name="creating-an-assembly"></a>Создание сборки
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Управляемые объекты базы данных, например хранимые процедуры или триггеры, компилируются и развертываются в единицах, называемых сборками. Управляемые DLL-сборки должны регистрироваться в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] прежде чем можно будет использовать возможности этой сборки. Для регистрации сборки в базе данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] используется инструкция CREATE ASSEMBLY. В этом разделе описывается регистрация сборки с помощью инструкции CREATE ASSEMBLY и способы указания параметров безопасности для сборки.  
  
## <a name="the-create-assembly-statement"></a>Инструкция CREATE ASSEMBLY  
 Инструкция CREATE ASSEMBLY используется для создания сборки в базе данных. Например:  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll';  
```  
  
 Предложение FROM задает путь к создаваемой сборке. Путь может указываться в формате UNC или быть локальным физическим путем к файлу.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не дает возможность регистрировать различные версии сборок с одинаковыми именами, культурой и открытыми ключами.  
  
 Можно создавать сборки, ссылающиеся на другие сборки. Если сборка создана в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] также создает сборки, на которые ссылается корневая сборка, если эти сборки уже не созданы в базе данных.  
  
 Пользователям базы данных или ролям пользователей предоставляются разрешения на создание в базе данных сборок, владельцами которых они будут. Чтобы создавать сборки, пользователь или роль базы данных должны иметь разрешение CREATE ASSEMBLY.  
  
 Сборка может успешно ссылаться на другие сборки только при следующих условиях.  
  
-   Владельцем сборки, которую вызывает или на которую ссылается пользователь или роль, является этот пользователь или роль.  
  
-   Сборка, которая вызывается или на которую указывает ссылка, была создана в этой базе данных.  
  
## <a name="specifying-security-when-creating-assemblies"></a>Уровни безопасности при создании сборки  
 При создании сборки в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] базы данных, можно указать один из трех различных уровней безопасности, в котором может выполняться код: **БЕЗОПАСНОМ**, **EXTERNAL_ACCESS**, или **UNSAFE** . Когда **CREATE ASSEMBLY** инструкция выполняется, выполняются определенные проверки сборку кода, которая может привести к сборке, не зарегистрирована на сервере. Дополнительные сведения см. в разделе образца Impersonation на [CodePlex](http://msftengprodsamples.codeplex.com/).  
  
 **БЕЗОПАСНЫЙ** набор разрешений по умолчанию и работает для большинства сценариев. Чтобы задать определенный уровень безопасности, измените синтаксис инструкции CREATE ASSEMBLY следующим образом.  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = SAFE;  
```  
  
 Можно также создать сборку с **БЕЗОПАСНОМ** набор разрешений, просто опустив третью строку приведенного выше кода:  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll';  
```  
  
 Когда выполняется код в сборке **БЕЗОПАСНОМ** разрешение задано, он может только выполнять вычисления и доступ к данным в на сервере с помощью внутрипроцессного управляемого поставщика.  
  
### <a name="creating-externalaccess-and-unsafe-assemblies"></a>Создание сборок EXTERNAL_ACCESS и UNSAFE  
 **EXTERNAL_ACCESS** предназначен для сценариев, в которых коду требуется доступ к ресурсам за пределами сервера, такие как файлы, сети, реестра и переменных среды. Каждый раз, когда сервер получает доступ к внешним ресурсам, он олицетворяет контекст безопасности пользователя, вызывающего управляемый код.  
  
 **НЕБЕЗОПАСНЫЙ** разрешение кода является для ситуаций, в которых сборка не проверялась на безопасность или необходим дополнительный доступ к защищенным источникам, например [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Win32 API.  
  
 Чтобы создать **EXTERNAL_ACCESS** или **UNSAFE** сборки в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], должно выполняться одно из следующих двух условий:  
  
1.  Сборка должна иметь строгое имя, подписанное обычной подписью или кодом Authenticode с сертификатом. Это строгое имя (или сертификат) создается внутри [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] как асимметричный ключ (или сертификат), и имеет соответствующее имя входа с **EXTERNAL ACCESS ASSEMBLY** разрешение (для сборок внешнего доступа) или  **UNSAFE ASSEMBLY** разрешение (для небезопасных сборок).  
  
2.  Владелец базы данных (DBO) имеет **EXTERNAL ACCESS ASSEMBLY** (для **ВНЕШНЕГО доступа** сборок) или **UNSAFE ASSEMBLY** (для **UNSAFE** Разрешение сборок) и база данных имеет [свойство базы данных TRUSTWORTHY](../../../relational-databases/security/trustworthy-database-property.md) присвоено **ON**.  
  
 Два приведенных выше условия также проверяются при загрузке сборки (которая включает выполнение). Чтобы загрузить сборку, должно выполняться хотя бы одно условие.  
  
 Мы рекомендуем [свойство базы данных TRUSTWORTHY](../../../relational-databases/security/trustworthy-database-property.md) в базе данных не будет присвоено **ON** только для запуска common language runtime (CLR) кода в серверный процесс. Вместо этого рекомендуется создать асимметричный ключ из файла сборки в главной базе данных. Затем необходимо создать имя входа, сопоставленное с этим асимметричным ключом, и имя входа должно быть предоставлено **EXTERNAL ACCESS ASSEMBLY** или **UNSAFE ASSEMBLY** разрешение.  
  
 Следующие [!INCLUDE[tsql](../../../includes/tsql-md.md)] инструкций выполните действия, необходимые для создания асимметричного ключа, сопоставления имени входа для этого ключа и предоставьте **EXTERNAL_ACCESS** имени входа разрешение. Эти инструкции [!INCLUDE[tsql](../../../includes/tsql-md.md)] необходимо выполнить перед выполнением инструкции CREATE ASSEMBLY.  
  
```  
USE master;   
GO    
  
CREATE ASYMMETRIC KEY SQLCLRTestKey FROM EXECUTABLE FILE = 'C:\MyDBApp\SQLCLRTest.dll'     
CREATE LOGIN SQLCLRTestLogin FROM ASYMMETRIC KEY SQLCLRTestKey     
GRANT EXTERNAL ACCESS ASSEMBLY TO SQLCLRTestLogin;   
GO   
```  
  
> [!NOTE]  
>  Необходимо создать новое имя входа для сопоставления с асимметричным ключом. Это имя входа используется только для предоставления разрешений и не должно сопоставляться с пользователем или использоваться в приложении.  
  
 Чтобы создать **ВНЕШНЕГО доступа** сборки, создатель должен иметь **ВНЕШНЕГО доступа** разрешение. Оно задается при создании сборки.  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = EXTERNAL_ACCESS;  
```  
  
 Следующие [!INCLUDE[tsql](../../../includes/tsql-md.md)] инструкций выполните действия, необходимые для создания асимметричного ключа, сопоставления имени входа для этого ключа и предоставьте **UNSAFE** имени входа разрешение. Эти инструкции [!INCLUDE[tsql](../../../includes/tsql-md.md)] необходимо выполнить перед выполнением инструкции CREATE ASSEMBLY.  
  
```  
USE master;   
GO    
  
CREATE ASYMMETRIC KEY SQLCLRTestKey FROM EXECUTABLE FILE = 'C:\MyDBApp\SQLCLRTest.dll';     
CREATE LOGIN SQLCLRTestLogin FROM ASYMMETRIC KEY SQLCLRTestKey ;    
GRANT UNSAFE ASSEMBLY TO SQLCLRTestLogin ;  
GO  
```  
  
 Чтобы указать, что сборка загружается с **UNSAFE** разрешение, укажите **UNSAFE** набором разрешений, при загрузке сборки на сервере:  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = UNSAFE;  
```  
  
 Дополнительные сведения о разрешениях для каждого параметра см. в разделе [безопасность интеграции CLR](../../../relational-databases/clr-integration/security/clr-integration-security.md).  
  
## <a name="see-also"></a>См. также  
 [Управление сборками интеграции со средой CLR](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md)   
 [Изменение сборки](../../../relational-databases/clr-integration/assemblies/altering-an-assembly.md)   
 [При удалении сборки](../../../relational-databases/clr-integration/assemblies/dropping-an-assembly.md)   
 [CLR Integration Code Access Security](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [Свойство базы данных TRUSTWORTHY](../../../relational-databases/security/trustworthy-database-property.md)   
 [Частично доверенный вызывающий код](http://msdn.microsoft.com/library/20b0248f-36da-4fc3-97d2-3789fcf6e084)  
  
  
