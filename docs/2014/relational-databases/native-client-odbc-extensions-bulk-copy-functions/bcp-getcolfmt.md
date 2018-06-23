---
title: bcp_getcolfmt | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 36
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1dcae7d7934221e1df720869d09aa6abcf958c04
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36097506"
---
# <a name="bcpgetcolfmt"></a>bcp_getcolfmt
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
 *HDBC*  
 Дескриптор соединения ODBC с поддержкой массового копирования.  
  
 *field*  
 Номер столбца, для которого получается свойство.  
  
 *property*  
 Одна из констант свойства.  
  
 *pValue*  
 Указатель на буфер, из которого получается значение свойства.  
  
 *cbValue*  
 Длина буфера свойств, в байтах.  
  
 *pcbLen*  
 Указатель длины данных, возвращаемых в буфер свойства.  
  
## <a name="returns"></a>Возвращает  
 SUCCEED или FAIL.  
  
## <a name="remarks"></a>Примечания  
 Значения свойства формата столбца перечислены в [bcp_setcolfmt](bcp-setcolfmt.md) раздела. Они устанавливаются с помощью вызова функции **bcp_setcolfmt** , а для их поиска используется функция **bcp_getcolfmt** .  
  
 Изменения в поведении заметны при подключении к [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] (или более поздней версии) сервер, по сравнению с более ранней версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии. Дополнительные сведения см. в разделе [обнаружение метаданных](../native-client/features/metadata-discovery.md).  
  
## <a name="bcpgetcolfmt-support-for-enhanced-date-and-time-features"></a>Поддержка функцией bcp_getcolfmt улучшенных возможностей даты-времени  
 Типы, используемые с `BCP_FMT_TYPE` свойство для типов даты и времени, как указано в [изменения массового копирования для улучшенной даты и времени &#40;OLE DB и ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).  
  
 Дополнительные сведения см. в разделе [даты и времени усовершенствования &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [Функции массового копирования](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  