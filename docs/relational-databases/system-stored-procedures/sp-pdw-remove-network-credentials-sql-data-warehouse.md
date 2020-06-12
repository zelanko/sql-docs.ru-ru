---
title: sp_pdw_remove_network_credentials
titleSuffix: Azure SQL Data Warehouse
ms.date: 03/14/2017
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.service: sql-data-warehouse
ms.subservice: design
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: c12696a2-5939-402b-9866-8a837ca4c0a3
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.custom: seo-dt-2019
ms.openlocfilehash: 12adbc7c7f10b16591b2fc8c6b0473e86036957b
ms.sourcegitcommit: 1be90e93980a8e92275b5cc072b12b9e68a3bb9a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84627573"
---
# <a name="sp_pdw_remove_network_credentials-sql-data-warehouse"></a>sp_pdw_remove_network_credentials (хранилище данных SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  При этом удаляются сетевые учетные данные, хранящиеся в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] , для доступа к общей сетевой папке. Например, эта хранимая процедура используется для удаления разрешения на [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] выполнение операций резервного копирования и восстановления на сервере, который находится в вашей сети.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_remove_network_credentials 'target_server_name'  
```  
  
## <a name="arguments"></a>Аргументы  
 "*target_server_name*"  
 Указывает имя узла или IP-адрес целевого сервера. Учетные данные для доступа к этому серверу будут удалены из [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] . Это не приводит к изменению или удалению каких-либо разрешений на фактическом целевом сервере, который управляется вашей группой.  
  
 *target_server_name* определяется как nvarchar (337).  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение **ALTER Server State** .  
  
## <a name="error-handling"></a>Обработка ошибок  
 Ошибка возникает, если не удается удалить учетные данные на управляющем узле и на всех вычислений.  
  
## <a name="general-remarks"></a>Общие замечания  
 Эта хранимая процедура удаляет сетевые учетные данные из учетной записи NetworkService для [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] . Учетная запись NetworkService запускает каждый экземпляр SMP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на управляющем узле и на вычислительных узлах. Например, при выполнении операции резервного копирования управляющий узел и каждый узел вычислений будут использовать учетные данные учетной записи NetworkService для доступа к целевому серверу.  
  
## <a name="metadata"></a>Метаданные  
 Чтобы получить список всех учетных данных и убедиться, что учетные данные были удалены, используйте [инструкцию sys. dm_pdw_network_credentials &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-network-credentials-transact-sql.md).  
  
 Чтобы добавить учетные данные, используйте [sp_pdw_add_network_credentials &#40;хранилище данных SQL&#41;](../../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md).  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-remove-credentials-for-performing-a-database-backup"></a>А) Удаление учетных данных для выполнения резервного копирования базы данных  
 В следующем примере удаляются учетные данные имени пользователя и пароля для доступа к целевому серверу с IP-адресом 10.192.147.63.  
  
```  
EXEC sp_pdw_remove_network_credentials '10.192.147.63';  
```  
  
  

