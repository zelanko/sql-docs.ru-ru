---
title: "Добавить подпись (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 05/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ADD SIGNATURE
- ADD_SIGNATURE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ADD SIGNATURE statement
- adding digital signatures
- signatures [SQL Server]
- digital signatures [SQL Server]
ms.assetid: 64d8b682-6ec1-4e5b-8aee-3ba11e72d21f
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 022c07cfc66694642da57042284c638ca1587496
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="add-signature-transact-sql"></a>ADD SIGNATURE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Добавляет цифровую подпись для хранимой процедуры, функции, сборки или триггера. Добавляет также скрепляющую подпись для хранимой процедуры, функции, сборки или триггера.  
  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
ADD [ COUNTER ] SIGNATURE TO module_class::module_name   
    BY <crypto_list> [ ,...n ]  
  
<crypto_list> ::=  
    CERTIFICATE cert_name  
    | CERTIFICATE cert_name [ WITH PASSWORD = 'password' ]  
    | CERTIFICATE cert_name WITH SIGNATURE = signed_blob   
    | ASYMMETRIC KEY Asym_Key_Name  
    | ASYMMETRIC KEY Asym_Key_Name [ WITH PASSWORD = 'password'.]  
    | ASYMMETRIC KEY Asym_Key_Name WITH SIGNATURE = signed_blob  
```  
  
## <a name="arguments"></a>Аргументы  
 *module_class*  
 Класс модуля, к которому добавляется подпись. По умолчанию для модулей области схемы это класс OBJECT.  
  
 *имя_модуля*  
 Имя хранимой процедуры, функции, сборки или триггера, для которых будет добавлена подпись или скрепляющая подпись.  
  
 СЕРТИФИКАТ *cert_name*  
 Имя сертификата, который будет использован для добавления подписи или скрепляющей подписи для хранимой процедуры, функции, сборки или триггера.  
  
 С ПАРОЛЕМ = "*пароль*"  
 Пароль, необходимый для расшифровки закрытого ключа сертификата или асимметричного ключа. Это предложение необходимо, только когда закрытый ключ не защищен главным ключом базы данных.  
  
 ПОДПИСЬ =*signed_blob*  
 Указывает подписанный большой двоичный объект (BLOB) модуля. Это предложение полезно, если нужно передать модуль без передачи закрытого ключа. При использовании этого предложения необходимы только модуль, подпись и открытый ключ, чтобы добавить подписанный большой двоичный объект в базу данных. *signed_blob* является двоичным объектом в шестнадцатеричном формате.  
  
 АСИММЕТРИЧНЫЙ ключ *Asym_Key_Name*  
 Имя ассиметричного ключа, который будет использован для добавления подписи или скрепляющей подписи для хранимой процедуры, функции, сборки или триггера.  
  
## <a name="remarks"></a>Замечания  
 Подписываемый модуль или модуль, на который ставится скрепляющая подпись, а также сертификат или асимметричный ключ, используемые для подписания, должны существовать. Каждый символ в модуле включен в вычисление подписи. Сюда включены начальные символы возврата каретки и перевода строки.  
  
 Подписи и скрепляющие подписи для модуля могут добавляться любым числом сертификатов и асимметричных ключей.  
  
 Подпись модуля удаляется при изменении модуля.  
  
 Если модуль содержит предложение EXECUTE AS, это значит, что идентификатор безопасности (SID) участника также является частью процесса подписи.  
  
> [!CAUTION]  
>  Подписывание модуля следует использовать только для предоставления разрешений, но не для их запрещения или отмены.  
  
 Встроенные функции с табличным значением нельзя подписывать.  
  
 Сведения о подписях содержатся в представлении каталога sys.crypt_properties.  
  
> [!WARNING]  
>  При воссоздании процедуры для подписи все инструкции в исходном пакете должны соответствовать повторно созданному пакету. Если какая-либо часть пакета будет отличаться, даже количеством пробелов или комментариями, будет получена другая подпись.  
  
## <a name="countersignatures"></a>Скрепляющая подпись  
 При выполнении подписанного модуля, подписи будет временно добавляется в токен SQL, но подписи будут потеряны, если модуль выполняет другой модуль или модуль прекращает выполнение. Скрепляющая подпись — это особая форма подписи. Сама по себе скрепляющая подпись не предоставляет никаких разрешений, но позволяет сохранить подписи, поставленные тем же самым сертификатом или асимметричным ключом, на все время вызова объекта, на котором стоит скрепляющая подпись.  
  
 Предположим, что Алиса вызывает процедуру ProcSelectT1ForAlice, которая вызывает процедуру procSelectT1, выбирающую данные из таблицы T1. У Алисы есть разрешение EXECUTE на процедуры ProcSelectT1ForAlice и procSelectT1, но нет разрешения SELECT на таблицу T1 и во всей этой цепочке нет никаких цепочек владения. Алиса не имеет доступа к таблице T1 — ни прямого, ни с помощью процедур ProcSelectT1ForAlice и procSelectT1. Поскольку мы хотим, чтобы Алиса всегда использовала ProcSelectT1ForAlice для доступа, мы не хотим предоставлять ей разрешение на выполнение процедуры procSelectT1. Что делать в этом случае?  
  
-   Если подписать процедуру procSelectT1 так, чтобы процедура procSelectT1 имела доступ к таблице T1, Алиса сможет прямо вызывать процедуру procSelectT1 и ей не нужно будет вызывать процедуру ProcSelectT1ForAlice.  
  
-   Можно не давать Алисе разрешения EXECUTE на процедуру procSelectT1, но в этом случае Алиса не сможет вызывать процедуру procSelectT1 даже через процедуру ProcSelectT1ForAlice.  
  
-   Подписание процедуры ProcSelectT1ForAlice также не будет работать само по себе, так как подпись будет потеряна при вызове процедуры procSelectT1.  
  
Однако с помощью скрепляющая подпись procSelectT1 с того же сертификата, используемого для подписания ProcSelectT1ForAlice, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сохранит подпись по всей цепочке вызова и обеспечит доступ к T1. Если Алиса захочет прямо обратиться к процедуре procSelectT1, она не сможет это сделать, так как скрепляющая подпись не предоставляет никаких прав. В приведенном ниже примере В показан код [!INCLUDE[tsql](../../includes/tsql-md.md)] для этого примера.  
  
## <a name="permissions"></a>Permissions  
 Требует разрешения ALTER на объект и разрешение CONTROL на сертификат или асимметричный ключ. Если соответствующий закрытый ключ защищен паролем, то у пользователя также должен быть этот пароль.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-signing-a-stored-procedure-by-using-a-certificate"></a>A. Подписание хранимой процедуры с помощью сертификата  
 В следующем примере хранимая процедура `HumanResources.uspUpdateEmployeeLogin` подписывается сертификатом `HumanResourcesDP`.  
  
```  
USE AdventureWorks2012;  
ADD SIGNATURE TO HumanResources.uspUpdateEmployeeLogin   
    BY CERTIFICATE HumanResourcesDP;  
