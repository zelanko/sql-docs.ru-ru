---
title: Замена xp_sqlagent_proxy_account, расширенная хранимая процедура новых хранимых процедур | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- xp_sqlagent_proxy_account
ms.assetid: 0e3cc931-6237-41dd-bf0d-0c03f4d8fff2
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 320c7c719752a08f5b41531d7861646aa9ffe423
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48181164"
---
# <a name="replace-usage-of-the-xpsqlagentproxyaccount-extended-stored-procedure-with-new-stored-procedures"></a>Замена вызовов расширенной хранимой процедуры xp_sqlagent_proxy_account на вызовы новых хранимых процедур
  Агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает несколько посредников. Они должны быть определены при помощи нового набора хранимых процедур. Дополнительные сведения о новых хранимых процедурах агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в следующих разделах электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   sp_add_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])  
  
-   sp_delete_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])  
  
-   sp_enum_login_for_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])  
  
-   sp_enum_proxy_for_subsystem ([!INCLUDE[tsql](../../includes/tsql-md.md)])  
  
-   sp_enum_sqlagent_subsystems ([!INCLUDE[tsql](../../includes/tsql-md.md)])  
  
-   sp_grant_proxy_to_subsystem ([!INCLUDE[tsql](../../includes/tsql-md.md)])  
  
-   sp_grant_login_to_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])  
  
-   sp_help_proxy" ([!INCLUDE[tsql](../../includes/tsql-md.md)])  
  
-   sp_revoke_login_from_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])  
  
-   sp_revoke_proxy_from_subsystem ([!INCLUDE[tsql](../../includes/tsql-md.md)])  
  
-   sp_update_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])  
  
> [!NOTE]  
>  После обновления до [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], все инструкции, использующие **xp_sqlagent_proxy_account** расширенной хранимой процедуры не будет работать. Используйте **sp_xp_cmdshell_proxy_account** вместо **xp_sqlagent_proxy_account** задать прокси-сервер для **xp_cmdshell**.  
  
## <a name="component"></a>Компонент  
 Агент[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]   
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления агента SQL Server](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
