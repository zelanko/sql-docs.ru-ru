---
title: "SUSER_SID (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SUSER_SID
- SUSER_SID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- logins [SQL Server], users
- SIDs [SQL Server]
- security identifiers [SQL Server]
- users [SQL Server], logins
- 15401 (Database Engine error)
- IDs [SQL Server], logins
- identification numbers [SQL Server], logins
- SUSER_SID function
ms.assetid: 57b42a74-94e1-4326-85f1-701b9de53c7d
caps.latest.revision: 31
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ab02d47027f970e05820bc377d72f60938b52b62
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="susersid-transact-sql"></a>SUSER_SID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает идентификатор безопасности (SID) для указанного имени входа.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SUSER_SID ( [ 'login' ] [ , Param2 ] )   
```  
  
## <a name="arguments"></a>Аргументы  
 **"** *входа* **"**  
**Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Имя входа пользователя. *Имя входа* — **sysname**. *Имя входа*, необязателен и может быть [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа или [!INCLUDE[msCoName](../../includes/msconame-md.md)] пользователя или группы Windows. Если *входа* — не указано, возвращаются сведения о текущем контексте безопасности. Если параметр содержит слово NULL, то возвращается NULL.  
  
 *Param2*  
**Применяется к**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Указывает, проверено ли имя входа. *Param2* относится к типу **int** и является необязательным. Когда *Param2* равно 0, то имя входа является недопустимым. Когда *Param2* не равен 0, имя входа Windows проверяется быть в точности совпадает с именем входа, хранящиеся в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **varbinary(85)**  
  
## <a name="remarks"></a>Замечания  
 Функция SUSER_SID может использоваться в качестве ограничения DEFAULT в инструкциях ALTER TABLE и CREATE TABLE. Функцию SUSER_SID можно использовать в списке выбора, в предложении WHERE, а также в любом месте, где разрешено использование выражений. После функции SUSER_SID всегда должны следовать скобки, даже если не задано ни одного параметра.  
  
 Если функция SUSER_SID вызывается без аргументов, она возвращает идентификатор SID текущего контекста безопасности. Если функция SUSER_SID вызывается без аргументов в пакете, в котором был переключен контекст с помощью инструкции EXECUTE AS, функция возвращает идентификатор SID олицетворенного контекста. При вызове из олицетворенного контекста функция SUSER_SID(ORIGINAL_LOGIN()) возвращает SID оригинального контекста.  
  
 Если параметры сортировки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и Windows не совпадают, функция SUSER_SID может завершиться, если имя входа в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и Windows хранятся в разных форматах. Например, если на компьютере Windows «TestComputer» есть пользователь «User», а в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] это имя входа хранится как «TESTCOMPUTER\User», то при разрешении имя входа «TestComputer\User» может быть не обнаружено. Чтобы пропустить данную проверку имени входа, используйте *Param2*. Разные параметры сортировки часто вызывают ошибку 15401 в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
 `Windows NT user or group '%s' not found. Check the name again.`  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-susersid"></a>A. Использование SUSER_SID  
 Следующий пример возвращает идентификатор безопасности (SID) для текущего контекста безопасности.  
  
```  
SELECT SUSER_SID('sa');  
```  
  
### <a name="b-using-susersid-with-a-specific-login"></a>Б. Использование SUSER_SID с определенным именем входа  
 В следующем примере возвращается идентификационный номер безопасности для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `sa` входа.  
  
**Применяется к**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
```  
SELECT SUSER_SID('sa');  
GO  
```  
  
### <a name="c-using-susersid-with-a-windows-user-name"></a>В. Использование SUSER_SID с именем пользователя Windows  
 В следующем примере возвращается идентификационный номер безопасности для пользователя Windows `London\Workstation1`.  
  
**Применяется к**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
```  
SELECT SUSER_SID('London\Workstation1');  
GO  
```  
  
### <a name="d-using-susersid-as-a-default-constraint"></a>Г. Использование SUSER_SID в качестве ограничения DEFAULT  
 В следующем примере функция `SUSER_SID` используется в качестве ограничения `DEFAULT` в инструкции `CREATE TABLE`.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE sid_example  
(  
login_sid   varbinary(85) DEFAULT SUSER_SID(),  
login_name  varchar(30) DEFAULT SYSTEM_USER,  
login_dept  varchar(10) DEFAULT 'SALES',  
login_date  datetime DEFAULT GETDATE()  
);   
GO  
INSERT sid_example DEFAULT VALUES;  
GO  
```  
  
### <a name="e-comparing-the-windows-login-name-to-the-login-name-stored-in-sql-server"></a>Д. Сравнение имени входа Windows с именем входа, сохраненным в SQL Server  
 В следующем примере показано, как использовать *Param2* получить SID из Windows и использует в качестве входных данных для этого идентификатора `SUSER_SNAME` функции. В этом примере имя входа указывается в формате, в котором оно хранится в Windows (`TestComputer\User`), а возвращается в формате, в котором оно хранится в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (`TESTCOMPUTER\User`).  
  
**Применяется к**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
```  
SELECT SUSER_SNAME(SUSER_SID('TestComputer\User', 0));  
```  
  
## <a name="see-also"></a>См. также:  
 [Функция ORIGINAL_LOGIN &#40; Transact-SQL &#41;](../../t-sql/functions/original-login-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [Binary и varbinary &#40; Transact-SQL &#41;](../../t-sql/data-types/binary-and-varbinary-transact-sql.md)   
 [Системные функции &#40; Transact-SQL &#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
  
  

