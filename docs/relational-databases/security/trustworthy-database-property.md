---
title: Свойство базы данных TRUSTWORTHY | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: security
ms.reviewer: ''
ms.suite: sql
ms.technology: security
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- TRUSTWORTHY database property
ms.assetid: 64b2a53d-4416-4a19-acc0-664a61b45348
caps.latest.revision: 22
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: f0bf333e1836c56b17799a90ccc6a279245d69cf
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2018
ms.locfileid: "35696645"
---
# <a name="trustworthy-database-property"></a>Свойство базы данных TRUSTWORTHY
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Свойство TRUSTWORTHY используется для указания того, доверяет ли экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базе данных и ее содержимому. По умолчанию это свойство имеет значение OFF, но его можно установить в ON при помощи инструкции ALTER DATABASE. Например, `ALTER DATABASE AdventureWorks2012 SET TRUSTWORTHY ON;`.  
  
> [!NOTE]  
>  Изменять это свойство могут только члены предопределенной роли сервера **sysadmin** .  
  
 Это свойство позволяет уменьшить уязвимость системы перед рядом угроз, связанных с присоединением базы данных, содержащей один из следующих объектов:  
  
-   вредоносные сборки с параметром разрешения EXTERNAL_ACCESS или UNSAFE. Дополнительные сведения см. в статье [CLR Integration Security](../../relational-databases/clr-integration/security/clr-integration-security.md).  
  
-   вредоносные модули, выполняемые в контексте привилегированных пользователей. Дополнительные сведения см. в разделе [Предложение EXECUTE AS (Transact-SQL)](../../t-sql/statements/execute-as-clause-transact-sql.md).  
  
 В обеих ситуациях объектам нужны конкретные права доступа, что повышает уязвимость системы. Для защиты от атак при использовании таких объектов в контексте базы данных, уже присоединенной к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], применяют соответствующие механизмы. Однако, если база данных переведена в режим работы «вне сети», пользователь, имеющий доступ к файлу базы данных, теоретически может присоединить ее к любому экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и добавить в нее вредоносное содержимое. Когда в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]отсоединяются и присоединяются базы данных, для файлов данных и журналов задаются определенные разрешения, ограничивающие доступ к файлам базы данных.  
  
 Так как база данных, присоединенная к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , не может сразу стать доверенной, то ей не разрешается доступ к ресурсам вне ее области до тех пор, пока не будет явно отмечена как доверенная. Для успешного выполнения модулей, которые обращаются к ресурсам, внешним по отношению к базе данных, и сборок с параметром разрешения EXTERNAL_ACCESS или UNSAFE нужно, чтобы были удовлетворены кое-какие дополнительные требования.  
  
## <a name="related-content"></a>См. также  
 [Центр обеспечения безопасности для базы данных Azure SQL и SQL Server Database Engine](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)  
  
  
