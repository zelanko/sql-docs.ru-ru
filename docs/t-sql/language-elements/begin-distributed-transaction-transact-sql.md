---
title: "НАЧАТЬ РАСПРЕДЕЛЕННЫХ ТРАНЗАКЦИЙ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 11/29/2016
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DISTRIBUTED
- BEGIN_DISTRIBUTED_TRANSACTION_TSQL
- DISTRIBUTED_TSQL
- BEGIN DISTRIBUTED TRANSACTION
dev_langs:
- TSQL
helpviewer_keywords:
- BEGIN DISTRIBUTED TRANSACTION statement
- distributed transactions [SQL Server], starting
- MS DTC, transaction management
- distributed transactions [SQL Server], BEGIN DISTRIBUTED TRANSACTION statement
- servers [SQL Server], distributed transactions
- starting distributed transactions
- remote servers [SQL Server], distributed transactions
- starting transactions
ms.assetid: c3bc2716-39d3-4061-8c6a-8734899231ac
caps.latest.revision: 36
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 93287230933c8ad33bc72185b2b26402ef8048fa
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="begin-distributed-transaction-transact-sql"></a>BEGIN DISTRIBUTED TRANSACTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Запускает распределенную транзакцию на языке [!INCLUDE[tsql](../../includes/tsql-md.md)], управляемую координатором распределенных транзакций [!INCLUDE[msCoName](../../includes/msconame-md.md)] (MS DTC).  
    
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
BEGIN DISTRIBUTED { TRAN | TRANSACTION }   
     [ transaction_name | @tran_name_variable ]   
[ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *transaction_name*  
 Имя определяемой пользователем транзакции, используемое для отслеживания распределенной транзакции в программах MS DTC. *transaction_name* должно соответствовать правилам для идентификаторов и должно быть \<= 32 символов.  
  
 @*tran_name_variable*  
 Имя пользовательской переменной, содержащей имя транзакции, которая используется для отслеживания распределенной транзакции в служебных программах координатора MS DTC. Переменная должна быть объявлена с **char**, **varchar**, **nchar**, или **nvarchar** тип данных.  
  
## <a name="remarks"></a>Замечания  
 Экземпляр компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], на котором выполняется инструкция BEGIN DISTRIBUTED TRANSACTION, является инициатором транзакции, контролирующим ее завершение. Если после этого в сеансе выполняется инструкция COMMIT TRANSACTION или ROLLBACK TRANSACTION, управляющий экземпляр передает координатору MS DTC управление распределенной транзакцией во всех экземплярах.  
  
 Изоляция моментального снимка уровня транзакции не поддерживает распределенные транзакции.  
  
 Основным способом прикрепления удаленных экземпляров компонентов [!INCLUDE[ssDE](../../includes/ssde-md.md)] к распределенной транзакции является выполнение распределенного запроса, ссылающегося на связанный сервер, в сеансе, который уже прикреплен к распределенной транзакции.  
  
 Например, если инструкция BEGIN DISTRIBUTED TRANSACTION выполняется на сервере А, сеанс вызывает хранимую процедуру на сервере Б и еще одну хранимую процедуру на сервере В. Хранимая процедура на сервере В выполняет распределенный запрос к серверу Г, и в результате в распределенную транзакцию включаются все четыре сервера. Экземпляр компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] на сервере А является автором транзакции и управляет ею.  
  
 Сеансы, вовлеченные в распределенную транзакцию на языке [!INCLUDE[tsql](../../includes/tsql-md.md)], не получают объект транзакции, который они могли бы передать другому сеансу, чтобы явным образом прикрепить его к распределенной транзакции. Единственный способ, при помощи которого удаленный сервер можно прикрепить к распределенной транзакции, — это представить его в качестве целевого сервера для распределенного запроса или вызова удаленной хранимой процедуры.  
  
 При в локальной транзакции выполняется распределенный запрос, транзакция автоматически повышается до распределенной транзакции, если целевой источник данных OLE DB поддерживает интерфейс ITransactionLocal. Если целевой источник данных OLE DB поддерживает интерфейс ITransactionLocal, операции только для чтения разрешены в распределенном запросе.  
  
 Сеанс, уже прикрепленный к распределенной транзакции, выполняет удаленную хранимую процедуру, ссылаясь на удаленный сервер.  
  
 **Удаленного proc trans хранимой процедуры sp_configure** параметр элементов управления, является ли вызовы удаленных хранимых процедур в локальной транзакции автоматически вызывают локальной транзакции повышаться до распределенной транзакции, управляемой координатором MS DTC. Параметр SET уровня соединения REMOTE_PROC_TRANSACTIONS может использоваться для переопределения экземпляр по умолчанию, заданные в **удаленного proc trans хранимой процедуры sp_configure**. Если этот параметр включен, вызов удаленной хранимой процедуры приводит к повышению уровня локальной транзакции до распределенной транзакции. Соединение, создающее транзакцию координатора MS DTC, становится инициатором этой транзакции. Инструкция COMMIT TRANSACTION фиксирует транзакцию, управляемую координатором MS DTC. Если **удаленного proc trans хранимой процедуры sp_configure** имеет значение ON, вызовы удаленных хранимых процедур в локальной транзакции автоматически защищаются как часть распределенной транзакции не требуется переписывать приложения, в частности проблему BEGIN DISTRIBUTED TRANSACTION вместо BEGIN TRANSACTION.  
  
 Дополнительные сведения о процессе и среды распределенных транзакций см. в разделе [!INCLUDE[msCoName](../../includes/msconame-md.md)] документации координатора распределенных транзакций.  
  
## <a name="permissions"></a>Permissions  
 Требуется членство в роли public.  
  
## <a name="examples"></a>Примеры  
 В этом примере удаляется кандидат из базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] как на локальном экземпляре компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)], так и на удаленном сервере. И локальная, и удаленная база данных зафиксирует транзакцию или выполнит ее откат.  
  
> [!NOTE]  
>  Этот пример приводит к сообщению об ошибке, если координатор MS DTC не установлен на компьютере, где выполняется экземпляр компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Дополнительные сведения об установке координатора MS DTC см. в документации по координатору распределенных транзакций Microsoft.  
  
```  
USE AdventureWorks2012;  
GO  
BEGIN DISTRIBUTED TRANSACTION;  
-- Delete candidate from local instance.  
DELETE AdventureWorks2012.HumanResources.JobCandidate  
    WHERE JobCandidateID = 13;  
-- Delete candidate from remote instance.  
DELETE RemoteServer.AdventureWorks2012.HumanResources.JobCandidate  
    WHERE JobCandidateID = 13;  
COMMIT TRANSACTION;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [BEGIN TRANSACTION (Transact-SQL)](../../t-sql/language-elements/begin-transaction-transact-sql.md)   
 [COMMIT TRANSACTION (Transact-SQL)](../../t-sql/language-elements/commit-transaction-transact-sql.md)   
 [ФИКСАЦИЯ РАБОЧЕГО &#40; Transact-SQL &#41;](../../t-sql/language-elements/commit-work-transact-sql.md)   
 [ROLLBACK TRANSACTION (Transact-SQL)](../../t-sql/language-elements/rollback-transaction-transact-sql.md)   
 [ROLLBACK WORK &#40; Transact-SQL &#41;](../../t-sql/language-elements/rollback-work-transact-sql.md)   
 [SAVE TRANSACTION (Transact-SQL)](../../t-sql/language-elements/save-transaction-transact-sql.md)  
  
  

