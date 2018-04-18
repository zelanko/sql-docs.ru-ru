---
title: sp_pdw_add_network_credentials (хранилище данных SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 0729eeff-ac7e-43f0-80fa-ff5346a75985
caps.latest.revision: 10
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 3d318447603f37153ecc62878061e0f44349347f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sppdwaddnetworkcredentials-sql-data-warehouse"></a>sp_pdw_add_network_credentials (хранилище данных SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Сетевые учетные данные в нем хранятся [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] и связывает их с сервера. Например, использовать эту хранимую процедуру для предоставления [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] соответствующие разрешения чтения и записи резервной копии базы данных и восстановления на целевом сервере, или создать резервную копию сертификата, используемого для прозрачного шифрования данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL (Transact-SQL)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_add_network_credentials 'target_server_name',  'user_name', ꞌpasswordꞌ  
```  
  
## <a name="arguments"></a>Аргументы  
 '*target_server_name*'  
 Указывает имя целевого сервера узла или IP-адрес. [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] будет доступ к этому серверу с помощью учетных данных имени пользователя и пароля, передаваемых этой хранимой процедуры.  
  
 Для подключения по сети InfiniBand, используйте InfiniBand IP-адрес целевого сервера.  
  
 *имя_сервера_назначения* определяется как nvarchar(337).  
  
 '*user_name*'  
 Указывает, функция user_name, имеющую разрешения на доступ к целевой сервер. Если учетные данные уже существуют для целевого сервера, они обновляются новыми учетными данными.  
  
 *имя_пользователя* определяется как nvarchar (513).  
  
 "*пароль*ꞌ  
 Указывает пароль для *имя_пользователя*.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="permissions"></a>Разрешения  
 Требуется **ALTER SERVER STATE** разрешение.  
  
## <a name="error-handling"></a>Обработка ошибок  
 Произошла ошибка при добавлении учетных данных завершилась с ошибками на узле управления, а все вычислительные узлы.  
  
## <a name="general-remarks"></a>Общие замечания  
 Эта хранимая процедура добавляет сетевые учетные данные учетной записи NetworkService для [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. Учетной записи NetworkService выполняется каждый экземпляр SMP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на узел элемента управления и вычислительных узлов. Например при выполнении операции резервного копирования, узел элемента управления и каждый вычислительный узел будет использовать учетные данные учетной записи NetworkService с целью чтения и разрешение на запись на целевой сервер.  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-add-credentials-for-performing-a-database-backup"></a>A. Добавьте учетные данные для выполнения резервной копии базы данных  
 В следующем примере имя и пароль учетных данных для seattle\david пользователя домена связывается с целевым сервером с IP-адресом 10.172.63.255. Seattle\david пользователь имеет разрешения на чтение и запись на целевой сервер. [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] будет хранить эти учетные данные и использовать их для чтения и записи к и из целевого сервера, необходимые для резервного копирования и операциями восстановления.  
  
```  
EXEC sp_pdw_add_network_credentials '10.172.63.255', 'seattle\david', '********';  
```  
  
 Команды резервного копирования требует, что имя сервера ввести IP-адрес.  
  
> [!NOTE]  
>  Создание резервной копии базы данных через InfiniBand, обязательно используйте InfiniBand IP-адрес резервного сервера.  
  
## <a name="see-also"></a>См. также  
 [sp_pdw_remove_network_credentials &#40;хранилище данных SQL&#41;](../../relational-databases/system-stored-procedures/sp-pdw-remove-network-credentials-sql-data-warehouse.md)  
  
  

