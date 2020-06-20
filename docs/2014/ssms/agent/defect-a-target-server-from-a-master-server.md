---
title: Отключение целевого сервера от главного | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- target servers [SQL Server], defecting
- SQL Server Agent jobs, master servers
- master servers [SQL Server], defecting target servers
- defecting target servers
ms.assetid: a6da262b-7b38-4ce4-bfd6-6a557c6e8a84
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2b17703fa87f5c0d3e7146a1660ac1ca7c7c1d81
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85008926"
---
# <a name="defect-a-target-server-from-a-master-server"></a>Отключение целевого сервера от главного сервера
  В этом разделе описывается исключение целевого сервера из главного в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] или управляющих объектов SQL Server (SMO). Запустите эту процедуру на целевом сервере.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Безопасность](#Security)  
  
-   **Для исключения целевого сервера используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [ОБЪЕКТАХ](#PowerShellProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Для выполнения этой хранимой процедуры пользователь должен быть членом предопределенной роли сервера `sysadmin`.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-defect-a-target-server-from-a-master-server"></a>Отключение целевого сервера от главного  
  
1.  В **обозревателе объектов**разверните сервер, настроенный как целевой сервер.  
  
2.  Щелкните правой кнопкой мыши **Агент SQL Server**, выберите **Администрирование нескольких серверов**и нажмите **Отключить**.  
  
3.  Щелкните **Да** , подтверждая, что этот целевой сервер необходимо отключить от главного сервера.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-defect-a-target-server-from-a-master-server"></a>Отключение целевого сервера от главного  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
```sql
sp_msx_defect ;  
```  
  
 Дополнительные сведения см. в разделе [sp_msx_defect &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-defect-transact-sql).  
  
##  <a name="using-sql-server-management-objects-smo"></a><a name="PowerShellProcedure"></a>Использование управляющие объекты SQL Server (SMO)  
 Используйте `MsxDefect Method`.  
  
## <a name="see-also"></a>См. также:  
 [Создание многосерверной среды](create-a-multiserver-environment.md)   
 [Автоматизированное администрирование в масштабах предприятия](automated-administration-across-an-enterprise.md)   
 [Отключение нескольких целевых серверов от главного](defect-multiple-target-servers-from-a-master-server.md)  
