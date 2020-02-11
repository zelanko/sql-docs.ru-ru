---
title: Поддерживаемые библиотеки .NET Framework | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], .NET Framework libraries
- .NET Framework [CLR Integration]
ms.assetid: 417544ff-c25c-496e-add4-2f278f8a4911
author: rothja
ms.author: jroth
ms.openlocfilehash: faace3cf7e03afe18d2298580c45470f0b32b580
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68140881"
---
# <a name="supported-net-framework-libraries"></a>Поддерживаемые библиотеки платформы .NET Framework
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Если среда CLR размещается в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], то появляется возможность разрабатывать на управляемом коде хранимые процедуры, триггеры, определяемые пользователем функции, определяемые пользователем типы и определяемые пользователем статистические функции. Функциональность, реализованная в библиотеках классов платформы .NET Framework, предоставляет доступ к предварительно построенным классам для операций со строками, сложных математических операций, доступа к файлам, шифрования и т. д. Доступ к этим классам легко получить из любой управляемой хранимой процедуры, определяемого пользователем типа, триггера, определяемой пользователем функции или определяемой пользователем статистической функции.  
  
> [!NOTE]  
>  При обслуживании или обновлении неподдерживаемых сборок в глобальном кэше сборок приложение [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] может прекратить работу. Это происходит вследствие того, что обслуживание или обновление библиотек в глобальном кэше сборок не обновляет сборки внутри [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Если сборка существует как в базе данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], так и в глобальном кэше сборок, обе копии сборки должны полностью совпадать. Если они не совпадают, то при использовании сборки с интеграцией со средой [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CLR возникает ошибка. При обслуживании или обновлении любых сборок в глобальном кэше сборок, которые также зарегистрированы в базе данных, включая неподдерживаемые сборки .NET Framework, обязательно выполните обслуживание или обновите копию сборки в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] базах данных с помощью инструкции **ALTER ASSEMBLY** . Дополнительные сведения см. в [статье базы знаний 949080](https://support.microsoft.com/kb/949080).  
  
## <a name="supported-libraries"></a>Поддерживаемые библиотеки  
 Начиная с [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] располагает списком поддерживаемых библиотек платформы .NET Framework, проверенных на соответствие стандартам надежности и безопасности при взаимодействии с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Поддерживаемые библиотеки не требуется явно регистрировать на сервере, прежде чем они могут быть использованы в пользовательском коде; [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] загружает их непосредственно из глобального кэша сборок.  
  
 Библиотеки и пространства имен, поддерживаемые интеграцией со средой CLR в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]:  
  
-   CustomMarshalers  
  
-   Microsoft.VisualBasic  
  
-   Microsoft.VisualC  
  
-   mscorlib  
  
-   Система  
  
-   System.Configuration  
  
-   System.Data  
  
-   System.Data.OracleClient  
  
-   System.Data.SqlXml  
  
-   System.Deployment  
  
-   System.Security  
  
-   System.Transactions  
  
-   System.Web.Services  
  
-   System.Xml  
  
-   System.Core.dll  
  
-   System.Xml.Linq.dll  
  
## <a name="unsupported-libraries"></a>Неподдерживаемые библиотеки  
 Неподдерживаемые библиотеки могут быть вызваны из управляемых хранимых процедур, триггеров, определяемых пользователем функций, определяемых пользователем типов и определяемых пользователем статистических функций. Неподдерживаемая библиотека должна быть сначала зарегистрирована в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] базе данных с помощью инструкции **CREATE ASSEMBLY** , прежде чем ее можно будет использовать в коде. Любая неподдерживаемая библиотека, зарегистрированная и работающая на сервере, должна быть просмотрена и проверена в отношении безопасности и надежности.  
  
 Например, пространство имен **System. DirectoryServices** не поддерживается. Необходимо зарегистрировать сборку System. DirectoryServices. dll с **НЕнадежными** разрешениями, прежде чем можно будет вызывать ее из кода. **НЕнадежное** разрешение необходимо, так как классы в пространстве имен **System. DirectoryServices** не соответствуют требованиям для **безопасного** или **EXTERNAL_ACCESS**. Дополнительные сведения см. в разделе [ограничения модели программирования интеграции со средой CLR](../../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md) и [Безопасность доступа к коду интеграции CLR](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md).  
  
## <a name="see-also"></a>См. также:  
 [Создание сборки](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)   
 [Безопасность доступа к коду при интеграции со средой CLR](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [Ограничения модели программирования на основе интеграции со средой CLR](../../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)  
  
  
