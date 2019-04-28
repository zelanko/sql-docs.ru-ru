---
title: Присоединение вторичной реплики к группе доступности (SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.joinreplica.f1
helpviewer_keywords:
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], joining
- Availability Groups [SQL Server], configuring
ms.assetid: e5bd2489-097a-490e-8ea1-34fe48378ad1
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f667ff368ca54f2ccfaeab47716338c7d694c1da
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62792160"
---
# <a name="join-a-secondary-replica-to-an-availability-group-sql-server"></a>Присоединение вторичной реплики к группе доступности (SQL Server)
  В этом разделе описывается присоединение вторичной реплики к группе доступности AlwaysOn с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]или PowerShell в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. После добавления вторичной реплики в группу доступности AlwaysOn необходимо присоединить эту реплику к группе доступности. Операция присоединения реплики должна быть выполнена на экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , на котором находится вторичная реплика.  
  
-   **Перед началом:**  
  
     [Предварительные требования](#Prerequisites)  
  
     [безопасность](#Security)  
  
-   **Подготовка базы данных-получателя с помощью различных средств.**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
-   **Дальнейшие действия.** [Настройте базы данных-получатели](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Prerequisites"></a> Предварительные требования  
  
-   Первичная реплика группы доступности должна быть в сети.  
  
-   Пользователь должен быть подключен к экземпляру сервера, на котором находится дополнительная реплика, которая еще не была присоединена к группе доступности.  
  
-   Экземпляр локального сервера должен иметь возможность подключения к конечной точке зеркального отображения базы данных на экземпляре сервера, где находится первичная реплика.  
  
> [!IMPORTANT]  
>  Если какое-либо из предварительных условий не выполняется, происходит сбой операции соединения. После неудачной попытки соединения может быть необходимо подключиться к экземпляру сервера, на котором содержится первичная реплика, чтобы удалить и повторно добавить вторичную реплику, прежде чем можно будет выполнить соединение с группой доступности. Дополнительные сведения см. в разделах [Удаление вторичной реплики из группы доступности (SQL Server)](remove-a-secondary-replica-from-an-availability-group-sql-server.md) и [Добавление вторичной реплики к группе доступности (SQL Server)](add-a-secondary-replica-to-an-availability-group-sql-server.md).  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Необходимо разрешение ALTER AVAILABILITY GROUP для группы доступности, разрешение CONTROL AVAILABILITY GROUP, разрешение ALTER ANY AVAILABILITY GROUP или разрешение CONTROL SERVER.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 **Присоединение реплики доступности к группе доступности**  
  
1.  В обозревателе объектов подключитесь к экземпляру сервера, на котором размещена вторичная реплика, и щелкните имя сервера, чтобы развернуть его дерево.  
  
2.  Разверните узел **Высокий уровень доступности AlwaysOn** и узел **Группы доступности** .  
  
3.  Выберите группу доступности вторичной реплики, к которой выполнено подключение.  
  
4.  Щелкните правой кнопкой мыши вторичную реплику и выберите пункт **Включить в группу доступности**.  
  
5.  Откроется диалоговое окно **Присоединить реплику к группе доступности** .  
  
6.  Чтобы присоединить вторичную реплику к группе доступности, нажмите кнопку **ОК**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Присоединение реплики доступности к группе доступности**  
  
1.  Подключитесь к экземпляру сервера, на котором находится дополнительная реплика.  
  
2.  Инструкция [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) используется следующим образом:  
  
     ALTER AVAILABILITY GROUP *имя_группы* JOIN  
  
     где *имя_группы* — это имя группы доступности.  
  
     В следующем примере объединяются дополнительная реплика и группа доступности `MyAG`.  
  
    ```  
    ALTER AVAILABILITY GROUP MyAG JOIN;  
    ```  
  
    > [!NOTE]  
    >  Пример использования инструкции [!INCLUDE[tsql](../../../includes/tsql-md.md)] в контексте см. в статье [Создание группы доступности (Transact-SQL)](create-an-availability-group-transact-sql.md).  
  
##  <a name="PowerShellProcedure"></a> Использование PowerShell  
 **Присоединение реплики доступности к группе доступности**  
  
 В поставщике [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell:  
  
1.  Перейдите в каталог (`cd`) экземпляра сервера, на котором размещается вторичная реплика.  
  
2.  Присоедините вторичную реплику к группе доступности, выполнив командлет **Join-SqlAvailabilityGroup** с именем группы доступности.  
  
     Например, следующая команда присоединяет вторичную реплику, размещенную на экземпляре сервера по указанному пути, к группе доступности `MyAg`.  На этом экземпляре сервера должна быть размещена вторичная реплика этой группы доступности.  
  
    ```  
    Join-SqlAvailabilityGroup -Path SQLSERVER:\SQL\SecondaryServer\InstanceName -Name 'MyAg'  
    ```  
  
    > [!NOTE]  
    >  Чтобы просмотреть синтаксис командлета, воспользуйтесь командлетом `Get-Help` в среде [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Дополнительные сведения см. в разделе [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
 **Настройка и использование поставщика SQL Server PowerShell**  
  
-   [Поставщик SQL Server PowerShell](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="FollowUp"></a> Дальнейшие действия. Настройка базы данных-получатели  
 Для каждой базы данных в группе доступности необходимо настроить базу данных-получатель на экземпляре сервера, где находится дополнительная реплика. Настроить базы данных-получатели до или после присоединения дополнительной реплики к группе доступности можно следующим образом.  
  
1.  Восстановите последние базы данных и резервные копии журналов каждой базы данных-источника на экземпляр сервера, где находится вторичная реплика, используя инструкцию RESTORE WITH NORECOVERY для каждой операции восстановления. Дополнительные сведения см. в статье [Ручная подготовка базы данных-получателя для присоединения к группе доступности (SQL Server)](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).  
  
2.  Присоедините каждую базу данных-получатель к группе доступности. Дополнительные сведения см. в статье [Присоединение базы данных-получателя к группе доступности (SQL Server)](join-a-secondary-database-to-an-availability-group-sql-server.md).  
  
## <a name="see-also"></a>См. также  
 [Создание и настройка групп доступности (SQL Server)](creation-and-configuration-of-availability-groups-sql-server.md)   
 [Обзор групп доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Устранение неполадок с конфигурацией групп доступности AlwaysOn &#40;SQL Server&#41;удален](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
  
