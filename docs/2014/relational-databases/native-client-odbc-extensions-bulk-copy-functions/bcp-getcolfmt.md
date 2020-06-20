---
title: bcp_getcolfmt | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_getcolfmt
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_getcolfmt function
ms.assetid: f8bdada5-7b2d-4475-8c98-f93e9d77b130
author: rothja
ms.author: jroth
ms.openlocfilehash: 294241eb586a70f4e0a826b1dce5d35879b3ee3e
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85019512"
---
# <a name="bcp_getcolfmt"></a>bcp_getcolfmt
  Используется для нахождения значения свойства формата столбца.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RETCODE bcp_getcolfmt (  
HDBC   
hdbc  
,  
INT   
field  
,  
INT   
property  
,  
void*   
pValue  
,  
INT   
cbvalue,  
INT*   
pcbLen  
);  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *hdbc*  
 Дескриптор соединения ODBC с поддержкой массового копирования.  
  
 *полями*  
 Номер столбца, для которого получается свойство.  
  
 *property*  
 Одна из констант свойства.  
  
 *pValue*  
 Указатель на буфер, из которого получается значение свойства.  
  
 *кбвалуе*  
 Длина буфера свойств, в байтах.  
  
 *pcbLen*  
 Указатель длины данных, возвращаемых в буфер свойства.  
  
## <a name="returns"></a>Возвращаемое значение  
 SUCCEED или FAIL.  
  
## <a name="remarks"></a>Remarks  
 Значения свойства формата столбца перечислены в разделе [bcp_setcolfmt](bcp-setcolfmt.md) . Они устанавливаются с помощью вызова функции **bcp_setcolfmt** , а для их поиска используется функция **bcp_getcolfmt** .  
  
 Изменения в поведении заметны при подключении к серверному компьютеру с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] (или более поздней версии), если сравнивать с более ранними версиями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения см. в разделе [Обнаружение метаданных](../native-client/features/metadata-discovery.md).  
  
## <a name="bcp_getcolfmt-support-for-enhanced-date-and-time-features"></a>Поддержка функцией bcp_getcolfmt улучшенных возможностей даты-времени  
 Типы, используемые со `BCP_FMT_TYPE` свойством для типов даты и времени, задаются в [инструкциях по расширению копирования для усовершенствованных типов даты и времени &#40;OLE DB и ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).  
  
 Дополнительные сведения см. в разделе [улучшения даты и времени &#40;&#41;ODBC ](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="see-also"></a>См. также:  
 [Bulk Copy Functions](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
