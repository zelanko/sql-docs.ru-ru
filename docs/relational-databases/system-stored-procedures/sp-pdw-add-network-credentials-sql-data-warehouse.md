---
description: sp_pdw_add_network_credentials (Azure синапсе Analytics)
title: sp_pdw_add_network_credentials
titleSuffix: Azure Synapse Analytics
ms.date: 03/14/2017
ms.service: sql-data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 0729eeff-ac7e-43f0-80fa-ff5346a75985
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest'
ms.custom: seo-dt-2019
ms.openlocfilehash: 0aeb775ea03d022337f45463b16e7134cfb12dc8
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97410762"
---
# <a name="sp_pdw_add_network_credentials-azure-synapse-analytics"></a>sp_pdw_add_network_credentials (Azure синапсе Analytics)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Он хранит сетевые учетные данные в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] и связывает их с сервером. Например, используйте эту хранимую процедуру, чтобы предоставить [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] соответствующие разрешения на чтение и запись для выполнения операций резервного копирования и восстановления базы данных на целевом сервере или для создания резервной копии сертификата, используемого для TDE.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql  
-- Syntax for Azure Synapse Analytics and Parallel Data Warehouse  
  
sp_pdw_add_network_credentials 'target_server_name',  'user_name', 'password'  
```  
[!INCLUDE[synapse-analytics-od-unsupported-syntax](../../includes/synapse-analytics-od-unsupported-syntax.md)]

## <a name="arguments"></a>Аргументы  
 "*target_server_name*"  
 Указывает имя узла или IP-адрес целевого сервера. [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] будет получать доступ к этому серверу с помощью учетных данных пользователя и пароля, переданных этой хранимой процедуре.  
  
 Для подключения через сеть InfiniBand используйте IP-адрес InfiniBand целевого сервера.  
  
 *target_server_name* определяется как nvarchar (337).  
  
 '*user_name*'  
 Указывает user_name, имеющую разрешения на доступ к целевому серверу. Если учетные данные для целевого сервера уже существуют, они будут обновлены до новых учетных данных.  
  
 *user_name* определяется как nvarchar (513).  
  
 '*Password* черта  
 Указывает пароль для *user_name*.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение **ALTER Server State** .  
  
## <a name="error-handling"></a>Обработка ошибок  
 Ошибка возникает, если добавление учетных данных не выполняется на управляющем узле и на всех вычислений.  
  
## <a name="general-remarks"></a>Общие замечания  
 Эта хранимая процедура добавляет сетевые учетные данные в учетную запись NetworkService для [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] . Учетная запись NetworkService запускает каждый экземпляр SMP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на управляющем узле и на вычислительных узлах. Например, при выполнении операции резервного копирования управляющий узел и каждый узел вычислений будут использовать учетные данные учетной записи NetworkService для получения разрешений на чтение и запись на целевом сервере.  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-add-credentials-for-performing-a-database-backup"></a>A. Добавление учетных данных для выполнения резервного копирования базы данных  
 В следующем примере связываются учетные данные имени пользователя и пароля для пользователя домена сеаттле\давид с целевым сервером, имеющим IP-адрес 10.172.63.255. Пользователь сеаттле\давид имеет разрешения на чтение и запись на целевом сервере. [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] сохранит эти учетные данные и будет использовать их для чтения и записи на целевом сервере, если это необходимо для операций резервного копирования и восстановления.  
  
```sql  
EXEC sp_pdw_add_network_credentials '10.172.63.255', 'seattle\david', '********';  
```  
  
 Команда Backup требует, чтобы имя сервера было указано как IP-адрес.  
  
> [!NOTE]  
>  Чтобы выполнить резервное копирование базы данных через InfiniBand, обязательно используйте IP-адрес InfiniBand сервера архивации.  
  
## <a name="see-also"></a>См. также:  
 [sp_pdw_remove_network_credentials &#40;Azure синапсе Analytics&#41;](../../relational-databases/system-stored-procedures/sp-pdw-remove-network-credentials-sql-data-warehouse.md)  
  
  

