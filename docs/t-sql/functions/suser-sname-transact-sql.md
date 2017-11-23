---
title: "SUSER_SNAME (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/29/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SUSER_SNAME_TSQL
- SUSER_SNAME
dev_langs: TSQL
helpviewer_keywords:
- security identification names [SQL Server]
- logins [SQL Server], users
- SIDs [SQL Server]
- SUSER_SNAME function
- users [SQL Server], logins
- logins [SQL Server], names
- IDs [SQL Server], logins
- identification numbers [SQL Server], logins
- names [SQL Server], logins
ms.assetid: 11ec7d86-d429-4004-a436-da25df9f8761
caps.latest.revision: "24"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 177c7802c3a9c7ca7fadbb279c0be35fd57af820
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="susersname-transact-sql"></a>SUSER_SNAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает имя входа, связанное с идентификатором безопасности (SID).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
SUSER_SNAME ( [ server_user_sid ] )   
```  
  
## <a name="arguments"></a>Аргументы  
 *server_user_sid*  
**Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Необязательный номер идентификатора безопасности имени входа. *server_user_sid* — **varbinary(85)**. *server_user_sid* может быть номером идентификатора безопасности любого [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа или [!INCLUDE[msCoName](../../includes/msconame-md.md)] пользователя или группы Windows. Если *server_user_sid* — не указано, возвращаются сведения о текущем пользователе. Если параметр содержит слово NULL, то возвращается NULL.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **nvarchar(128)**  
  
## <a name="remarks"></a>Замечания  
 Функция SUSER_SNAME может применяться как ограничение DEFAULT в инструкциях ALTER TABLE и CREATE TABLE. Функция SUSER_SNAME может применяться в списке выбора, в предложении WHERE и в выражении, где это допустимо. За функцией SUSER_SNAME всегда должны следовать круглые скобки, даже если не указано никаких параметров.  
  
 При вызове без аргумента функция SUSER_SNAME возвращает название текущего контекста безопасности. При вызове без аргумента в пределах пакета, который переключил контекст с помощью EXECUTE AS, функция SUSER_SNAME возвращает название олицетворенного контекста. При вызове из олицетворенного контекста функция ORIGINAL_LOGIN возвращает название оригинального контекста.  
  
## <a name="includesssdsfullincludessssdsfull-mdmd-remarks"></a>[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. Замечания  
 SUSER_NAME всегда возвращает имя входа для текущего контекста безопасности.  
  
 Инструкция SUSER_SNAME не поддерживает выполнение с помощью олицетворенного контекста безопасности посредством инструкции EXECUTE AS.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-susersname"></a>A. Использование параметра SUSER_SNAME  
 В следующем примере возвращается имя входа для текущего контекста безопасности.  
  
```  
SELECT SUSER_SNAME();  
GO  
```  
  
### <a name="b-using-susersname-with-a-windows-user-security-id"></a>Б. Использование параметра SUSER_SNAME с идентификатором безопасности пользователя Windows  
 Следующий пример возвращает имя входа, связанное с номером идентификатора безопасности Windows.  
  
**Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
```  
SELECT SUSER_SNAME(0x010500000000000515000000a065cf7e784b9b5fe77c87705a2e0000);  
GO  
```  
  
### <a name="c-using-susersname-as-a-default-constraint"></a>В. Использование параметра SUSER_SNAME в качестве ограничения DEFAULT  
 В следующем примере функция `SUSER_SNAME` используется в качестве ограничения `DEFAULT` в инструкции `CREATE TABLE`.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE sname_example  
(  
login_sname sysname DEFAULT SUSER_SNAME(),  
employee_id uniqueidentifier DEFAULT NEWID(),  
login_date  datetime DEFAULT GETDATE()  
);   
GO  
INSERT sname_example DEFAULT VALUES;  
GO  
```  
  
### <a name="d-calling-susersname-in-combination-with-execute-as"></a>Г. Вызов функции SUSER_SNAME в сочетании с EXECUTE AS  
 Этот пример показывает поведение функции SUSER_SNAME при вызове из олицетворенного контекста.  
  
**Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
```  
SELECT SUSER_SNAME();  
GO  
EXECUTE AS LOGIN = 'WanidaBenShoof';  
SELECT SUSER_SNAME();  
REVERT;  
GO  
SELECT SUSER_SNAME();  
GO  
  
```  
  
 Ниже приводится результат.  
  
 ```
sa  
WanidaBenShoof  
sa
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="e-using-susersname"></a>Д. Использование параметра SUSER_SNAME  
 Следующий пример возвращает имя входа для номера идентификатора безопасности со значением `0x01`.  
  
```  
SELECT SUSER_SNAME(0x01);  
GO  
```  
  
### <a name="f-returning-the-current-login"></a>Е. Возвращает текущее имя входа  
 Следующий пример возвращает имя входа текущего имени входа.  
  
```  
SELECT SUSER_SNAME() AS CurrentLogin;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Функция SUSER_SID &#40; Transact-SQL &#41;](../../t-sql/functions/suser-sid-transact-sql.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [sys.server_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [ВЫПОЛНЕНИЕ AS &#40; Transact-SQL &#41;](../../t-sql/statements/execute-as-transact-sql.md)  
  
  

