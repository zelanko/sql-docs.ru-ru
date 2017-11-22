---
title: "DROP AVAILABILITY GROUP (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP_AVAILABILITY_GROUP_TSQL
- DROP AVAILABILITY GROUP
dev_langs: TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], removing
- Availability Groups [SQL Server], Transact-SQL statements
- DROP AVAILABILITY GROUP statement
- Availability Groups [SQL Server], dropping
ms.assetid: c1600289-c990-454a-b279-dba0ebd5d63e
caps.latest.revision: "44"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5d097f90cfabc250921c3212ed0a89e85362c0f6
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="drop-availability-group-transact-sql"></a>DROP AVAILABILITY GROUP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Удаляет указанную группу доступности и все ее реплики. Если экземпляр сервера, на котором размещена одна из реплик доступности, находится в режиме «вне сети» при удалении группы доступности, то после перехода в режим «в сети» локальная реплика доступности будет удалена с экземпляра сервера. При удалении группы доступности также удаляется и связанный с ней прослушиватель группы доступности, если он существует.  
  
> [!IMPORTANT]  
>  Если возможно, удаляйте группу доступности только при наличии подключения к экземпляру сервера, где размещена первичная реплика. При удалении группы доступности с первичной реплики разрешается внесение изменений в бывшие базы данных-источники (без защиты высокого уровня доступности). Удаление группы доступности из вторичной реплики переводит первичную реплику в **RESTORING** состояния и изменения не разрешены в базах данных.  
  
 Сведения о других способах удаления группы доступности см. в разделе [удалить группу доступности &#40; SQL Server &#41; ](../../database-engine/availability-groups/windows/remove-an-availability-group-sql-server.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DROP AVAILABILITY GROUP group_name   
[ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *имя_группы*  
 Указывает имя удаляемой группы доступности.  
  
## <a name="limitations-and-recommendations"></a>Ограничения  
  
-   Выполнение **DROP AVAILABILITY GROUP** необходимо включить функцию групп доступности AlwaysOn на экземпляре сервера. Дополнительные сведения см. в разделе [Включение и отключение групп доступности AlwaysOn (SQL Server)](../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md).  
  
-   **DROP AVAILABILITY GROUP** не может выполняться в составе пакетов или транзакций. В этой инструкции также не поддерживаются выражения и переменные.  
  
-   Группу доступности можно удалить из любого узла отказоустойчивой кластеризации сервера Windows (WSFC), обладающего учетными данными, соответствующими группе доступности. Благодаря этому обеспечивается возможность удаления группы доступности при отсутствии ее оставшихся реплик доступности.  
  
    > [!IMPORTANT]  
    >  Старайтесь не удалять группу доступности, если отказоустойчивый кластер Windows Server (WSFC) не имеет кворума. Если необходимо удалить группу доступности, когда нет кворума кластера, то группа доступности метаданных, хранимая в кластере, не удаляется. После того как кластер снова получит кворум, необходимо будет удалить группу доступности еще раз, чтобы удалить ее из кластера WSFC.  
  
-   На вторичной реплике **DROP AVAILABILITY GROUP** следует использовать только в экстренных случаях. Это связано с тем, что удаление группы доступности переводит группу в режим «вне сети». При удалении группы доступности из вторичной реплики первичная реплика не может определить, является ли **OFFLINE** состояние возникло из-за потери кворума, принудительного перехода на другой ресурс или **DROP AVAILABILITY GROUP**команды. Первичная реплика переходит **RESTORING** состояние, чтобы избежать возможной ситуации с дроблением. Дополнительные сведения см. в статье [Поведение инструкции DROP AVAILABILITY GROUP](http://blogs.msdn.com/b/psssql/archive/2012/06/13/how-it-works-drop-availability-group-behaviors.aspx) (блог инженеров CSS SQL Server).  
  
## <a name="security"></a>Безопасность  
  
### <a name="permissions"></a>Permissions  
 Требуется **ALTER AVAILABILITY GROUP** разрешение для группы доступности, **CONTROL AVAILABILITY GROUP** разрешение, **ALTER ANY AVAILABILITY GROUP** разрешение, или **CONTROL SERVER** разрешение. Для удаления группы доступности, которая не размещена на экземпляре локального сервера, необходимо **CONTROL SERVER** разрешение или **УПРАВЛЕНИЯ** разрешение для этой группы доступности.  
  
## <a name="examples"></a>Примеры  
 В следующем примере удаляется группа доступности `AccountsAG`.  
  
```  
DROP AVAILABILITY GROUP AccountsAG;  
```  
  
##  <a name="RelatedContent"></a> См. также  
  
-   [Принцип работы. Поведение инструкции DROP AVAILABILITY GROUP](http://blogs.msdn.com/b/psssql/archive/2012/06/13/how-it-works-drop-availability-group-behaviors.aspx) (блог инженеров CSS SQL Server)  
  
## <a name="see-also"></a>См. также:  
 [ALTER AVAILABILITY GROUP (Transact-SQL)](../../t-sql/statements/alter-availability-group-transact-sql.md)   
 [CREATE AVAILABILITY GROUP (Transact-SQL)](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [Удаление группы доступности (SQL Server)](../../database-engine/availability-groups/windows/remove-an-availability-group-sql-server.md)  
  
  
