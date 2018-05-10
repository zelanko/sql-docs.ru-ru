---
title: Объекты OLE-автоматизации (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-ole
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- triggers [SQL Server], OLE Automation
- batches [SQL Server], OLE Automation
- OLE Automation [SQL Server]
- OLE Automation [SQL Server], about OLE Automation
ms.assetid: a887d956-4cd0-400a-aa96-00d7abd7c44b
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 3cf6cfa987f1022107679c79206d9714b0fd9985
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="ole-automation-objects-in-transact-sql"></a>Объекты OLE-автоматизации в Transact-SQL
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  [!INCLUDE[tsql](../../includes/tsql-md.md)] включен ряд системных хранимых процедур, позволяющих ссылаться на объекты OLE-автоматизации из пакетов [!INCLUDE[tsql](../../includes/tsql-md.md)] , хранимых процедур и триггеров. Они выполняются как расширенные хранимые процедуры, при этом объекты OLE-автоматизации, запускаемые посредством хранимых процедур, работают в адресном пространстве экземпляра [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] аналогично расширенным хранимым процедурам.  
  
 Хранимые процедуры OLE-автоматизации позволяют пакетам [!INCLUDE[tsql](../../includes/tsql-md.md)] ссылаться на объекты SQL-DMO и пользовательские объекты OLE-автоматизации, например на объекты, реализующие интерфейс **IDispatch** . Пользовательский внутрипроцессный OLE-сервер, созданный в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] , должен иметь обработчик ошибок (определяемый по инструкции **On Error GoTo** ) для подпрограмм **Class_Initialize** и **Class_Terminate** . Все исключения, не обработанные в подпрограммах **Class_Initialize** и **Class_Terminate** , могут привести к непредвиденным ошибкам, в том числе вызвать нарушение общей защиты экземпляра компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Рекомендуется создавать обработчики ошибок и для остальных подпрограмм.  
  
 При обращении к объекту OLE-автоматизации из [!INCLUDE[tsql](../../includes/tsql-md.md)] сперва необходимо вызвать системную хранимую процедуру **sp_OACreate** , которая создает экземпляр объекта в адресном пространстве экземпляра компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 После создания экземпляра объекта можно вызывать следующие хранимые процедуры для работы со свойствами, методами и получением сведений об ошибках, связанных с созданным объектом.  
  
-   **sp_OAGetProperty** возвращает значение свойства.  
  
-   **sp_OASetProperty** устанавливает значение свойства.  
  
-   **sp_OAMethod** вызывает метод.  
  
-   **sp_OAGetErrorInfo** возвращает сведения о последней возникшей ошибке.  
  
 Когда объект больше не нужен, вызов хранимой процедуры **sp_OADestroy** позволяет освободить память, удалив объект, созданный хранимой процедурой **sp_OACreate**.  
  
 Объекты OLE-автоматизации возвращают данные в качестве значений свойств и методов. **sp_OAGetProperty** и **sp_OAMethod** возвращают эти значения данных в форме результирующего набора.  
  
 Областью видимости объекта OLE-автоматизации является пакет. Все ссылки на объект должны находиться в одном пакете, хранимой процедуре или триггере.  
  
 Объект OLE-автоматизации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по переданной ссылке позволяет производить доступ к другим содержащимся в нем объектам. Например, если используется объект SQL-DMO **SQLServer** , возможна передача ссылок на базы данных и таблицы, содержащиеся на этом сервере.  
  
## <a name="related-content"></a>См. также  
 [Синтаксис иерархии объектов (Transact-SQL)](../../relational-databases/system-stored-procedures/object-hierarchy-syntax-transact-sql.md)  
  
 [Настройка контактной зоны](../../relational-databases/security/surface-area-configuration.md)  
  
 [Параметр конфигурации сервера «Ole Automation Procedures»](../../database-engine/configure-windows/ole-automation-procedures-server-configuration-option.md)  
  
 [sp_OACreate (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-oacreate-transact-sql.md)  
  
 [sp_OAGetProperty (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-oagetproperty-transact-sql.md)  
  
 [sp_OASetProperty (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-oasetproperty-transact-sql.md)  
  
 [sp_OAMethod (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-oamethod-transact-sql.md)  
  
 [sp_OAGetErrorInfo (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-oageterrorinfo-transact-sql.md)  
  
 [sp_OADestroy (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-oadestroy-transact-sql.md)  
  
  
