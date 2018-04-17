---
title: bcp_getcolfmt | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-odbc-extensions-bulk-copy-functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- bcp_getcolfmt
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_getcolfmt function
ms.assetid: f8bdada5-7b2d-4475-8c98-f93e9d77b130
caps.latest.revision: 36
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: e68209f476d5f53785bffabafabae7e7b6e4c323
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="bcpgetcolfmt"></a>bcp_getcolfmt
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Используется для нахождения значения свойства формата столбца.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RETCODE bcp_getcolfmt (  
        HDBC hdbc,  
        INT field,  
        INT property,  
        void* pValue,  
        INT cbvalue,  
        INT* pcbLen);  
```  
  
## <a name="arguments"></a>Аргументы  
 *HDBC*  
 Дескриптор соединения ODBC с поддержкой массового копирования.  
  
 *field*  
 Номер столбца, для которого получается свойство.  
  
 *Свойство*  
 Одна из констант свойства.  
  
 *pValue*  
 Указатель на буфер, из которого получается значение свойства.  
  
 *cbValue*  
 Длина буфера свойств, в байтах.  
  
 *pcbLen*  
 Указатель длины данных, возвращаемых в буфер свойства.  
  
## <a name="returns"></a>Возвращает  
 SUCCEED или FAIL.  
  
## <a name="remarks"></a>Замечания  
 Значения свойства формата столбца перечислены в [bcp_setcolfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-setcolfmt.md) раздела. Они устанавливаются с помощью вызова функции **bcp_setcolfmt** , а для их поиска используется функция **bcp_getcolfmt** .  
  
 Изменения в поведении заметны при подключении к [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] (или более поздней версии) сервер, по сравнению с более ранней версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии. Дополнительные сведения см. в разделе [Metadata Discovery](../../relational-databases/native-client/features/metadata-discovery.md).  
  
## <a name="bcpgetcolfmt-support-for-enhanced-date-and-time-features"></a>Поддержка функцией bcp_getcolfmt улучшенных возможностей даты-времени  
 Типы, используемые с **BCP_FMT_TYPE** свойство для типов даты и времени, как указано в [изменения массового копирования для улучшенной даты и времени &#40;OLE DB и ODBC&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).  
  
 Дополнительные сведения см. в разделе [даты и времени усовершенствования & #40; ODBC & #41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [Функции массового копирования](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
