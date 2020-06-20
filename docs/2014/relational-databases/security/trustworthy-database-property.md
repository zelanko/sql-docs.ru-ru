---
title: Свойство базы данных TRUSTWORTHY | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- TRUSTWORTHY database property
ms.assetid: 64b2a53d-4416-4a19-acc0-664a61b45348
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 23391fe48037d4cd7f69aef7df6649949301a0f0
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85055315"
---
# <a name="trustworthy-database-property"></a>Свойство базы данных TRUSTWORTHY
  Свойство TRUSTWORTHY используется для указания того, доверяет ли экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базе данных и ее содержимому. По умолчанию это свойство имеет значение OFF, но его можно установить в ON при помощи инструкции ALTER DATABASE. Например, `ALTER DATABASE AdventureWorks2012 SET TRUSTWORTHY ON;`.  
  
> [!NOTE]  
>  Изменять это свойство могут только члены предопределенной роли сервера **sysadmin** .  
  
 Это свойство позволяет уменьшить уязвимость системы перед рядом угроз, связанных с присоединением базы данных, содержащей один из следующих объектов:  
  
-   вредоносные сборки с параметром разрешения EXTERNAL_ACCESS или UNSAFE. Дополнительные сведения см. в статье [CLR Integration Security](../clr-integration/security/clr-integration-security.md).  
  
-   вредоносные модули, выполняемые в контексте привилегированных пользователей. Дополнительные сведения см. в разделе [Предложение EXECUTE AS (Transact-SQL)](/sql/t-sql/statements/execute-as-clause-transact-sql).  
  
 В обеих ситуациях объектам нужны конкретные права доступа, что повышает уязвимость системы. Для защиты от атак при использовании таких объектов в контексте базы данных, уже присоединенной к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], применяют соответствующие механизмы. Однако, если база данных переведена в режим работы «вне сети», пользователь, имеющий доступ к файлу базы данных, теоретически может присоединить ее к любому экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и добавить в нее вредоносное содержимое. Когда в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]отсоединяются и присоединяются базы данных, для файлов данных и журналов задаются определенные разрешения, ограничивающие доступ к файлам базы данных.  
  
 Так как база данных, присоединенная к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , не может сразу стать доверенной, то ей не разрешается доступ к ресурсам вне ее области до тех пор, пока не будет явно отмечена как доверенная. Для успешного выполнения модулей, которые обращаются к ресурсам, внешним по отношению к базе данных, и сборок с параметром разрешения EXTERNAL_ACCESS или UNSAFE нужно, чтобы были удовлетворены кое-какие дополнительные требования.  
  
## <a name="related-content"></a>См. также  
 [Центр безопасности для ядра СУБД SQL Server и Базы данных Azure SQL](security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
