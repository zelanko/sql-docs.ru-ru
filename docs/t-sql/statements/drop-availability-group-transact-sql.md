---
description: DROP AVAILABILITY GROUP (Transact-SQL)
title: DROP AVAILABILITY GROUP (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP_AVAILABILITY_GROUP_TSQL
- DROP AVAILABILITY GROUP
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], removing
- Availability Groups [SQL Server], Transact-SQL statements
- DROP AVAILABILITY GROUP statement
- Availability Groups [SQL Server], dropping
ms.assetid: c1600289-c990-454a-b279-dba0ebd5d63e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d2335b8015f0eb88821e94231ac8cf48d9bc0471
ms.sourcegitcommit: bd3a135f061e4a49183bbebc7add41ab11872bae
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/21/2020
ms.locfileid: "92300387"
---
# <a name="drop-availability-group-transact-sql"></a>DROP AVAILABILITY GROUP (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Удаляет указанную группу доступности и все ее реплики. Если экземпляр сервера, на котором размещена одна из реплик доступности, находится в режиме «вне сети» при удалении группы доступности, то после перехода в режим «в сети» локальная реплика доступности будет удалена с экземпляра сервера. При удалении группы доступности также удаляется и связанный с ней прослушиватель группы доступности, если он существует.  
  
> [!IMPORTANT]  
>  Если возможно, удаляйте группу доступности только при наличии подключения к экземпляру сервера, где размещена первичная реплика. При удалении группы доступности с первичной реплики разрешается внесение изменений в бывшие базы данных-источники (без защиты высокого уровня доступности). Удаление группы доступности из вторичной реплики переводит первичную реплику в состояние **RESTORING** (восстановление), и в базы данных не разрешается вносить изменения.  
  
 Сведения о других способах удаления группы доступности см. в разделе [Удаление группы доступности (SQL Server)](../../database-engine/availability-groups/windows/remove-an-availability-group-sql-server.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
DROP AVAILABILITY GROUP group_name   
[ ; ]  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 *group_name*  
 Указывает имя удаляемой группы доступности.  
  
## <a name="limitations-and-recommendations"></a>Ограничения  
  
-   Для выполнения инструкции **DROP AVAILABILITY GROUP** необходимо, чтобы на экземпляре сервера были включены группы доступности AlwaysOn. Дополнительные сведения см. в разделе [Включение и отключение групп доступности AlwaysOn (SQL Server)](../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md).  
  
-   **DROP AVAILABILITY GROUP** не может выполняться в составе пакетов или транзакций. В этой инструкции также не поддерживаются выражения и переменные.  
  
-   Группу доступности можно удалить из любого узла отказоустойчивой кластеризации сервера Windows (WSFC), обладающего учетными данными, соответствующими группе доступности. Благодаря этому обеспечивается возможность удаления группы доступности при отсутствии ее оставшихся реплик доступности.  
  
    > [!IMPORTANT]  
    >  Старайтесь не удалять группу доступности, если отказоустойчивый кластер Windows Server (WSFC) не имеет кворума. Если необходимо удалить группу доступности, когда нет кворума кластера, то группа доступности метаданных, хранимая в кластере, не удаляется. После того как кластер снова получит кворум, необходимо будет удалить группу доступности еще раз, чтобы удалить ее из кластера WSFC.  
  
-   На вторичной реплике команда **DROP AVAILABILITY GROUP** должна использоваться только в экстренных случаях. Это связано с тем, что удаление группы доступности переводит группу в режим «вне сети». При удалении группы доступности из вторичной реплики первичная реплика не может определить, возникло состояние **OFFLINE** из-за потери кворума, принудительного перехода на другой ресурс или команды **DROP AVAILABILITY GROUP** . Первичная реплика переходит в состояние **RESTORING** , чтобы избежать возможной ситуации с дроблением. Дополнительные сведения см. в статье [Поведение инструкции DROP AVAILABILITY GROUP](/archive/blogs/psssql/how-it-works-drop-availability-group-behaviors) (блог инженеров CSS SQL Server).  
  
## <a name="security"></a>Безопасность  
  
### <a name="permissions"></a>Разрешения  
 Необходимо разрешение **ALTER AVAILABILITY GROUP** для группы доступности, разрешение **CONTROL AVAILABILITY GROUP** , разрешение **ALTER ANY AVAILABILITY GROUP** или разрешение **CONTROL SERVER** . Для удаления группы доступности, которая не размещена на экземпляре локального сервера, необходимо разрешение **CONTROL SERVER** или разрешение **CONTROL** для этой группы доступности.  
  
## <a name="examples"></a>Примеры  
 В следующем примере удаляется группа доступности `AccountsAG`.  
  
```sql  
DROP AVAILABILITY GROUP AccountsAG;  
```  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> См. также  
  
-   [Принцип работы. Поведение инструкции DROP AVAILABILITY GROUP](/archive/blogs/psssql/how-it-works-drop-availability-group-behaviors) (блог инженеров CSS SQL Server)  
  
## <a name="see-also"></a>См. также:  
 [ALTER AVAILABILITY GROUP (Transact-SQL)](../../t-sql/statements/alter-availability-group-transact-sql.md)   
 [CREATE AVAILABILITY GROUP (Transact-SQL)](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [Удаление группы доступности (SQL Server)](../../database-engine/availability-groups/windows/remove-an-availability-group-sql-server.md)  
  
