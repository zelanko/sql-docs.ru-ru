---
title: Разрешение сетевого доступа к зеркальному отображению базы данных с использованием проверки подлинности Windows | Документы Майкрософт
ms.custom: ''
ms.date: 05/17/2016
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.suite: sql
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Windows authentication [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: 28c8fec5-5feb-4c84-8d72-f2bd1ae3b40d
caps.latest.revision: 34
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 74420606416675428b19351327aefb78b6dab22b
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35311473"
---
# <a name="database-mirroring---allow-network-access---windows-authentication"></a>Разрешение сетевого доступа к зеркальному отображению базы данных с использованием проверки подлинности Windows
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  При проверке подлинности Windows для соединения с конечными точками зеркального отображения базы данных двух экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимо вручную задать учетные записи для входа с учетом следующих факторов.  
  
-   Если экземпляры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняются как службы под разными учетными записями домена (одного или других доверенных доменов), нужно создать имя входа для каждой учетной записи в базе данных **master** на каждом удаленном экземпляре сервера и предоставить этому имени входа разрешение CONNECT для конечной точки.  
  
-   Если экземпляры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняются как учетные записи сетевой службы, нужно создать в базе данных **master** на каждом из удаленных экземпляров серверов имя входа для каждой учетной записи главного компьютера (*имя_домена***\\***имя_компьютера$*) и предоставить этому имени входа разрешение CONNECT для конечной точки. Это обусловлено тем, что экземпляр сервера, выполняемый под учетной записью Network Service, выполняет проверку подлинности с помощью учетной записи домена главного компьютера.  
  
> [!NOTE]  
>  Убедитесь, что конечная точка существует для каждого из экземпляров сервера. Дополнительные сведения см. в разделе [Создание конечной точки зеркального отображения базы данных с проверкой подлинности Windows (Transact-SQL)](../../database-engine/database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md).  
  
### <a name="to-configure-logins-for-windows-authentication"></a>Настройка имен входа для проверки подлинности Windows  
  
1.  Для учетной записи пользователя каждого экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]создайте имя входа в других экземплярах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Выполняйте инструкцию [CREATE LOGIN](../../t-sql/statements/create-login-transact-sql.md) с предложением FROM WINDOWS.  
  
     Дополнительные сведения см. в разделе [Создание имени входа](../../relational-databases/security/authentication-access/create-a-login.md).  
  
2.  Кроме того, чтобы выполнивший вход пользователь гарантированно имел доступ к конечной точке, предоставьте имени входа разрешения на соединение с конечной точкой с помощью инструкции [GRANT](../../t-sql/statements/grant-transact-sql.md) . Обратите внимание, что разрешения на подключение к конечной точке предоставлять не требуется, если пользователь является администратором.  
  
     Дополнительные сведения см. в статье [Grant a Permission to a Principal](../../relational-databases/security/authentication-access/grant-a-permission-to-a-principal.md).  
  
## <a name="example"></a>Пример  
 В следующем примере [!INCLUDE[tsql](../../includes/tsql-md.md)] создается имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для учетной записи пользователя `Otheruser` , которая принадлежит домену `Adomain`. Затем пользователю предоставляются разрешения на подключение к существующей конечной точке зеркального отображения базы данных `Mirroring_Endpoint`.  
  
```  
USE master;  
GO  
CREATE LOGIN [Adomain\Otheruser] FROM WINDOWS;  
GO  
GRANT CONNECT on ENDPOINT::Mirroring_Endpoint TO [Adomain\Otheruser];  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Обзор групп доступности AlwaysOn (SQL Server)](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Зеркальное отображение базы данных (SQL Server)](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   
 [Безопасность транспорта для зеркального отображения баз данных и групп доступности AlwaysOn (SQL Server)](../../database-engine/database-mirroring/transport-security-database-mirroring-always-on-availability.md)   
 [Конечная точка зеркального отображения базы данных (SQL Server)](../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md)  
  
  
