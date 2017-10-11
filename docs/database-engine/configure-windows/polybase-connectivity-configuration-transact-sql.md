---
title: "Конфигурация подключения к PolyBase (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PolyBase
ms.assetid: 82252e4f-b1d0-49e5-aa0b-3624aade2add
caps.latest.revision: 14
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 74f73ab33a010583b4747fcc2d9b35d6cdea14a2
ms.openlocfilehash: b57b1e802969995f87d5663e5e7dbdc92700a9b5
ms.contentlocale: ru-ru
ms.lasthandoff: 08/04/2017

---
# <a name="polybase-connectivity-configuration-transact-sql"></a>Конфигурация подключения к PolyBase (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-pdw_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-pdw-md.md)]

  Отображает или изменяет глобальные параметры конфигурации для подключения к PolyBase Hadoop и хранилищу BLOB-объектов Azure.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
--List all of the configuration options  
sp_configure  
[;]  
  
--Configure Hadoop connectivity  
sp_configure [ @configname = ] 'hadoop connectivity',  
             [ @configvalue = ] { 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 }  
[;]  
  
RECONFIGURE  
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@configname=** ] **"***имя_параметра***"**  
 Имя параметра конфигурации. Аргумент*option_name* имеет тип **varchar(35)**, значение по умолчанию — NULL. Если этот параметр отсутствует, возвращается список всех параметров.  
  
 [ **@configvalue=** ] **"***значение***"**  
 Новое значение параметра конфигурации. Аргумент*value* имеет тип **int**и значение по умолчанию NULL. Максимальное значение зависит от конкретного параметра.  
  
 **'hadoop connectivity'**  
 Указывает тип источника данных Hadoop для всех подключений из PolyBase к кластерам Hadoop или хранилищу BLOB-объектов Azure (WASB). Этот параметр необходим для создания внешнего источника данных для внешней таблицы. Дополнительные сведения см. в разделе [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md),  
  
 Ниже приведены параметры подключения к Hadoop и соответствующие поддерживаемые источники данных Hadoop. Одновременно может действовать только один параметр. Параметры 1, 4 и 7 позволяют создать несколько типов внешних источников данных и использовать их во всех сеансах на сервере.  
  
-   Параметр 0. Отключить подключение Hadoop  
  
-   Параметр 1. Hortonworks HDP 1.3 в Windows Server  
  
-   Параметр 1. Хранилище BLOB-объектов Azure (WASB[S])  
  
-   Параметр 2. Hortonworks HDP 1.3 в Linux  
  
-   Параметр 3. Cloudera CDH 4.3 в Linux  
  
-   Параметр 4. Hortonworks HDP 2.0 в Windows Server  
  
-   Параметр 4. Хранилище BLOB-объектов Azure (WASB[S])  
  
-   Параметр 5. Hortonworks HDP 2.0 в Linux  
  
-   Параметр 6. Cloudera 5.1, 5.2, 5.3, 5.4, 5.5, 5.9, 5.10, 5.11 и 5.12 в Linux  
  
-   Параметр 7. Hortonworks 2.1, 2.2, 2.3, 2.4, 2.5 и 2.6 в Linux  
  
-   Параметр 7. Hortonworks 2.1, 2.2 и 2.3 в Windows Server  
  
-   Параметр 7. Хранилище BLOB-объектов Azure (WASB[S])  
  
 **RECONFIGURE**  
 Обновляет рабочее значение (run_value) в соответствии со значением конфигурации (config_value). См. определения параметров run_value и config_value в разделе [Наборы результатов](#ResultSets) . Новое значение конфигурации, которое задается параметром sp_configure, не вступит в силу до тех пор, пока инструкция RECONFIGURE не задаст рабочее значение.  
  
 После выполнения инструкции RECONFIGURE необходимо остановить и перезапустить службу SQL Server. Обратите внимание, что при остановке службы SQL Server автоматически останавливаются две дополнительные службы — PolyBase Engine и служба перемещения данных. После перезапуска службы ядра SQL Server запустите эти две службы заново (они не запускаются автоматически).  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
##  <a name="ResultSets"></a> Наборы результатов  
 При выполнении без параметров **sp_configure** возвращает результирующий набор с пятью столбцами.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**name**|**nvarchar(35)**|Имя параметра конфигурации.|  
|**minimum**|**int**|Минимальное значение параметра конфигурации.|  
|**maximum**|**int**|Максимальное значение параметра конфигурации.|  
|**config_value**|**int**|Значение, которое было задано с помощью **sp_configure**.|  
|**run_value**|**int**|Текущее значение, используемое PolyBase. Это значение можно задать, выполнив инструкцию RECONFIGURE.<br /><br /> Значения **config_value** и **run_value** , как правило, совпадают, если не находятся в процессе изменения.<br /><br /> Если выполняется перенастройка, может потребоваться перезагрузка, чтобы это рабочее значение стало точным.|  
  
## <a name="general-remarks"></a>Общие замечания  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]после выполнения инструкции RECONFIGURE для вступления в силу рабочего значения 'hadoop connectivity' необходимо перезапустить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
В [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]после выполнения инструкции RECONFIGURE для вступления в силу рабочего значения 'hadoop connectivity' необходимо перезапустить область [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] .  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
 Недопустимо использование RECONFIGURE в явной или неявной транзакции.  
  
## <a name="permissions"></a>Permissions  
 Все пользователи могут выполнять команду **sp_configure** без параметров или с параметром @configname .  
  
 Для изменения значения конфигурации или выполнения инструкции RECONFIGURE требуется разрешение **ALTER SETTINGS** на уровне сервера или членство в предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-list-all-available-configuration-settings"></a>A. Список всех доступных параметров конфигурации.  
 В следующем примере демонстрируется, как создать список всех параметров конфигурации.  
  
```  
EXEC sp_configure;  
```  
  
 В результате возвращается имя параметра, за которым следуют его минимальное и максимальное значения. **config_value** — это значение, которое будет использовать SQL или PolyBase после завершения перенастройки. **run_value** — это значение, которое используется в настоящий момент. Значения **config_value** и **run_value** , как правило, совпадают, если не находятся в процессе изменения.  
  
### <a name="b-list-the-configuration-settings-for-one-configuration-name"></a>Б. Список параметров конфигурации для одного имени конфигурации.  
  
```  
EXEC sp_configure @configname='hadoop connectivity';  
```  
  
### <a name="c-set-hadoop-connectivity"></a>В. Установка подключения к Hadoop.  
 В этом примере для PolyBase задается параметр 7. Этот параметр позволяет PolyBase создавать и использовать внешние таблицы в Hortonworks 2.1, 2.2 и 2.3 в Linux и Windows Server, а также в хранилище BLOB-объектов Azure. Например, SQL может содержать 30 внешних таблиц, 7 из которых будут ссылаться на данные в Hortonworks 2.1 в Linux, 4 — в Hortonworks 2.2 в Linux, 7 — в Hortonworks 2.3 в Linux и еще 12 — в хранилище BLOB-объектов Azure.  
  
```  
--Configure external tables to reference data on Hortonworks 2.1, 2.2, and 2.3 on Linux, and Azure blob storage  
  
sp_configure @configname = 'hadoop connectivity', @configvalue = 7;  
GO  
  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [CREATE EXTERNAL TABLE (Transact-SQL)](../../t-sql/statements/create-external-table-transact-sql.md)   
 [CREATE EXTERNAL FILE FORMAT (Transact-SQL)](../../t-sql/statements/create-external-file-format-transact-sql.md)   
 [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md)  
  
  

