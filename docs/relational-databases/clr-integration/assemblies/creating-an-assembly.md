---
title: Создание сборки | Документация Майкрософт
description: Используйте CREATE ASSEMBLY, чтобы зарегистрировать сборку в SQL Server и указать ее параметры безопасности. Зарегистрируйте сборку, чтобы использовать ее функциональность.
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
ms.openlocfilehash: 724f0fc6a38388d9366f3c46090ddaf22cd64a34
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85887817"
---
# <a name="creating-an-assembly"></a>Создание сборки
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Управляемые объекты базы данных, например хранимые процедуры или триггеры, компилируются и развертываются в единицах, называемых сборками. Управляемые сборки DLL должны быть зарегистрированы в, [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] прежде чем можно будет использовать функциональные возможности, предоставляемые сборкой. Для регистрации сборки в базе данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] используется инструкция CREATE ASSEMBLY. В этом разделе описывается регистрация сборки с помощью инструкции CREATE ASSEMBLY и способы указания параметров безопасности для сборки.  
  
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
 При создании сборки в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] базе данных можно указать один из трех уровней безопасности, в которых может выполняться код: **безопасный**, **EXTERNAL_ACCESS**или **небезопасный**. При выполнении инструкции **CREATE ASSEMBLY** в сборке кода выполняются определенные проверки, которые могут вызвать сбой регистрации сборки на сервере. Дополнительные сведения см. в примере олицетворения на [сайте CodePlex](https://msftengprodsamples.codeplex.com/).  
  
 **Безопасность** является набором разрешений по умолчанию и работает в большинстве сценариев. Чтобы задать определенный уровень безопасности, измените синтаксис инструкции CREATE ASSEMBLY следующим образом.  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = SAFE;  
```  
  
 Кроме того, можно создать сборку с набором разрешений " **надежный** ", просто опустив третью строку кода выше:  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll';  
```  
  
 Если код в сборке выполняется в наборе разрешений " **Надежные** ", он может выполнять вычисления и доступ к данным только внутри сервера через внутрипроцессный управляемый поставщик.  
  
### <a name="creating-external_access-and-unsafe-assemblies"></a>Создание сборок EXTERNAL_ACCESS и UNSAFE  
 **EXTERNAL_ACCESS** решает сценарии, в которых коду требуется доступ к ресурсам вне сервера, например файлам, сети, реестру и переменным среды. Каждый раз, когда сервер получает доступ к внешним ресурсам, он олицетворяет контекст безопасности пользователя, вызывающего управляемый код.  
  
 Разрешение **НЕбезопасного** кода предназначено для тех случаев, когда сборка не безопасно проверена или требует дополнительного доступа к ограниченным ресурсам, таким как [!INCLUDE[msCoName](../../../includes/msconame-md.md)] API Win32.  
  
 Чтобы создать **EXTERNAL_ACCESS** или **незащищенную** сборку в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , необходимо выполнить одно из следующих двух условий.  
  
1.  Сборка должна иметь строгое имя, подписанное обычной подписью или кодом Authenticode с сертификатом. Это строгое имя (или сертификат) создается внутри [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в виде асимметричного ключа (или сертификата) и имеет соответствующее имя входа с разрешениями **внешнего доступа к сборке** (для сборок внешнего доступа) или разрешение **ненадежной сборки** (для ненадежных сборок).  
  
2.  Владелец базы данных (DBO) имеет **ВНЕШНЮЮ СБОРКУ доступа** (для сборок **внешнего доступа** ) или **ненадежной сборки** (для **ненадежных** сборок), а для базы данных [свойство базы данных TRUSTWORTHY](../../../relational-databases/security/trustworthy-database-property.md) установлено в значение **On**.  

 Два приведенных выше условия также проверяются при загрузке сборки (которая включает выполнение). Чтобы загрузить сборку, должно выполняться хотя бы одно условие.  
  
 Рекомендуется, чтобы [свойство базы данных TRUSTWORTHY](../../../relational-databases/security/trustworthy-database-property.md) в базе данных не было установлено в **On** только для запуска кода среды CLR в серверном процессе. Вместо этого рекомендуется создать асимметричный ключ из файла сборки в главной базе данных. После этого необходимо создать имя входа, сопоставленное с этим асимметричным ключом, а для имени входа должно быть предоставлено разрешение на **сборку внешнего доступа** или **ненадежное сборка** .  
  
 Следующие [!INCLUDE[tsql](../../../includes/tsql-md.md)] инструкции выполняют шаги, необходимые для создания асимметричного ключа, сопоставляют имя входа с этим ключом, а затем предоставляют **EXTERNAL_ACCESS** разрешение на доступ к имени входа. Эти инструкции [!INCLUDE[tsql](../../../includes/tsql-md.md)] необходимо выполнить перед выполнением инструкции CREATE ASSEMBLY.  
  
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
  
 Чтобы создать сборку **внешнего доступа** , создателю необходимо иметь разрешение **внешнего доступа** . Оно задается при создании сборки.  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = EXTERNAL_ACCESS;  
```  
  
 Следующие [!INCLUDE[tsql](../../../includes/tsql-md.md)] инструкции выполняют шаги, необходимые для создания асимметричного ключа, сопоставляют имя входа с этим ключом, а затем предоставляют **ненадежное** разрешение на доступ к имени входа. Эти инструкции [!INCLUDE[tsql](../../../includes/tsql-md.md)] необходимо выполнить перед выполнением инструкции CREATE ASSEMBLY.  
  
```  
USE master;   
GO    
  
CREATE ASYMMETRIC KEY SQLCLRTestKey FROM EXECUTABLE FILE = 'C:\MyDBApp\SQLCLRTest.dll';     
CREATE LOGIN SQLCLRTestLogin FROM ASYMMETRIC KEY SQLCLRTestKey ;    
GRANT UNSAFE ASSEMBLY TO SQLCLRTestLogin ;  
GO  
```  
  
 Чтобы указать, что сборка загружается с **НЕнадежным** разрешением, укажите **ненадежный** набор разрешений при загрузке сборки на сервер:  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = UNSAFE;  
```  
  
 Дополнительные сведения о разрешениях для каждого из параметров см. в разделе [безопасность интеграции со средой CLR](../../../relational-databases/clr-integration/security/clr-integration-security.md).  
  
## <a name="see-also"></a>См. также  
 [Управление сборками интеграции со средой CLR](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md)   
 [Изменение сборки](../../../relational-databases/clr-integration/assemblies/altering-an-assembly.md)   
 [Удаление сборки](../../../relational-databases/clr-integration/assemblies/dropping-an-assembly.md)   
 [Безопасность доступа к коду при интеграции со средой CLR](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [Свойство базы данных TRUSTWORTHY](../../../relational-databases/security/trustworthy-database-property.md)   
 [Частично доверенный вызывающий код](https://msdn.microsoft.com/library/20b0248f-36da-4fc3-97d2-3789fcf6e084)  
  
  
