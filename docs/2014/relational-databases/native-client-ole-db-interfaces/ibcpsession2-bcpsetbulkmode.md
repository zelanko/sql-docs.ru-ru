---
title: 'Метода IBCPSession2:: BCPSetBulkMode | Документация Майкрософт'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- BCPSetBulkMode function
ms.assetid: babba19f-e67b-450c-b0e6-523a0f9d23ab
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2e2ba7f2874cc35fbd662c8696fa999980b52bb6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62989990"
---
# <a name="ibcpsession2bcpsetbulkmode"></a>IBCPSession2::BCPSetBulkMode
  Метода IBCPSession2:: BCPSetBulkMode предоставляет альтернативу [IBCPSession:: BCPColFmt &#40;OLE DB&#41;](ibcpsession-bcpcolfmt-ole-db.md) для указания формата столбца. В отличие от IBCPSession:: BCPColFmt, который устанавливает атрибуты формата отдельных столбцов, метода IBCPSession2:: BCPSetBulkMode задает все атрибуты.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT BCPSetBulkMode (  
      int property,  
   void * pField,  
   int cbField,  
   void * pRow,  
   int cbRow  
);  
```  
  
## <a name="arguments"></a>Аргументы  
 *property*  
 Константа типа BYTE. Список констант см. в таблице в подразделе «Примечания».  
  
 *пфиелд*  
 Указатель на значение признака конца поля.  
  
 cbField  
 Длина в байтах значения признака конца поля.  
  
 pRow  
 Указатель на значение признака конца строки.  
  
 cbRow  
 Длина в байтах значения признака конца строки.  
  
## <a name="returns"></a>Возвращает  
 Метода IBCPSession2:: BCPSetBulkMode может возвращать одно из следующих данных:  
  
|||  
|-|-|  
|`S_OK`|Метод выполнен успешно.|  
|`E_FAIL`|Произошла ошибка, связанная с поставщиком. Подробные сведения можно получить с помощью интерфейса ISQLServerErrorInfo.|  
|`E_UNEXPECTED`|Непредвиденный вызов метода. Например, `IBCPSession2::BCPInit` метод не был вызван до вызова метода IBCPSession2:: BCPSetBulkMode.|  
|`E_INVALIDARG`|Недопустимое значение аргумента.|  
|`E_OUTOFMEMORY`|Ошибка, связанная с нехваткой памяти.|  
  
## <a name="remarks"></a>Remarks  
 Метода IBCPSession2:: BCPSetBulkMode можно использовать для выполнения полного копирования из запроса или таблицы. При использовании метода IBCPSession2::BCPSetBulkMode для массового копирования из инструкции запроса его необходимо вызывать до вызова метода `IBCPSession::BCPControl(BCP_OPTIONS_HINTS, ...)` для указания инструкции запроса.  
  
 В рамках одной команды не следует сочетать синтаксис вызова RPC с синтаксисом пакетных запросов (например,`{rpc func};SELECT * from Tbl`).  Это вызовет ICommandPrepare::P готовка, чтобы вернуть ошибку и предотвратить получение метаданных. Если в рамках одной команды требуется объединить выполнение хранимой процедуры и пакетный запрос, то следует использовать синтаксис ODBC CALL (например,`{call func}; SELECT * from Tbl`).  
  
 В следующей таблице перечислены константы для параметра *property* .  
  
|Свойство|Description|  
|--------------|-----------------|  
|BCP_OUT_CHARACTER_MODE|Указывает символьный режим вывода.<br /><br /> Соответствует параметру-c в BCP. EXE, и для IBCPSession:: BCPColFmt со свойством *еусердататипе* , `BCP_TYPE_SQLCHARACTER`имеющим значение.|  
|BCP_OUT_WIDE_CHARACTER_MODE|Указывает режим вывода в Юникоде.<br /><br /> Соответствует параметру-w в BCP. EXE и IBCPSession:: BCPColFmt со свойством *еусердататипе* , `BCP_TYPE_SQLNCHAR`имеющим значение.|  
|BCP_OUT_NATIVE_TEXT_MODE|Указывает собственные типы для несимвольных типов и Юникод для символьных типов.<br /><br /> Соответствует параметру-N в BCP. EXE и IBCPSession:: BCPColFmt со свойством *еусердататипе* , `BCP_TYPE_SQLNCHAR` имеющим значение, если тип столбца является строкой или `BCP_TYPE_DEFAULT` если не является строкой.|  
|BCP_OUT_NATIVE_MODE|Указывает типы данных базы данных.<br /><br /> Соответствует параметру-n в BCP. EXE и IBCPSession:: BCPColFmt со свойством *еусердататипе* , `BCP_TYPE_DEFAULT`имеющим значение.|  
  
 Можно вызвать IBCPSession:: BCPControl и метода IBCPSession2:: BCPSetBulkMode for IBCPSession:: BCPControl, которые не конфликтуют с метода IBCPSession2:: BCPSetBulkMode. Например, можно вызвать IBCPSession:: BCPControl с `BCP_OPTION_FIRST` и метода IBCPSession2:: BCPSetBulkMode.  
  
 Нельзя вызывать IBCPSession:: BCPControl с `BCP_OPTION_TEXTFILE` и метода IBCPSession2:: BCPSetBulkMode.  
  
 При попытке вызвать метода IBCPSession2:: BCPSetBulkMode с последовательностью вызовов функций, включающих IBCPSession:: BCPColFmt, IBCPSession:: BCPControl и IBCPSession:: BCPReadFmt, один из вызовов функции возвратит ошибку последовательности. Если необходимо исправить ошибку, вызовите IBCPSession::BCPInit, чтобы сбросить параметры и начать заново.  
  
 В следующей таблице приведено несколько примеров вызовов функций, которые вызовут ошибку последовательности.  
  
 Последовательность вызовов  
  
```  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_IN);  
BCPSetBulkMode();  
```  
  
```  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPSetBulkMode();  
BCPReadFmt();  
```  
  
```  
BCPInit(NULL, "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPControl(BCP_OPTION_HINTS, "select ...");  
BCPSetBulkMode();  
```  
  
```  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPSetBulkMode();  
BCPColFmt();  
```  
  
```  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPControl(BCP_OPTION_DELAYREADFMT, true);  
BCPReadFmt();  
BCPColFmt();  
```  
  
```  
BCPInit(NULL, "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPControl(BCP_OPTION_DELAYREADFMT, true);  
BCPSetBulkMode();  
BCPControl(BCP_OPTION_HINTS, "select ...");  
BCPReadFmt();  
```  
  
```  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPControl(BCP_OPTION_DELAYREADFMT, true);  
BCPColumns();  
```  
  
```  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPControl(BCP_OPTION_DELAYREADFMT, true);  
BCPSetColFmt();  
```  
  
## <a name="example"></a>Пример  
 В следующем образце создается четыре файла с использованием разных параметров метода IBCPSession2::BCPSetBulkMode.  
  
```  
  
// compile with: sqlncli11.lib oleaut32.lib ole32.lib  
  
#include <stdio.h>  
#include "sqlncli.h"  
  
IDBInitialize*  g_pIDBInitialize = NULL;  
IBCPSession2 * g_pIBcpSession = NULL;  
class COLEDBPropSet : public DBPROPSET {  
public:  
   COLEDBPropSet() {  
      rgProperties = NULL;  
      cProperties = 0;  
   };  
   COLEDBPropSet(const GUID& guid) {  
      rgProperties = NULL;  
      cProperties = 0;  
      guidPropertySet = guid;  
   };  
   ~COLEDBPropSet() {  
      for ( ULONG i = 0 ; i < cProperties ; i++ )  
         VariantClear(&rgProperties[i].vValue);  
      CoTaskMemFree(rgProperties);  
   }  
   void SetGUID(const GUID& guid) {  
      guidPropertySet = guid;  
   };  
   bool AddProperty(DWORD dwPropertyID, bool bValue) {  
      if (!Add())  
         return false;  
      rgProperties[cProperties].dwPropertyID = dwPropertyID;  
      rgProperties[cProperties].vValue.vt = VT_BOOL;  
      rgProperties[cProperties].vValue.boolVal = (bValue) ? VARIANT_TRUE : VARIANT_FALSE;  
      cProperties++;  
      return true;  
   };  
   bool AddProperty(DWORD dwPropertyID, long nValue) {  
      if (!Add())  
         return false;  
      rgProperties[cProperties].dwPropertyID  = dwPropertyID;  
      rgProperties[cProperties].vValue.vt     = VT_I4;  
      rgProperties[cProperties].vValue.lVal   = nValue;  
      cProperties++;  
      return true;  
   };  
   bool AddProperty(DWORD dwPropertyID,LPCWSTR szValue) {  
      if (!Add())  
         return false;  
      rgProperties[cProperties].dwPropertyID = dwPropertyID;  
      rgProperties[cProperties].vValue.vt = VT_BSTR;  
      rgProperties[cProperties].vValue.bstrVal = SysAllocString(szValue);  
      cProperties++;  
      return true;  
   };  
   bool Add() {  
      DBPROP* p = (DBPROP*)CoTaskMemRealloc(rgProperties, (cProperties + 1) * sizeof(DBPROP));  
      if (p != NULL) {  
         rgProperties = p;  
         rgProperties[cProperties].dwOptions = DBPROPOPTIONS_REQUIRED;  
         rgProperties[cProperties].colid = DB_NULLID;  
         rgProperties[cProperties].vValue.vt = VT_EMPTY;  
         return true;  
      }  
      else  
         return false;  
   };  
};  
  
void OLEDBCleanUp() {  
   if (g_pIDBInitialize) {  
      g_pIDBInitialize->Release();  
      g_pIDBInitialize = NULL;  
   }  
   if (g_pIBcpSession) {  
      g_pIBcpSession->Release();  
      g_pIBcpSession = NULL;  
   }  
}  
  
BOOL MakeOLEDBConnect(LPWSTR  pServer) {  
   BOOL ret = true;  
   IDBProperties * pIDBProperties = NULL;  
   IDBCreateSession * pIDBCreateSession = NULL;  
   COLEDBPropSet PropSet(DBPROPSET_DBINIT);  
   COLEDBPropSet BcpProperty(DBPROPSET_SQLSERVERDATASOURCE);  
   try {  
      HRESULT hr = CoInitializeEx(NULL,COINIT_MULTITHREADED);   
      hr = CoCreateInstance(SQLNCLI_CLSID, NULL, CLSCTX_INPROC_SERVER, IID_IDBInitialize, (LPVOID *)&g_pIDBInitialize);  
      if (FAILED(hr)) {  
         printf("CoCreateInstance failed\n");  
         return false;  
      }  
      PropSet.AddProperty(DBPROP_INIT_DATASOURCE, (LPWSTR)pServer);  
      PropSet.AddProperty(DBPROP_AUTH_INTEGRATED, L"SSPI");  
      hr = g_pIDBInitialize->QueryInterface(IID_IDBProperties, (void**) &pIDBProperties);  
      if (FAILED(hr)) {  
         printf("g_pIDBInitialize->->QueryInterface(IID_IDBProperties...) failed\n");  
         throw false;  
      }  
      hr = pIDBProperties->SetProperties(1, &PropSet);  
      if (FAILED(hr)) {  
         printf("g_pIDBInitialize->->SetProperties(...) failed\n");  
         throw false;  
      }  
      hr = g_pIDBInitialize->Initialize();  
      if (FAILED(hr)) {  
         printf("g_pIDBInitialize->->Initialize() failed\n");  
         throw false;  
      }  
      BcpProperty.AddProperty(SSPROP_ENABLEFASTLOAD, true);  
      BcpProperty.AddProperty(SSPROP_ENABLEBULKCOPY, true);  
      hr = pIDBProperties->SetProperties(1, &BcpProperty);  
      if (FAILED(hr)) {  
         printf("g_pIDBInitialize->->SetProperties() for bcp failed\n");  
         throw false;  
      }  
      hr = g_pIDBInitialize->QueryInterface(IID_IDBCreateSession, (void**) &pIDBCreateSession);  
      if (FAILED(hr)) {  
         printf("g_pIDBInitialize->QueryInterface(IID_IDBCreateSession..) failed\n");  
         throw false;  
      }  
  
      hr = pIDBCreateSession->CreateSession(NULL, IID_IBCPSession2, (IUnknown**) &g_pIBcpSession);  
      if (FAILED(hr)) {  
         printf("g_pIDBCreateSession->CreateSession() failed\n");  
         throw false;  
      }  
   }  
   catch(...) {  
      ret = false;  
   }  
   if (pIDBProperties)  
      pIDBProperties->Release();  
   if (pIDBCreateSession)  
      pIDBCreateSession->Release();  
   return ret;  
}  
  
BOOL BCPSetBulkMode(LPWSTR pszServer, LPTSTR pszQureryOut, char BCPType, LPWSTR pszDataFile) {  
   HRESULThr;  
   if (!MakeOLEDBConnect(pszServer))  
      return false;  
   hr = g_pIBcpSession->BCPInit(NULL, pszDataFile, NULL, BCP_DIRECTION_OUT );   // bcp init for queryout  
   if (FAILED(hr)) {  
      printf("BCP init failed\n");  
      OLEDBCleanUp();  
      return false;  
   }  
   // setbulkmode  
   char ColTerm[] = "\t";  
   char RowTerm[] = "\r\n";  
   wchar_t wColTerm[] = L"\t";  
   wchar_t wRowTerm[] = L"\r\n";  
   BYTE * pColTerm = NULL;  
   int cbColTerm = NULL;  
   BYTE * pRowTerm = 0;  
   int cbRowTerm = 0;  
   int bulkmode = -1;  
  
   if(BCPType == 'c') {   // bcp -c  
      pColTerm = (BYTE*)ColTerm;  
      pRowTerm = (BYTE*)RowTerm;  
      cbColTerm = 1;  
      cbRowTerm = 2;  
      bulkmode = BCP_OUT_CHARACTER_MODE;  
   }  
   else  
      if(BCPType == 'w') {   // bcp -w  
         pColTerm = (BYTE*)wColTerm;  
         pRowTerm = (BYTE*)wRowTerm;  
         cbColTerm = 2;  
         cbRowTerm = 4;  
         bulkmode = BCP_OUT_WIDE_CHARACTER_MODE;  
      }  
      else  
         if (BCPType == 'n')   // bcp -n  
            bulkmode = BCP_OUT_NATIVE_MODE;  
         else  
            if (BCPType == 'N')   // bcp -n  
               bulkmode = BCP_OUT_NATIVE_TEXT_MODE;  
            else {  
               printf("unknown bcp mode\n");  
               OLEDBCleanUp();  
               return false;  
            }  
            hr = g_pIBcpSession->BCPSetBulkMode(bulkmode, pColTerm, cbColTerm, pRowTerm, cbRowTerm);  
            if (FAILED(hr)) {  
               printf("BCPSetBulkMode failed\n");  
               OLEDBCleanUp();  
               return false;  
            }  
  
            // set queryout TSQL statement  
            hr = g_pIBcpSession->BCPControl(BCP_OPTION_HINTS, pszQureryOut);  
            if (FAILED(hr)) {  
               printf("BCPControl failed\n");  
               OLEDBCleanUp();  
               return false;  
            }  
            // bcp copy  
            DBROWCOUNT nRowsInserted = 0;  
            hr = g_pIBcpSession->BCPExec(&nRowsInserted);  
            if (FAILED(hr)) {  
               printf("BCPExec failed\n");  
               OLEDBCleanUp();  
               return false;  
            }  
            printf("bcp done\n");  
            OLEDBCleanUp();  
            return true;  
}  
  
int main() {  
   BCPSetBulkMode(L"localhost", TEXT("SELECT 'this is a bcp -c test', 1,2") , 'c', L"bcpc.dat");  
   BCPSetBulkMode(L"localhost", TEXT("SELECT 'this is a bcp -w test', 1,2") , 'w', L"bcpw.dat");  
   BCPSetBulkMode(L"localhost", TEXT("SELECT 'this is a bcp -c test', 1,2") , 'n', L"bcpn.dat");  
   BCPSetBulkMode(L"localhost", TEXT("SELECT 'this is a bcp -w test', 1,2") , 'N', L"bcp_N.dat");  
}  
```  
  
## <a name="see-also"></a>См. также:  
 [Метода IBCPSession2 &#40;OLE DB&#41;](ibcpsession2-ole-db.md)  
  
  
