---
title: Удаление точки управления служебной программой (служебная программа SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: c048a416-900e-4c77-8243-e0f0d8b94068
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b4325be141d93a684a0cbb31a6f2c91197704ba4
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85023300"
---
# <a name="remove-a-utility-control-point-sql-server-utility"></a>удалить точку управления служебной программой (SQL Server Utility)
  В этом разделе описывается удаление точки управления служебной программой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Для удаления точки управления служебной программы используется:**  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
 До использования этой процедуры до удаления пункта управления программой из программы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] следует учесть следующие обстоятельства. При выполнении операции хранимая процедура выполнит проверку готовности к установке.  
  
-   До выполнения этой процедуры все управляемые экземпляры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимо удалить из точки управления служебной программой. Обратите внимание, что пункт управления программой является управляемым экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [Удаление экземпляра SQL Server из служебной программы SQL Server](remove-an-instance-of-sql-server-from-the-sql-server-utility.md).  
  
-   Эта процедура должна запускаться на компьютере, являющемся точкой управления служебной программой.  
  
-   Если экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , где удален пункт управления служебной программой, содержал набор элементов сбора, не относящийся к служебной программе, эта процедура не удаляет базу данных UMDW (sysutility_mdw). В этом случае перед повторным созданием точки управления служебной программой необходимо вручную удалить базу данных UMDW (sysutility_mdw).  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Эта процедура должна выполняться пользователем, имеющим разрешения `sysadmin`, необходимые для создания точки управления служебной программой.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-remove-a-utility-control-point"></a>Удаление точки управления служебной программой  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
```  
EXEC msdb.dbo.sp_sysutility_ucp_remove;  
```  
  
## <a name="see-also"></a>См. также:  
 [Функции и задачи служебной программы SQL Server](sql-server-utility-features-and-tasks.md)   
 [Использование проводника служебных программ для управления служебной программой SQL Server](use-utility-explorer-to-manage-the-sql-server-utility.md)   
 [Устранение неполадок служебной программы SQL Server](../../database-engine/troubleshoot-the-sql-server-utility.md)  
  
  
