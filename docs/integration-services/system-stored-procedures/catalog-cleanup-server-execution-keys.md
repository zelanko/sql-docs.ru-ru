---
title: "Catalog.cleanup_server_execution_keys | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a79f1006-54e8-4cbf-96f8-5ed143ebb830
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 172925d5a63aa831881b6a6325f0dbcbccd4dd56
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="catalogcleanupserverexecutionkeys"></a>Catalog.cleanup_server_execution_keys
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Удаляет сертификаты и симметричные ключи из базы данных SSISDB.  
  
## <a name="syntax"></a>Синтаксис  
  
```sql
catalog.cleanup_server_execution_keys [ @cleanup_flag = ] cleanup_flag ,  
[ @delete_batch_size = ] delete_batch_size  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @cleanup_flag =] *cleanup_flag*  
 Указывает, включена ли уровень выполнения (1) или проекта на уровне (2) сертификаты и симметричные ключи для удаления.  
  
 Уровень выполнения (1) следует используйте только в том случае, если PER_EXECUTION (1) присвоено SERVER_OPERATION_ENCRYPTION_LEVEL.  
  
 Используйте уровня проекта (2) только в том случае, когда SERVER_OPERATION_ENCRYPTION_LEVEL имеет значение PER_PROJECT (2). Сертификаты и симметричные ключи удаляются только для проектов, которые были удалены и для которых были очищены журналы операций.  
  
 [ @delete_batch_size =] *delete_batch_size*  
 Число ключей и сертификатов для удаления. Значение по умолчанию — 1000.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 для успеха и 1 для ошибки.  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет.  
  
## <a name="permissions"></a>Permissions  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения READ и EXECUTE на проект и, если это применимо, разрешения на чтение на указанную среду.  
  
-   Членство в **ssis_admin** роли базы данных.  
  
-   Членство в **sysadmin** роли сервера.  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 Эта хранимая процедура вызывает ошибки в следующих сценариях:  
  
-   Существует одна или несколько активных операций в базе данных SSISDB.  
  
-   База данных SSISDB не находится в режиме одного пользователя.  
  
## <a name="remarks"></a>Замечания  
 Пакет обновления 2 для SQL Server 2012 добавлены свойства SERVER_OPERATION_ENCRYPTION_LEVEL **internal.catalog_properties** таблицы. Это свойство имеет два возможных значения:  
  
-   **(1) PER_EXECUTION** — сертификат и симметричный ключ, используемый для защиты конфиденциальных выполнения параметры и журналы выполнения создаются для каждого выполнения. Это значение по умолчанию. Возможно возникновение проблем с производительностью (взаимоблокировки, сбой обслуживания заданий и т. д) в рабочей среде, потому что сертификат и ключи создаются для каждого выполнения. Тем не менее этот параметр обеспечивает более высокий уровень безопасности, чем другое значение (2).  
  
-   **(2) PER_PROJECT** — сертификат и симметричный ключ, используемый для защиты конфиденциальных параметров создаются для каждого проекта. Это обеспечивает лучшую производительность, чем уровень PER_EXECUTION так как ключ и сертификат формируется один раз для проекта, а не при каждом выполнении.  
  
 Необходимо запустить [catalog.cleanup_server_log](../../integration-services/system-stored-procedures/catalog-cleanup-server-log.md) хранимой процедуры перед изменением SERVER_OPERATION_ENCRYPTION_LEVEL от 1 до 2 (или) от 2 до 1. Перед выполнением данной хранимой процедуры, выполните следующие действия:  
  
1.  Убедитесь, что значение свойства OPERATION_CLEANUP_ENABLED имеет значение TRUE в [catalog.catalog_properties &#40; База данных SSISDB &#41; ](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md) таблицы.  
  
2.  Задайте для базы данных служб Integration Services (SSISDB) однопользовательский режим. В SQL Server Management Studio запустить диалоговое окно «Свойства базы данных» для SSISDB, перейдите на вкладку Параметры и установить свойство ограничение доступа в однопользовательский режим (SINGLE_USER). После запуска cleanup_server_log хранимой процедуры, задать значение свойства обратно в исходное значение.  
  
3.  Запустите хранимую процедуру [catalog.cleanup_server_log](../../integration-services/system-stored-procedures/catalog-cleanup-server-log.md).  
  
4.  Теперь, загрузив и измените значение свойства SERVER_OPERATION_ENCRYPTION_LEVEL в [catalog.catalog_properties &#40; База данных SSISDB &#41; ](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md) таблицы.  
  
5.  Запустите хранимую процедуру [catalog.cleanup_server_execution_keys](../../integration-services/system-stored-procedures/catalog-cleanup-server-execution-keys.md) для очистки ключей сертификатов из базы данных SSISDB. Удаление сертификаты и ключи из базы данных SSISDB может занять длительное время, поэтому он должен быть запущен периодически во время пониженной нагрузки.  
  
     Можно указать область или уровне (выполнение и проекта) и количество ключей для удаления. Размер пакета для удаления по умолчанию — 1000. При установке уровня 2, ключи и сертификаты удаляются только в том случае, если связанные проекты были удалены.  
  
 Дополнительные сведения см. в следующей статье базы знаний. [Исправление: Проблемы с производительностью при развертывании с помощью SSISDB хранения в SQL Server 2012](http://support.microsoft.com/kb/2972285)  
  
## <a name="example"></a>Пример  
 В следующем примере вызывается cleanup_server_execution_keys хранимой процедуры.  
  
```sql  
USE [SSISDB]  
GO  
  
DECLARE@return_value int  
  
EXEC@return_value = [internal].[cleanup_server_execution_keys]  
@cleanup_flag = 1,  
@delete_batch_size = 500  
  
SELECT'Return Value' = @return_value  
  
GO  
```  
  
  

