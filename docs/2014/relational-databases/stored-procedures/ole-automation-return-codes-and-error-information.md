---
title: Коды возврата и сведения об ошибках OLE-автоматизации | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: 34744bedb701155d2695f6efc5aab3c493e6cf48
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63011263"
---
# <a name="ole-automation-return-codes-and-error-information"></a>Коды возврата и сведения об ошибках OLE-автоматизации
  Системные хранимые процедуры OLE-автоматизации возвращают код возврата типа `int`, который представляет собой значение HRESULT, возвращенное базовой операцией OLE-автоматизации. Значение HRESULT, равное 0, свидетельствует об успешном завершении операции. Ненулевое значение HRESULT является кодом ошибки OLE в шестнадцатеричной форме 0x800*nnnnn*, однако при возврате `int` значение в код возврата хранимой процедуры, HRESULT имеет форме 214*nnnnnnn*.  
  
 Например если передать недопустимое имя объекта (SQLDMO. (Xyzzy) для sp_OACreate приводит процедуры для возврата `int` значение HRESULT, равное 2147221005, что эквивалентно шестнадцатеричному 0x800401f3.  
  
 Процедуру `CONVERT(binary(4), @hresult)` можно использовать для преобразования значения HRESULT с типом `int` в значение с типом `binary`. Однако в результате вызова `CONVERT(char(10), CONVERT(binary(4), @hresult))` будет получена нечитаемая строка, потому что каждый байт значения HRESULT будет преобразован в один символ ASCII. Для преобразования можно использовать следующий образец хранимой процедуры HexToChar `int` HRESULT `char` значение, содержащее читаемую шестнадцатеричную строку.  
  
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
  
 Приведенный ниже образец хранимой процедуры **sp_displayoaerrorinfo** позволяет вывести сведения об ошибке OLE-автоматизации, если одна из процедур OLE-автоматизации возвратит ненулевой код возврата HRESULT. В этом образце хранимой процедуры используется `HexToChar`.  
  
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
    EXEC HexToChar @HResult, @HRHex OUT;  
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
 [sp_OAGetErrorInfo (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-oageterrorinfo-transact-sql)  
  
  