GO  
```  
  
### <a name="b-signing-a-stored-procedure-by-using-a-signed-blob"></a>Б. Подписание хранимой процедуры с помощью подписанного большого двоичного объекта  
 В следующем примере создается новая база данных и сертификат для использования в примере. В этом примере будет создана и подписана простая хранимая процедура и выполнена выборка большого двоичного объекта сигнатуры из `sys.crypt_properties`. Подпись удаляется, затем добавляется еще раз. Процедура подписывается с помощью конструкции WITH SIGNATURE.  
  
```  
CREATE DATABASE TestSignature ;  
GO  
USE TestSignature ;  
GO  
-- Create a CERTIFICATE to sign the procedure.  
CREATE CERTIFICATE cert_signature_demo   
    ENCRYPTION BY PASSWORD = 'pGFD4bb925DGvbd2439587y'  
    WITH SUBJECT = 'ADD SIGNATURE demo';  
GO  
-- Create a simple procedure.  
CREATE PROC [sp_signature_demo]  
AS  
    PRINT 'This is the content of the procedure.' ;  
GO  
-- Sign the procedure.  
ADD SIGNATURE TO [sp_signature_demo]   
    BY CERTIFICATE [cert_signature_demo]   
    WITH PASSWORD = 'pGFD4bb925DGvbd2439587y' ;  
GO  
-- Get the signature binary BLOB for the sp_signature_demo procedure.  
SELECT cp.crypt_property  
    FROM sys.crypt_properties AS cp  
    JOIN sys.certificates AS cer  
        ON cp.thumbprint = cer.thumbprint  
    WHERE cer.name = 'cert_signature_demo' ;  
GO  
```  
  
 Подпись `crypt_property`, возвращаемая этой инструкции, будет изменяться каждый раз при создании процедуры. Запишите результат для использования далее в ходе примера. Для этого примера выдается следующий результат: `0x831F5530C86CC8ED606E5BC2720DA835351E46219A6D5DE9CE546297B88AEF3B6A7051891AF3EE7A68EAB37CD8380988B4C3F7469C8EABDD9579A2A5C507A4482905C2F24024FFB2F9BD7A953DD5E98470C4AA90CE83237739BB5FAE7BAC796E7710BDE291B03C43582F6F2D3B381F2102EEF8407731E01A51E24D808D54B373`.  
  
```  
-- Drop the signature so that it can be signed again.  
DROP SIGNATURE FROM [sp_signature_demo]   
    BY CERTIFICATE [cert_signature_demo];  
