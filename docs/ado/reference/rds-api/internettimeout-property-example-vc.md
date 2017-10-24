---
title: "Пример свойства InternetTimeout (VC ++) | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- InternetTimeout property [ADO], VC++ example
ms.assetid: 88b6d05c-d4eb-4ab1-bbe2-95d146237f94
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 41b7d8dbc90c2cea8eaa198b0caf15aefd8051ba
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="internettimeout-property-example-vc"></a>Пример свойства InternetTimeout (VC ++)
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 В этом примере демонстрируется [InternetTimeout](../../../ado/reference/rds-api/internettimeout-property-rds.md) свойство, которое существует на [DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) и [DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) объектов. В этом случае **InternetTimeout** показано свойство на **DataControl** объекта и значение времени ожидания устанавливается в значение 20 секунд.  
  
```  
// BeginInternetTimeoutCpp  
#import "c:\Program Files\Common Files\System\ADO\msado15.dll" \  
    no_namespace rename("EOF", "EndOfFile")  
#import "C:\Program Files\Common Files\System\MSADC\msadco.dll"  
  
#include <ole2.h>  
#include <stdio.h>  
#include <conio.h>  
  
// Function declarations  
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);};  
void InternetTimeOutX(void);  
void PrintProviderError(_ConnectionPtr pConnection);  
void PrintComError(_com_error &e);  
  
//////////////////////////////////////////////////////////  
//                                                      //  
//    Main Function                                     //  
//                                                      //  
//////////////////////////////////////////////////////////  
  
void main()  
{  
    if(FAILED(::CoInitialize(NULL)))  
        return;  
  
    InternetTimeOutX();  
  
    ::CoUninitialize();  
}  
  
//////////////////////////////////////////////////////////  
//                                                      //  
//         InternetTimeOutX Function                    //  
//                                                      //  
//////////////////////////////////////////////////////////  
  
void InternetTimeOutX(void)   
{  
    HRESULT hr = S_OK;  
  
    // Define ADO object pointers.  
    // Initialize pointers on define.  
    // These are in the ADODB::  namespace.  
    _RecordsetPtr  pRst = NULL;  
  
    //Define RDS object pointers  
    RDS::IBindMgrPtr dc ;  
  
    try  
    {  
        TESTHR(dc.CreateInstance(__uuidof(RDS::DataControl)));  
        dc->Server = "http://MyServer";  
        dc->Connect = "Data Source='AuthorDatabase'";  
        dc->SQL = "SELECT * FROM Authors";  
  
        // Wait at least 20 seconds.  
        dc->InternetTimeout = 20000;  
        dc->Refresh();  
  
        // Use another Recordset as a convenience  
        pRst = dc->GetRecordset();  
        while(!(pRst->EndOfFile))  
        {  
            printf("%s %s",(LPSTR) (_bstr_t) pRst->Fields->  
                GetItem("au_fname")->Value,  
               (LPSTR) (_bstr_t) pRst->Fields->  
                GetItem("au_lname")->Value);  
  
            pRst->MoveNext();  
        }  
        pRst->Close();  
    }  
  
    catch (_com_error &e)  
    {  
        PrintProviderError(pRst->GetActiveConnection());  
        PrintComError(e);  
    }  
}  
  
//////////////////////////////////////////////////////////  
//                                                      //  
//     PrintProviderError Function                      //  
//                                                      //  
//////////////////////////////////////////////////////////  
  
void PrintProviderError(_ConnectionPtr pConnection)  
{  
    // Print Provider Errors from Connection object.  
    // pErr is a record object in the Connection's Error collection.  
    ErrorPtr  pErr  = NULL;  
  
    if( (pConnection->Errors->Count) > 0)  
    {  
        long nCount = pConnection->Errors->Count;  
        // Collection ranges from 0 to nCount -1.  
        for(long i = 0; i < nCount; i++)  
        {  
            pErr = pConnection->Errors->GetItem(i);  
            printf("\t Error number: %x\t%s", pErr->Number,   
                pErr->Description);  
        }  
    }  
}  
  
//////////////////////////////////////////////////////////  
//                                                      //  
//     PrintComError Function                           //  
//                                                      //  
//////////////////////////////////////////////////////////  
  
void PrintComError(_com_error &e)  
{  
    _bstr_t bstrSource(e.Source());  
    _bstr_t bstrDescription(e.Description());  
  
    // Print Com errors.    
    printf("Error\n");  
    printf("\tCode = %08lx\n", e.Error());  
    printf("\tCode meaning = %s\n", e.ErrorMessage());  
    printf("\tSource = %s\n", (LPCSTR) bstrSource);  
    printf("\tDescription = %s\n", (LPCSTR) bstrDescription);  
}  
// EndInternetTimeoutCpp  
```  
  
## <a name="see-also"></a>См. также:  
 [Свойство InternetTimeout (RDS)](../../../ado/reference/rds-api/internettimeout-property-rds.md)



