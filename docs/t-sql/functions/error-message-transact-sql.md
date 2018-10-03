---
title: ERROR_MESSAGE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ERROR_MESSAGE_TSQL
- ERROR_MESSAGE
dev_langs:
- TSQL
helpviewer_keywords:
- ERROR_MESSAGE function
- errors [SQL Server], text of
- messages [SQL Server], text of
- TRY...CATCH [SQL Server]
- CATCH block
ms.assetid: f32877a6-5f17-418c-a32c-5a1a344b3c45
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ab08801cb70dc2048e03e1be394e6fa897b087e2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47807262"
---
# <a name="errormessage-transact-sql"></a>ERROR_MESSAGE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Эта функция возвращает текст сообщения об ошибке, которая вызвала выполнение блока CATCH конструкции TRY…CATCH.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
ERROR_MESSAGE ( )   
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **nvarchar(4000)**  
  
## <a name="return-value"></a>Возвращаемое значение  
При вызове в блоке CATCH функция `ERROR_MESSAGE` возвращает полный текст сообщения об ошибке, запустившей блок `CATCH`. Текст содержит значения подставляемых параметров, таких как длина, имена объектов или время.  
  
Функция `ERROR_MESSAGE` возвращает значение NULL в случае вызова вне блока CATCH.  
  
## <a name="remarks"></a>Remarks  
Функцию `ERROR_MESSAGE` можно вызывать в любом месте области действия блока CATCH.  
  
Функция `ERROR_MESSAGE` возвращает соответствующее сообщение об ошибке независимо от количества ее выполнений или от места ее вызова в области действия блока `CATCH`. В этом ее отличие от таких функций, как @@ERROR, которые возвращают номер ошибки только в той инструкции, которая непосредственно следует за инструкцией, вызвавшей ошибку.  
  
Во вложенных блоках `CATCH` функция `ERROR_MESSAGE` возвращает сообщение об ошибке, соответствующее области действия блока `CATCH`, который ссылался на данный блок `CATCH`. Например, блок `CATCH` внешней конструкции TRY...CATCH может содержать внутреннюю конструкцию `TRY...CATCH`. Во внутреннем блоке `CATCH` функция `ERROR_MESSAGE` возвращает сообщение об ошибке, вызвавшей внутренний блок `CATCH`. Если функция `ERROR_MESSAGE` выполняется во внешнем блоке `CATCH`, она возвращает сообщение об ошибке, вызвавшей внешний блок `CATCH`.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-errormessage-in-a-catch-block"></a>A. Использование функции ERROR_MESSAGE в блоке CATCH  
В приведенном ниже примере показана инструкция `SELECT`, вызывающая ошибку деления на ноль. Блок `CATCH` возвращает сообщение об ошибке.  
  
```  
  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  

-----------

(0 row(s) affected)

ErrorMessage
----------------------------------
Divide by zero error encountered.

(1 row(s) affected)

```  
  
### <a name="b-using-errormessage-in-a-catch-block-with-other-error-handling-tools"></a>Б. Использование функции ERROR_MESSAGE в блоке CATCH с другими средствами обработки ошибок  
В приведенном ниже примере показана инструкция `SELECT`, вызывающая ошибку деления на ноль. Вместе с сообщением об ошибке блок `CATCH` возвращает сведения о ней.  
  
```  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT  
        ERROR_NUMBER() AS ErrorNumber  
        ,ERROR_SEVERITY() AS ErrorSeverity  
        ,ERROR_STATE() AS ErrorState  
        ,ERROR_PROCEDURE() AS ErrorProcedure  
        ,ERROR_LINE() AS ErrorLine  
        ,ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  

-----------

(0 row(s) affected)

ErrorNumber ErrorSeverity ErrorState  ErrorProcedure  ErrorLine  ErrorMessage
----------- ------------- ----------- --------------- ---------- ----------------------------------
8134        16            1           NULL            4          Divide by zero error encountered.

(1 row(s) affected)

```
  

