---
description: sp_syscollector_update_collector_type (Transact-SQL)
title: sp_syscollector_update_collector_type (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_update_collector_type_TSQL
- sp_syscollector_update_collector_type
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syscollector_update_collector_type
- data collector [SQL Server], stored procedures
ms.assetid: 3c414dfd-d9ca-4320-81aa-949465b967bf
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 175e3299c37afe307de8b5f809e44646d0a26047
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89534855"
---
# <a name="sp_syscollector_update_collector_type-transact-sql"></a>sp_syscollector_update_collector_type (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

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
`[ @collector_type_uid = ] 'collector_type_uid'` Идентификатор GUID для типа сборщика. *collector_type_uid* имеет тип **uniqueidentifier**, и, если он равен null, он будет автоматически создан и возвращен в качестве выходных данных.  
  
`[ @name = ] 'name'` Имя типа сборщика. Аргумент *Name* имеет тип **sysname** и должен быть указан.  
  
`[ @parameter_schema = ] 'parameter_schema'` XML-схема для этого типа сборщика. *parameter_schema* является **XML** и может потребоваться для некоторых типов сборщиков. Если этот аргумент не задан, он может принимать значение NULL.  
  
`[ @collection_package_id = ] collection_package_id` Локальный уникальный идентификатор, указывающий на [!INCLUDE[ssIS](../../includes/ssis-md.md)] пакет сбора, используемый набором сбора. *collection_package_id* является **уникуеидентифер** и является обязательным. Чтобы получить значение для *collection_package_id*, запросите системное представление dbo.syscollector_collector_types в базе данных msdb.  
  
`[ @upload_package_id = ] upload_package_id` Локальный уникальный идентификатор, указывающий на [!INCLUDE[ssIS](../../includes/ssis-md.md)] пакет отправки, используемый набором сбора. *upload_package_id* имеет тип **uniqueidentifier** и является обязательным. Чтобы получить значение для *upload_package_id*, запросите системное представление dbo.syscollector_collector_types в базе данных msdb.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в предопределенной роли базы данных **dc_admin** (с разрешением EXECUTE).  
  
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
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Сбор данных](../../relational-databases/data-collection/data-collection.md)  
  
  
