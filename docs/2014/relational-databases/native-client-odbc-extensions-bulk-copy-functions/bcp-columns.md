---
title: bcp_columns | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_columns
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_columns function
ms.assetid: 5376f6fe-9508-439a-8c66-778d77f19ac3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fcfbbdb1881662401e791ea197115120444cf855
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63225532"
---
# <a name="bcpcolumns"></a>bcp_columns
  Задает общее количество столбцов в файле пользователя, используемых для массового копирования на сервер или с сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [bcp_setbulkmode](bcp-setbulkmode.md) может использоваться вместо bcp_columns и [bcp_colfmt](bcp-colfmt.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RETCODE bcp_columns (  
HDBC   
hdbc  
,  
INT   
nColumns  
);  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *HDBC*  
 Дескриптор соединения ODBC с поддержкой массового копирования.  
  
 *nColumns*  
 Общее количество столбцов в файле пользователя. Даже если планируется выполнить массовое копирование данных из пользовательского файла, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы и не планируется копировать все столбцы в файле пользователя, по-прежнему необходимо задать *nColumns* общего числа столбцов файла пользователя.  
  
## <a name="returns"></a>Возвращает  
 SUCCEED или FAIL.  
  
## <a name="remarks"></a>Примечания  
 Эту функцию можно вызывать только после [bcp_init](bcp-init.md) был вызван с допустимым именем файла.  
  
 Эту функцию следует вызывать только в том случае, если планируется использовать формат файла пользователя, отличный от формата по умолчанию. Дополнительные сведения об описании стандартного формата пользовательского файла см. в разделе **bcp_init**.  
  
 После вызова метода `bcp_columns`, необходимо вызвать [bcp_colfmt](bcp-colfmt.md)для каждого столбца в пользовательском файле, чтобы полностью описать нестандартный формат файла.  
  
## <a name="see-also"></a>См. также  
 [Функции массового копирования](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
