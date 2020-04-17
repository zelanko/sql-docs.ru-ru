---
title: Создание Ассамблеи Документы Майкрософт
description: Используйте CREATE ASSEMBLY для регистрации сборки в сервере S'L и указания ее параметров безопасности. Зарегистрируйте сборку, чтобы использовать ее функциональность.
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
ms.openlocfilehash: 6ca6787abae22722a7bbb99d335e63d47051bb46
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81486847"
---
# <a name="creating-an-assembly"></a>Создание сборки
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Управляемые объекты базы данных, например хранимые процедуры или триггеры, компилируются и развертываются в единицах, называемых сборками. Управляемые сборки DLL должны [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] быть зарегистрированы до того, как можно будет использовать функциональность, предоставляемую сборкой. Для регистрации сборки в базе данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] используется инструкция CREATE ASSEMBLY. В этом разделе описывается регистрация сборки с помощью инструкции CREATE ASSEMBLY и способы указания параметров безопасности для сборки.  
  
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
 При создании сборки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в базу данных можно указать один из трех различных уровней безопасности, на которых может работать код: **SAFE,** **EXTERNAL_ACCESS**или **UNSAFE.** При запуске оператора **CREATE ASSEMBLY** на сборке кода выполняются определенные проверки, которые могут привести к тому, что сборка не зарегистрируется на сервере. Для получения дополнительной информации смотрите образец олицетворения на [CodePlex](https://msftengprodsamples.codeplex.com/).  
  
 **SAFE** — это набор разрешений по умолчанию, который работает для большинства сценариев. Чтобы задать определенный уровень безопасности, измените синтаксис инструкции CREATE ASSEMBLY следующим образом.  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = SAFE;  
```  
  
 Также можно создать сборку с разрешением **SAFE,** установленным, просто опустив третью строку кода выше:  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll';  
```  
  
 Когда код в сборке работает под набором разрешений **SAFE,** он может выполнять вычисления и доступ к данным на сервере только через поставщика управляемых данных в процессе процесса.  
  
### <a name="creating-external_access-and-unsafe-assemblies"></a>Создание сборок EXTERNAL_ACCESS и UNSAFE  
 **EXTERNAL_ACCESS** рассматриваются сценарии, в которых код удостаивается доступом к ресурсам за пределами сервера, таким как файлы, сетевые, реестровые и переменные среды. Каждый раз, когда сервер получает доступ к внешним ресурсам, он олицетворяет контекст безопасности пользователя, вызывающего управляемый код.  
  
 Разрешение кода **UNSAFE** предназначено для тех ситуаций, когда сборка не является проверяемым безопасным или требует дополнительного доступа к ограниченным ресурсам, таким как [!INCLUDE[msCoName](../../../includes/msconame-md.md)] API Win32.  
  
 Для создания **EXTERNAL_ACCESS** или **UNSAFE** сборки в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], одно из следующих двух условий должны быть выполнены:  
  
1.  Сборка должна иметь строгое имя, подписанное обычной подписью или кодом Authenticode с сертификатом. Это сильное имя (или [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] сертификат) создается внутри как асимметричный ключ (или сертификат) и имеет соответствующий логин с разрешением **EXTERNAL ACCESS ASSEMBLY** (для сборок внешнего доступа) или разрешение **UNSAFE ASSEMBLY** (для небезопасных сборок).  
  
2.  Владелец базы данных (DBO) имеет **external ACCESS ASSEMBLY** (для агрегатов EXTERNAL **ACCESS)** или **UNSAFE ASSEMBLY** (для сборок **UNSAFE)** с разрешением, а база данных имеет [TRUSTWORTHY Database Property,](../../../relational-databases/security/trustworthy-database-property.md) установленный на **ON**.  

 Два приведенных выше условия также проверяются при загрузке сборки (которая включает выполнение). Чтобы загрузить сборку, должно выполняться хотя бы одно условие.  
  
 Мы рекомендуем, чтобы [TRUSTWORTHY Database Property](../../../relational-databases/security/trustworthy-database-property.md) в базе данных не устанавливалось **на ON** только для запуска кода общего времени выполнения языка (CLR) в процессе сервера. Вместо этого рекомендуется создать асимметричный ключ из файла сборки в главной базе данных. Затем необходимо создать логин, отображаемый с этим асимметричным ключом, и логин должен быть предоставлен **EXTERNAL ACCESS ASSEMBLY** или **unSAFE ASSEMBLY.**  
  
 Следующие [!INCLUDE[tsql](../../../includes/tsql-md.md)] операторы выполняют шаги, необходимые для создания асимметричного ключа, наносят на карту логин для этого ключа, а затем предоставляют **EXTERNAL_ACCESS** разрешение на вход. Эти инструкции [!INCLUDE[tsql](../../../includes/tsql-md.md)] необходимо выполнить перед выполнением инструкции CREATE ASSEMBLY.  
  
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
  
 Для создания сборки **EXTERNAL ACCESS** создателю необходимо разрешение **EXTERNAL ACCESS.** Оно задается при создании сборки.  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = EXTERNAL_ACCESS;  
```  
  
 Следующие [!INCLUDE[tsql](../../../includes/tsql-md.md)] операторы выполняют шаги, необходимые для создания асимметричного ключа, наносят на карту логин для этого ключа, а затем предоставляют разрешение **UNSAFE** на вход. Эти инструкции [!INCLUDE[tsql](../../../includes/tsql-md.md)] необходимо выполнить перед выполнением инструкции CREATE ASSEMBLY.  
  
```  
USE master;   
GO    
  
CREATE ASYMMETRIC KEY SQLCLRTestKey FROM EXECUTABLE FILE = 'C:\MyDBApp\SQLCLRTest.dll';     
CREATE LOGIN SQLCLRTestLogin FROM ASYMMETRIC KEY SQLCLRTestKey ;    
GRANT UNSAFE ASSEMBLY TO SQLCLRTestLogin ;  
GO  
```  
  
 Чтобы указать, что сборка загружается с разрешения **UNSAFE,** вы указываете набор разрешений **UNSAFE** при загрузке сборки на сервер:  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = UNSAFE;  
```  
  
 Для получения более подробной информации о разрешениях для каждой из настроек, [см.](../../../relational-databases/clr-integration/security/clr-integration-security.md)  
  
## <a name="see-also"></a>См. также:  
 [Управление интеграционными ассамблеями CLR](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md)   
 [Изменение Ассамблеи](../../../relational-databases/clr-integration/assemblies/altering-an-assembly.md)   
 [Удаление Ассамблеи](../../../relational-databases/clr-integration/assemblies/dropping-an-assembly.md)   
 [ClR Интеграция Код Безопасности доступа](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [TRUSTWORTHY База данных собственности](../../../relational-databases/security/trustworthy-database-property.md)   
 [Частично доверенный вызывающий код](https://msdn.microsoft.com/library/20b0248f-36da-4fc3-97d2-3789fcf6e084)  
  
  
