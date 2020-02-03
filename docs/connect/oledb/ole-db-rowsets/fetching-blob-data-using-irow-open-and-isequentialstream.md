---
title: Выборка данных BLOB с помощью метода IRow::Open и интерфейса ISequentialStream | Документы Майкрософт
description: Выборка данных BLOB с помощью метода IRow::Open и интерфейса ISequentialStream
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- fetching BLOB data
- Open method
- ISequentialStream interface
- BLOBs, fetching
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 7af4888a77dc96145082f1378713f020b16f56a0
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "68015380"
---
# <a name="fetching-blob-data-using-irowopen-and-isequentialstream"></a>Выборка данных BLOB при помощи метода IRow::Open и интерфейса ISequentialStream
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Метод **IRow::Open** поддерживает открытие только объектов типа DBGUID_STREAM или DBGUID_NULL.  
  
 Следующая функция использует метод **IRow::Open** и интерфейс **ISequentialStream** для выборки больших данных.  
  
```  
void InitializeAndExecuteCommand()  
{  
    ULONG iidx;  
    WCHAR* wCmdString=OLESTR("SELECT * FROM MyTable");  
    // Do the initialization, create the session, and set command text.  
    hr = pICommandText->Execute(NULL, IID_IRow, NULL,   
                         &cNumRows,(IUnknown **)&pIRow)))  
    //Get 1 column at a time.  
    for(ULONG i=1; i <= NoOfColumns; i++)  
      GetSequentialColumn(pIRow, iidx);  
    // Do the clean up.  
}  
HRESULT GetSequentialColumn(IRow* pUnkRow, ULONG iCol)  
{  
    HRESULT hr = NOERROR;  
    ULONG cbRead = 0;  
    ULONG cbTotal = 0;  
    ULONG cColumns = 0;  
    ULONG cReads = 0;  
    ISequentialStream* pIStream = NULL;  
    WCHAR* pBuffer[kMaxBuff]; //50 chars read by ISequentialStream::Read()  
    DBCOLUMNINFO* prgInfo;  
    OLECHAR* pColNames;  
    IColumnsInfo* pIColumnsInfo;  
    DBID columnid;  
    DBCOLUMNACCESS column;  
  
    hr = pUnkRow->QueryInterface(IID_IColumnsInfo,   
                            (void**) &pIColumnsInfo);  
    hr = pIColumnsInfo->GetColumnInfo(&cColumns, &prgInfo, &pColNames);  
    // Get Column ID.  
    columnid = (prgInfo + (iCol - 1))->columnid;  
    // Get sequential stream object by calling IRow::Open.  
    hr = pUnkRow->Open(NULL, &columnid, DBGUID_STREAM, 0,   
                    IID_ISequentialStream,(LPUNKNOWN *)&pIStream);  
    ZeroMemory(pBuffer, kMaxBuff * sizeof(WCHAR));  
    // Read 50 chars at a time until no more data.  
    do  
    {  
        hr = pIStream->Read(pBuffer, kMaxBuff, &cbRead);  
        cbTotal = cbTotal + cbRead;  
        // Process the data.  
    } while(cbRead > 0);  
// Do the clean up.  
    return hr;  
}  
```  
  
 Большие данные могут быть привязаны или получены с помощью интерфейса **ISequentialStream**. Для привязанных столбцов флаг состояния указывает, усекаются ли данные при установке флага DBSTATUS_S_TRUNCATED.  
  
## <a name="see-also"></a>См. также:  
 [Выборка данных большого двоичного объекта при помощи интерфейса IRow](../../oledb/ole-db-rowsets/fetching-a-single-row-with-irow.md)  
  
  
