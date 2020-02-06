---
title: Коды возврата и сведения об ошибках OLE-автоматизации | Документация Майкрософт
ms.custom: ''
ms.date: 07/05/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: conceptual
helpviewer_keywords:
- return codes [SQL Server]
- OLE Automation [SQL Server], return codes
- OLE Automation [SQL Server], errors
ms.assetid: 9696fb05-e9e8-4836-b359-d4de0be0eeb2
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 12bfbfa82768efe361f9b067764c7b5a4c408931
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68136761"
---
# <a name="ole-automation-return-codes-and-error-information"></a>Коды возврата и сведения об ошибках OLE-автоматизации
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Системные хранимые процедуры OLE-автоматизации возвращают код возврата типа **int** , который представляет собой значение HRESULT, возвращенное базовой операцией OLE-автоматизации. Значение HRESULT, равное 0, свидетельствует об успешном завершении операции. Ненулевое значение HRESULT является кодом ошибки OLE, представленным в шестнадцатеричной форме 0x800*nnnnn*, однако при возврате из хранимой процедуры в качестве кода возврата значения с типом **int** значение HRESULT представляется в форме 214*nnnnnnn*.  
  
 Например, если в хранимую процедуру sp_OACreate передать недопустимое имя объекта (SQLDMO.Xyzzy), она возвратит значение HRESULT типа **int** , равное 2 147 221 005, что эквивалентно шестнадцатеричному 0x800401f3.  
  
 Процедуру `CONVERT(binary(4), @hresult)` можно использовать для преобразования значения HRESULT типа **int** в значение типа **binary** . Однако в результате вызова `CONVERT(char(10), CONVERT(binary(4), @hresult))` будет получена нечитаемая строка, потому что каждый байт значения HRESULT будет преобразован в один символ ASCII. Чтобы преобразовать значение HRESULT типа **int** в значение типа **char** , представляющее читаемую шестнадцатеричную строку, можно использовать приведенный ниже образец хранимой процедуры HexToChar.  
  
```  
USE AdventureWorks2012;  
GO  
IF EXISTS(SELECT name FROM sys.objects  
          WHERE name = N'dbo.sp_HexToChar')  
    DROP PROCEDURE HexToChar;  
GO  
CREATE PROCEDURE dbo.sp_HexToChar  
    @BinValue varbinary(255),  
    @HexCharValue nvarchar(255) OUTPUT  
AS  
    DECLARE @CharValue nvarchar(255);  
    DECLARE @Position int;  
    DECLARE @Length int;  
    DECLARE @HexString nchar(16);  
    SELECT @CharValue = N'0x';  
    SELECT @Position = 1;  
    SELECT @Length = DATALENGTH(@BinValue);  
    SELECT @HexString = N'0123456789ABCDEF';  
    WHILE (@Position <= @Length)  
    BEGIN  
        DECLARE @TempInt int;  
        DECLARE @FirstInt int;  
        DECLARE @SecondInt int;  
        SELECT @TempInt = CONVERT(int, SUBSTRING(@BinValue,@Position,1));  
        SELECT @FirstInt = FLOOR(@TempInt/16);  
        SELECT @SecondInt = @TempInt - (@FirstInt*16);  
        SELECT @CharValue = @CharValue +  
            SUBSTRING(@HexString, @FirstInt+1, 1) +  
            SUBSTRING(@HexString, @SecondInt+1, 1);  
        SELECT @Position = @Position + 1;  
    END  
    SELECT @HexCharValue = @CharValue;  
GO  
DECLARE @BinVariable varbinary(35);  
DECLARE @CharValue nvarchar(35);  
  
SET @BinVariable = 123456;  
  
EXECUTE dbo.sp_HexToChar  
    @binvalue = @BinVariable,  
    @HexCharValue = @CharValue OUTPUT;  
  
SELECT @BinVariable AS BinaryValue,  
    @CharValue AS CharacterRep;  
GO  
```  
  
 Приведенный ниже образец хранимой процедуры **sp_displayoaerrorinfo** позволяет вывести сведения об ошибке OLE-автоматизации, если одна из процедур OLE-автоматизации возвратит ненулевой код возврата HRESULT. В этом образце хранимой процедуры используется процедура **HexToChar**.  
  
```  
CREATE PROCEDURE dbo.sp_DisplayOAErrorInfo  
    @Object int,  
    @HResult int  
AS  
    DECLARE @Output nvarchar(255);  
    DECLARE @HRHex nchar(10);  
    DECLARE @HR int;  
    DECLARE @Source nvarchar(255);  
    DECLARE @Description nvarchar(255);  
    PRINT N'OLE Automation Error Information';  
    EXEC sp_HexToChar @HResult, @HRHex OUT;  
    SELECT @Output = N'  HRESULT: ' + @HRHex;  
    PRINT @Output;  
    EXEC @HR = sp_OAGetErrorInfo  
        @Object,  
        @Source OUT,  
        @Description OUT;  
    IF @HR = 0  
    BEGIN  
        SELECT @Output = N'  Source: ' + @Source;  
        PRINT @Output;  
        SELECT @Output = N'  Description: '  
               + @Description;  
        PRINT @Output;  
    END  
    ELSE  
    BEGIN  
       PRINT N' sp_OAGetErrorInfo failed.';  
       RETURN;  
    END  
GO  
```  
  
## <a name="related-content"></a>См. также  
 [sp_OAGetErrorInfo (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-oageterrorinfo-transact-sql.md)  
  
  