GO  
-- Add the signature. Use the signature BLOB obtained earlier.  
ADD SIGNATURE TO [sp_signature_demo]   
    BY CERTIFICATE [cert_signature_demo]  
    WITH SIGNATURE = 0x831F5530C86CC8ED606E5BC2720DA835351E46219A6D5DE9CE546297B88AEF3B6A7051891AF3EE7A68EAB37CD8380988B4C3F7469C8EABDD9579A2A5C507A4482905C2F24024FFB2F9BD7A953DD5E98470C4AA90CE83237739BB5FAE7BAC796E7710BDE291B03C43582F6F2D3B381F2102EEF8407731E01A51E24D808D54B373 ;  
GO  
```  
  
### <a name="c-accessing-a-procedure-using-a-countersignature"></a>В. Обращение к процедуре с помощью скрепляющей подписи  
 В следующем примере показано, как скрепляющая подпись помогает контролировать доступ к объекту.  
  
```  
-- Create tesT1 database  
CREATE DATABASE testDB;  
GO  
USE testDB;  
GO  
-- Create table T1  
CREATE TABLE T1 (c varchar(11));  
INSERT INTO T1 VALUES ('This is T1.');  
  
-- Create a TestUser user to own table T1  
CREATE USER TestUser WITHOUT LOGIN;  
ALTER AUTHORIZATION ON T1 TO TestUser;  
  
-- Create a certificate for signing  
CREATE CERTIFICATE csSelectT  
  ENCRYPTION BY PASSWORD = 'SimplePwd01'  
  WITH SUBJECT = 'Certificate used to grant SELECT on T1';  
CREATE USER ucsSelectT1 FROM CERTIFICATE csSelectT;  
GRANT SELECT ON T1 TO ucsSelectT1;  
  
-- Create a principal with low privileges  
CREATE LOGIN Alice WITH PASSWORD = 'SimplePwd01';  
CREATE USER Alice;  
  
-- Verify Alice cannoT1 access T1;  
EXECUTE AS LOGIN = 'Alice';  
    SELECT * FROM T1;  
REVERT;  
  
-- Create a procedure that directly accesses T1  
CREATE PROCEDURE procSelectT1 AS  
BEGIN  
    PRINT 'Now selecting from T1...';  
    SELECT * FROM T1;  
END;  
GO  
GRANT EXECUTE ON procSelectT1 to public;  
  
-- Create special procedure for accessing T1  
CREATE PROCEDURE  procSelectT1ForAlice AS  
BEGIN  
   IF USER_ID() <> USER_ID('Alice')  
    BEGIN  
        PRINT 'Only Alice can use this.';  
        RETURN  
    END  
   EXEC procSelectT1;  
END;  
GO;  
GRANT EXECUTE ON procSelectT1ForAlice TO PUBLIC;  
  
-- Verify procedure works for a sysadmin user  
EXEC procSelectT1ForAlice;  
  
-- Alice still can't use the procedure yet  
EXECUTE AS LOGIN = 'Alice';  
    EXEC procSelectT1ForAlice;  
REVERT;  
  
-- Sign procedure to grant it SELECT permission  
ADD SIGNATURE TO procSelectT1ForAlice BY CERTIFICATE csSelectT   
WITH PASSWORD = 'SimplePwd01';  
  
-- Counter sign proc_select_t, to make this work  
ADD COUNTER SIGNATURE TO procSelectT1 BY CERTIFICATE csSelectT   
WITH PASSWORD = 'SimplePwd01';  
  
-- Now the proc works.   
-- Note that calling procSelectT1 directly still doesn't work  
EXECUTE AS LOGIN = 'Alice';  
    EXEC procSelectT1ForAlice;  
    EXEC procSelectT1;  
REVERT;  
  
-- Cleanup  
USE master;  
GO  
DROP DATABASE testDB;  
DROP LOGIN Alice;  
  
```  
  
## <a name="see-also"></a>См. также:  
 [sys.crypt_properties &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-crypt-properties-transact-sql.md)   
 [УДАЛИТЬ подпись &#40; Transact-SQL &#41;](../../t-sql/statements/drop-signature-transact-sql.md)  
  
  
