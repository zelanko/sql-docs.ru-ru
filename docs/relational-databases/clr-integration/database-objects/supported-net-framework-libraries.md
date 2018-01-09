---
title: "Поддерживаемые библиотеки платформы .NET Framework | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], .NET Framework libraries
- .NET Framework [CLR Integration]
ms.assetid: 417544ff-c25c-496e-add4-2f278f8a4911
caps.latest.revision: "25"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 41ff7f36b26ddc1adc96bcbc9569c5a697741dd5
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="supported-net-framework-libraries"></a>Поддерживаемые библиотеки платформы .NET Framework
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]С общий язык размещенной среды выполнения (CLR) в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], можно создавать хранимые процедуры, триггеры, определяемые пользователем функции, определяемые пользователем типы и определяемые пользователем статистические функции в управляемом коде. Функциональность, реализованная в библиотеках классов платформы .NET Framework, предоставляет доступ к предварительно построенным классам для операций со строками, сложных математических операций, доступа к файлам, шифрования и т. д. Доступ к этим классам легко получить из любой управляемой хранимой процедуры, определяемого пользователем типа, триггера, определяемой пользователем функции или определяемой пользователем статистической функции.  
  
> [!NOTE]  
>  При обслуживании или обновлении неподдерживаемых сборок в глобальном кэше сборок приложение [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] может прекратить работу. Это происходит вследствие того, что обслуживание или обновление библиотек в глобальном кэше сборок не обновляет сборки внутри [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Если сборка существует как в базе данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], так и в глобальном кэше сборок, обе копии сборки должны полностью совпадать. Если они не совпадают, то при использовании сборки с интеграцией со средой [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CLR возникает ошибка. При обслуживании или обновлении любых сборок в глобальном кэше СБОРОК, которые также зарегистрированы в базе данных, включая неподдерживаемых сборок платформы .NET Framework, убедитесь, что обслуживание или обновление копии сборки внутри вашей [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] баз данных с  **ALTER ASSEMBLY** инструкции. Дополнительные сведения см. в разделе [статье 949080 базы знаний](http://support.microsoft.com/kb/949080).  
  
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
 Неподдерживаемые библиотеки могут быть вызваны из управляемых хранимых процедур, триггеров, определяемых пользователем функций, определяемых пользователем типов и определяемых пользователем статистических функций. Неподдерживаемые библиотеки, сначала должны быть зарегистрированы в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] базы данных с помощью **CREATE ASSEMBLY** инструкции, прежде чем он может использоваться в коде. Любая неподдерживаемая библиотека, зарегистрированная и работающая на сервере, должна быть просмотрена и проверена в отношении безопасности и надежности.  
  
 Например **System.DirectoryServices** пространство имен не поддерживается. Необходимо зарегистрировать сборку System.DirectoryServices.dll с **UNSAFE** разрешения, прежде чем его можно вызвать из кода приложения. **UNSAFE** разрешений необходим из-за классы в **System.DirectoryServices** пространства имен не отвечают требованиям для **БЕЗОПАСНОМ** или  **EXTERNAL_ACCESS**. Дополнительные сведения см. в разделе [ограничения модели программирования интеграции со средой CLR](../../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md) и [CLR Integration Code Access Security](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md).  
  
## <a name="see-also"></a>См. также:  
 [Создание сборки](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)   
 [Среда CLR Integration Code Access Security](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [Ограничения модели программирования на основе интеграции со средой CLR](../../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)  
  
  
