---
title: "sp_syscollector_update_collector_type (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_syscollector_update_collector_type_TSQL
- sp_syscollector_update_collector_type
dev_langs: TSQL
helpviewer_keywords:
- sp_syscollector_update_collector_type
- data collector [SQL Server], stored procedures
ms.assetid: 3c414dfd-d9ca-4320-81aa-949465b967bf
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4e8f2dbc3024ee7349774c1bccd10d75c0bfffb7
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="spsyscollectorupdatecollectortype-transact-sql"></a>sp_syscollector_update_collector_type (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Обновляет тип сборщика для элемента сбора. Обновляет по заданному имени и идентификатору GUID конфигурацию типа сборщика, включая пакет сбора и передачи, схему параметров и схему модуля форматирования параметров.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_syscollector_update_collector_type [ @collector_type_uid = ] 'collector_type_uid' OUTPUT  
          , [ @name = ] 'name'  
          , [ @parameter_schema = ] 'parameter_schema'  
          , [ @collection_package_id = ] collection_package_id  
          , [ @upload_package_id = ] upload_package_id  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@collector_type_uid =** ] **"***аргумент collector_type_uid***"**  
 Идентификатор GUID типа сборщика. *Аргумент collector_type_uid* — **uniqueidentifier**, и если оно равно NULL, он будет автоматически создается и возвращается как OUTPUT.  
  
 [  **@name =** ] **"***имя***"**  
 Имя типа сборщика. *имя* — **sysname** и должен быть указан.  
  
 [  **@parameter_schema =** ] **"***parameter_schema***"**  
 Схема XML для этого типа сборщика. *parameter_schema* — **xml** и может требоваться определенными типами сборщика. Если этот аргумент не задан, он может принимать значение NULL.  
  
 [  **@collection_package_id =** ] *collection_package_id*  
 Локальный уникальный идентификатор, указывающий на пакет сбора [!INCLUDE[ssIS](../../includes/ssis-md.md)], используемый в данном наборе элементов сбора. *collection_package_id* — **uniqueidentifer** и является обязательным. Для получения значения для *collection_package_id*, запросите системное представление dbo.syscollector_collector_types в базе данных msdb.  
  
 [  **@upload_package_id =** ] *upload_package_id*  
 Локальный уникальный идентификатор, указывающий на пакет передачи [!INCLUDE[ssIS](../../includes/ssis-md.md)], используемый в данном наборе элементов сбора. *upload_package_id* — **uniqueidentifier** и является обязательным. Для получения значения для *upload_package_id*, запросите системное представление dbo.syscollector_collector_types в базе данных msdb.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="permissions"></a>Permissions  
 Требуется членство в **dc_admin** (с разрешением EXECUTE) предопределенной роли базы данных.  
  
## <a name="example"></a>Пример  
 В этом примере обновляется тип сборщика «Универсальный запрос T-SQL». (В примере используется схема по умолчанию для типа сборщика «Универсальный запрос T-SQL».)  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_update_collector_type  
@collector_type_uid = '302E93D1-3424-4BE7-AA8E-84813ECF2419',  
@name = 'Generic T-SQL Query Collector Type',  
@parameter_schema = '<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="DataCollectorType">  
  <xs:element name="TSQLQueryCollector">  
<xs:complexType>  
  <xs:sequence>  
<xs:element name="Query" minOccurs="1" maxOccurs="unbounded">  
  <xs:complexType>  
<xs:sequence>  
  <xs:element name="Value" type="xs:string" />  
  <xs:element name="OutputTable" type="xs:string" />  
</xs:sequence>  
  </xs:complexType>  
</xs:element>  
<xs:element name="Databases" minOccurs="0" maxOccurs="1">  
  <xs:complexType>  
<xs:sequence>  
  <xs:element name="Database" minOccurs="0" maxOccurs="unbounded" type="xs:string" />  
</xs:sequence>  
<xs:attribute name="UseSystemDatabases" type="xs:boolean" use="optional" />  
<xs:attribute name="UseUserDatabases" type="xs:boolean" use="optional" />  
  </xs:complexType>  
</xs:element>  
  </xs:sequence>  
</xs:complexType>  
  </xs:element>  
</xs:schema>',  
@collection_package_id = '292B1476-0F46-4490-A9B7-6DB724DE3C0B',  
@upload_package_id = '6EB73801-39CF-489C-B682-497350C939F0';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Сбор данных](../../relational-databases/data-collection/data-collection.md)  
  
  
