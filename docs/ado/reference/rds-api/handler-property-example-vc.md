---
description: Пример свойства Handler (Visual C++)
title: Пример свойства Handler (Visual c++) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Handler property [ADO], VC++ example
ms.assetid: d046d89c-622b-48bc-9d30-f454c3e13595
author: rothja
ms.author: jroth
ms.openlocfilehash: 5a570727ef9bdee2ac1411a1594dae518dd4fe36
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88438966"
---
# <a name="handler-property-example-vc"></a>Пример свойства Handler (Visual C++)
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 В этом примере демонстрируется свойство [обработчика](../../../ado/reference/rds-api/handler-property-rds.md) объектов [RDS элемента управления](../../../ado/reference/rds-api/datacontrol-object-rds.md) . (Дополнительные сведения см. в разделе [Настройка фактов](../../../ado/guide/remote-data-service/datafactory-customization.md) .)  
  
 Предположим, что в файле параметров, Msdfmap.ini, расположенном на сервере, есть следующие разделы:  
  
```  
[connect AuthorDataBase]  
Access=ReadWrite  
Connect="DSN=Pubs"  
[sql AuthorById]  
SQL="SELECT * FROM Authors WHERE au_id = ?"  
```  
  
 Код выглядит следующим образом. Команда, назначенная свойству [SQL](../../../ado/reference/rds-api/sql-property.md) , будет соответствовать идентификатору ***аусорбид*** и будет получать строку для автора Ивана о'леари. Несмотря на то, что свойство [Connect](../../../ado/reference/rds-api/connect-property-rds.md) в коде указывает источник данных Northwind, этот источник данных будет перезаписан с помощью раздела Msdfmap.ini *Connect* . Свойство [Recordset](../../../ado/reference/rds-api/recordset-sourcerecordset-properties-rds.md) объекта **элемента управления** данных назначается несвязанному объекту [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) исключительно в качестве удобства для написания кода.  
  
```  
// BeginHandlerCpp.cpp  
// compile with: /EHsc  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
#import "msadco.dll"  
  
#include <ole2.h>  
#include <stdio.h>  
#include <conio.h>  
  
// Function declarations  
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);};  
void HandlerX();  
void PrintProviderError(_ConnectionPtr pConnection);  
void PrintComError(_com_error &e);  
  
int main() {  
   HRESULT hr = S_OK;  
   hr = ::CoInitialize(NULL);  
   if (SUCCEEDED(hr)) {  
      HandlerX();  
      ::CoUninitialize();  
   }  
}  
  
void HandlerX() {  
   HRESULT  hr = S_OK;  
   // Define and initialize ADO object pointers, in the ADODB namespace.     
   _RecordsetPtr pRst = NULL;  
  
   // Define RDS object pointers.  
   RDS::IBindMgrPtr dc;  
  
   try {  
      TESTHR(hr = dc.CreateInstance(__uuidof(RDS::DataControl)));  
      dc->Handler = "MSDFMAP.Handler";  
      dc->ExecuteOptions = 1;  
      dc->FetchOptions = 1;  
      dc->Server = "https://MyServer";  
      dc->Connect = "Data Source=AuthorDatabase";  
      dc->SQL = "AuthorById('267-41-2394')";  
  
      // Retrieve the record.  
      dc->Refresh();  
  
      // Use another Recordset as a convenience.  
      pRst = dc->GetRecordset();  
      printf("Author is %s %s",   
         (LPSTR)(_bstr_t) pRst->Fields->GetItem("au_fname")->Value,   
         (LPSTR)(_bstr_t) pRst->Fields->GetItem("au_lname")->Value);  
      pRst->Close();  
  
   }  // End Try statement.  
   catch (_com_error &e) {  
      PrintProviderError(pRst->GetActiveConnection());  
      PrintComError(e);  
   }  
}  
  
void PrintProviderError(_ConnectionPtr pConnection) {  
   // Print Provider Errors from Connection object.  
   // pErr is a record object in the Connection's Error collection.  
   ErrorPtr pErr = NULL;  
   long nCount = 0;  
   long i = 0;  
  
   if ( (pConnection->Errors->Count) > 0) {  
      nCount = pConnection->Errors->Count;  
      // Collection ranges from 0 to nCount -1.  
      for ( i = 0 ; i < nCount ; i++ ) {  
         pErr = pConnection->Errors->GetItem(i);  
         printf("\t Error number: %x\t%s", pErr->Number, pErr->Description);  
      }  
   }  
}  
  
void PrintComError(_com_error &e) {  
   _bstr_t bstrSource(e.Source());  
   _bstr_t bstrDescription(e.Description());  
  
   // Print Com errors.    
   printf("Error\n");  
   printf("\tCode = %08lx\n", e.Error());  
   printf("\tCode meaning = %s\n", e.ErrorMessage());  
   printf("\tSource = %s\n", (LPCSTR) bstrSource);  
   printf("\tDescription = %s\n", (LPCSTR) bstrDescription);  
}  
```  
  
## <a name="see-also"></a>См. также:  
 [Объект элемента управления (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)   
 [Свойство Handler (служба удаленных рабочих столов)](../../../ado/reference/rds-api/handler-property-rds.md)






















