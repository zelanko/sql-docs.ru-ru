---
title: sp_getbindtoken (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_getbindtoken
- sp_getbindtoken_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_getbindtoken
ms.assetid: 5db87d77-85fa-45a3-a23a-3ea500f9a5ac
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: dca4015832f8bebf5501c4b3a7e84339bf62957b
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82833216"
---
# <a name="sp_getbindtoken-transact-sql"></a>sp_getbindtoken (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает уникальный идентификатор для транзакции. Этот уникальный идентификатор является строкой, используемой для привязки сеансов при помощи процедуры sp_bindsession.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Используйте режим MARS или распределенные транзакции. Дополнительные сведения см. [в разделе Использование нескольких активных результирующих наборов &#40;режиме MARS&#41;](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_getbindtoken [@out_token =] 'return_value' OUTPUT   
```  
  
## <a name="arguments"></a>Аргументы  
 [ @out_token =] "*RETURN_VALUE*"  
 Токен, используемый для связывания сеансов. *RETURN_VALUE* имеет тип **varchar (255)** и не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Нет  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 sp_getbindtoken будет возвращать действительный маркер только в том случае, если хранимая процедура выполняется внутри активной транзакции. В противном случае компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] возвращает сообщение об ошибке. Пример:  
  
```  
-- Declare a variable to hold the bind token.  
-- No active transaction.  
DECLARE @bind_token varchar(255);  
-- Trying to get the bind token returns an error 3921.  
EXECUTE sp_getbindtoken @bind_token OUTPUT;  
Server: Msg 3921, Level 16, State 1, Procedure sp_getbindtoken, Line 4  
Cannot get a transaction token if there is no transaction active.  
Reissue the statement after a transaction has been started.  
```  
  
 Если sp_getbindtoken используется для прикрепления соединения распределенных транзакций в открытой транзакции, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает тот же токен. Пример:  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @bind_token varchar(255);  
  
BEGIN TRAN;  
  
EXECUTE sp_getbindtoken @bind_token OUTPUT;  
SELECT @bind_token AS Token;  
  
BEGIN DISTRIBUTED TRAN;  
  
EXECUTE sp_getbindtoken @bind_token OUTPUT;  
SELECT @bind_token AS Token;  
```  
  
 Обе инструкции `SELECT` возвращают один и тот же токен:  
  
```  
Token  
-----  
PKb'gN5<9aGEedk_16>8U=5---/5G=--  
(1 row(s_) affected)  
  
Token  
-----  
PKb'gN5<9aGEedk_16>8U=5---/5G=--  
(1 row(s_) affected)  
```  
  
 Токен привязки может быть использован с процедурой sp_bindsession для привязки новых сеансов к одной и той же транзакции. Токен привязки действителен только локально внутри каждого экземпляра компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и не может разделяться несколькими экземплярами.  
  
 Для получения и передачи токена привязки необходимо выполнить процедуру sp_getbindtoken перед выполнением процедуры sp_bindsession  для использования общего пространства блокировок. Если получен токен привязки, процедура sp_bindsession выполняется правильно.  
  
> [!NOTE]  
>  Для получения токена привязки для использования из расширенной хранимой процедуры рекомендуется использовать интерфейс прикладного программирования (API) Open Data Services процедуры srv_getbindtoken.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в роли public.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано получение токена привязки и отображается имя токена привязки.  
  
```  
DECLARE @bind_token varchar(255);  
BEGIN TRAN;  
EXECUTE sp_getbindtoken @bind_token OUTPUT;  
SELECT @bind_token AS Token;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Token`  
  
 `----------------------------------------------------------`  
  
 `\0]---5^PJK51bP<1F<-7U-]ANZ`  
  
## <a name="see-also"></a>См. также  
 [sp_bindsession &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-bindsession-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [API srv_getbindtoken &#40;расширенных хранимых процедур&#41;](../../relational-databases/extended-stored-procedures-reference/srv-getbindtoken-extended-stored-procedure-api.md)  
  
  
