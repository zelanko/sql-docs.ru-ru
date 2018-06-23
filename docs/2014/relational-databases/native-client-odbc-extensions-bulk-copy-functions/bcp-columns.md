---
title: bcp_columns | Документы Microsoft
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
- bcp_columns
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_columns function
ms.assetid: 5376f6fe-9508-439a-8c66-778d77f19ac3
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f2f7cb508f9b7715abbc2505f38b30795df2d142
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095673"
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
 Общее количество столбцов в файле пользователя. Даже если планируется выполнить массовое копирование данных из файла пользователя в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы и скопировать все столбцы в файле пользователя не требуется, по-прежнему необходимо задать *nColumns* общего числа столбцов в файле пользователя.  
  
## <a name="returns"></a>Возвращает  
 SUCCEED или FAIL.  
  
## <a name="remarks"></a>Примечания  
 Эта функция может быть вызван только после [bcp_init](bcp-init.md) был вызван с недопустимым именем файла.  
  
 Эту функцию следует вызывать только в том случае, если планируется использовать формат файла пользователя, отличный от формата по умолчанию. Дополнительные сведения об описании формата файла пользователя по умолчанию см. в разделе **bcp_init**.  
  
 После вызова метода `bcp_columns`, необходимо вызвать [bcp_colfmt](bcp-colfmt.md)для каждого столбца в пользовательском файле, чтобы полностью описать нестандартный формат файла.  
  
## <a name="see-also"></a>См. также  
 [Функции массового копирования](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  