---
title: SUSER_SID (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 97043c1232dd3003ff5c7101403c53425d75bca5
ms.sourcegitcommit: f688a37bb6deac2e5b7730344165bbe2c57f9b9c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/08/2019
ms.locfileid: "73843590"
---
# <a name="suser_sid-transact-sql"></a>SUSER_SID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает идентификатор безопасности (SID) для указанного имени входа.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SUSER_SID ( [ 'login' ] [ , Param2 ] )   
```  
  
## <a name="arguments"></a>Аргументы  
 **'** *login* **'**  
**Применимо к**: с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Имя входа пользователя. Аргумент *login* имеет тип **sysname**. Аргумент *login* необязателен и может представлять собой имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] либо имя пользователя или группы в [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. Если аргумент *login* не задан, возвращаются сведения о текущем контексте безопасности. Если параметр содержит слово NULL, то возвращается NULL.  
  
 *Param2*  
**Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Указывает, проверено ли имя входа. Аргумент *Param2* имеет тип **int** и является необязательным. Если параметр *Param2* равен 0, то имя для входа не проверяется. Если параметр*Param2* не равен 0, то имя для входа Windows проверяется на обязательное соответствие имени для входа, сохраненному в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **varbinary(85)**  
  
## <a name="remarks"></a>Remarks  
 Функция SUSER_SID может использоваться в качестве ограничения DEFAULT в инструкциях ALTER TABLE и CREATE TABLE. Функцию SUSER_SID можно использовать в списке выбора, в предложении WHERE, а также в любом месте, где разрешено использование выражений. После функции SUSER_SID всегда должны следовать скобки, даже если не задано ни одного параметра.  
  
 Если функция SUSER_SID вызывается без аргументов, она возвращает идентификатор SID текущего контекста безопасности. Если функция SUSER_SID вызывается без аргументов в пакете, в котором был переключен контекст с помощью инструкции EXECUTE AS, функция возвращает идентификатор SID олицетворенного контекста. При вызове из олицетворенного контекста функция SUSER_SID(ORIGINAL_LOGIN()) возвращает SID оригинального контекста.  
  
 Если параметры сортировки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и Windows не совпадают, функция SUSER_SID может завершиться, если имя входа в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и Windows хранятся в разных форматах. Например, если на компьютере Windows «TestComputer» есть пользователь «User», а в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] это имя входа хранится как «TESTCOMPUTER\User», то при разрешении имя входа «TestComputer\User» может быть не обнаружено. Чтобы отключить проверку имени для входа, используйте параметр *Param2*. Разные параметры сортировки часто вызывают ошибку 15401 в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
 `Windows NT user or group '%s' not found. Check the name again.`  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-suser_sid"></a>A. Использование SUSER_SID  
 В приведенном ниже примере возвращается идентификатор безопасности (SID) для текущего контекста безопасности.  
  
```  
SELECT SUSER_SID();  
```  
  
### <a name="b-using-suser_sid-with-a-specific-login"></a>Б. Использование SUSER_SID с определенным именем входа  
 В приведенном ниже примере возвращается идентификатор безопасности для имени для входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `sa`.  
  
**Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
```  
SELECT SUSER_SID('sa');  
GO  
```  
  
### <a name="c-using-suser_sid-with-a-windows-user-name"></a>В. Использование SUSER_SID с именем пользователя Windows  
 В следующем примере возвращается идентификационный номер безопасности для пользователя Windows `London\Workstation1`.  
  
**Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
```  
SELECT SUSER_SID('London\Workstation1');  
GO  
```  
  
### <a name="d-using-suser_sid-as-a-default-constraint"></a>Г. Использование SUSER_SID в качестве ограничения DEFAULT  
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
 В приведенном ниже примере показано, как с помощью параметра *Param2* получить SID из Windows и передать его в функцию `SUSER_SNAME`. В этом примере имя входа указывается в формате, в котором оно хранится в Windows (`TestComputer\User`), а возвращается в формате, в котором оно хранится в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (`TESTCOMPUTER\User`).  
  
**Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
```  
SELECT SUSER_SNAME(SUSER_SID('TestComputer\User', 0));  
```  
  
## <a name="see-also"></a>См. также:  
 [ORIGINAL_LOGIN (Transact-SQL)](../../t-sql/functions/original-login-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [binary и varbinary (Transact-SQL)](../../t-sql/data-types/binary-and-varbinary-transact-sql.md)   
 [Системные функции (Transact-SQL)](../../relational-databases/system-functions/system-functions-category-transact-sql.md)  
  
  
