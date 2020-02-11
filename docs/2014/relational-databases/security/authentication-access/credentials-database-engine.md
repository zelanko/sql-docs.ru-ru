---
title: Учетные данные (ядро СУБД) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- principals [SQL Server], credentials
- schemas [SQL Server], credentials
- permissions [SQL Server], credentials
- groups [SQL Server], credentials
- ALTER ANY CREDENTIAL permission
- security [SQL Server], credentials
- authentication [SQL Server], credentials
- users [SQL Server], credentials
- credentials [SQL Server], about credentials
- credentials [SQL Server]
ms.assetid: c8df6022-e0b4-46b8-9670-3f86938d3177
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: d42f93735723c81baf837736bfabcda2b1707aae
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63011831"
---
# <a name="credentials-database-engine"></a>Учетные данные (компонент Database Engine)
  Учетные данные представляют собой запись, которая содержит сведения для проверки подлинности (учетные данные), которые необходимы для подключения к ресурсу вне [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Эти сведения используются [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Большинство учетных данных содержат имя пользователя Windows и пароль.  
  
 Хранимые в учетных данных сведения позволяют пользователю, подключившемуся к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с применением проверки подлинности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , обращаться к ресурсам, размещенным вне данного экземпляра сервера. Когда внешним ресурсом является ОС Windows, проверяется соответствие данных пользователя сведениям, указанным в учетной записи Windows. Одни учетные данные могут соответствовать нескольким зарегистрированным именам входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Но имя входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] может соответствовать только одним учетным данным.  
  
 Системные учетные данные создаются автоматически и связываются с определенными конечными точками. Имена для системных учетных данных начинаются с двух символов решетки (##).  
  
 Дополнительные сведения об учетных данных см. в представлении каталога [sys. Credentials](/sql/relational-databases/system-catalog-views/sys-credentials-transact-sql) .  
  
## <a name="related-content"></a>См. также  
 [Создание учетных данных](../authentication-access/create-a-credential.md) [Создание учетных данных &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql)  
  
 [Обеспечение безопасности SQL Server](../securing-sql-server.md)  
  
  
